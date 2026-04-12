# Future Leads Architecture: Single Source of Truth

## Problem Statement

The current architecture has two lead tables with bidirectional foreign keys:

- `extracted_leads` - Main app leads (extractions, X intent, LinkedIn intent)
- `linkedin_leads` - Extension CRM (stages, invitations, copilot)

This creates:

- Two sources of truth for "who is a lead"
- Sync complexity (bidirectional FKs: `extracted_leads.linkedin_lead_id` and `linkedin_leads.extracted_lead_id`)
- Risk of orphaned records or data drift over time
- Confusing queries ("which table do I query?")

---

## Proposed Architecture

Separate the **lead identity** from the **CRM workflow state**.

```
┌─────────────────────────────────────────────────────────────┐
│ leads (single source of truth)                              │
├─────────────────────────────────────────────────────────────┤
│ id UUID PRIMARY KEY                                         │
│ user_id UUID                                                │
│                                                             │
│ -- Identity                                                 │
│ name TEXT                                                   │
│ username TEXT                                               │
│ bio TEXT                                                    │
│ profile_image_url TEXT                                      │
│ location TEXT                                               │
│                                                             │
│ -- Platform profiles                                        │
│ twitter_profile_url TEXT                                    │
│ linkedin_profile_url TEXT                                   │
│ public_identifier TEXT (LinkedIn)                           │
│ headline TEXT (LinkedIn)                                    │
│ company TEXT                                                │
│                                                             │
│ -- Source tracking                                          │
│ source TEXT ('extraction'|'tweet_search'|'linkedin_search') │
│ source_search_id UUID                                       │
│ source_type TEXT ('author'|'commenter'|'follower')          │
│                                                             │
│ -- Intent analysis                                          │
│ priority_score INTEGER                                      │
│ sentiment TEXT                                              │
│ sentiment_score DECIMAL                                     │
│ sentiment_reasoning TEXT                                    │
│ original_content TEXT                                       │
│ parent_content TEXT                                         │
│ source_content_url TEXT                                     │
│ intent_category TEXT                                        │
│                                                             │
│ -- Qualification                                            │
│ offer_id UUID                                               │
│ qualified_at TIMESTAMP                                      │
│ qualification_score DECIMAL                                 │
│ qualification_reasoning TEXT                                │
│                                                             │
│ -- Timestamps                                               │
│ created_at TIMESTAMP                                        │
│ updated_at TIMESTAMP                                        │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ 1:1 (optional, only for LinkedIn leads)
                              ▼
┌─────────────────────────────────────────────────────────────┐
│ linkedin_crm_state (extension CRM only)                     │
├─────────────────────────────────────────────────────────────┤
│ id UUID PRIMARY KEY                                         │
│ lead_id UUID REFERENCES leads(id) ON DELETE CASCADE         │
│ user_id UUID                                                │
│                                                             │
│ -- CRM Stage                                                │
│ stage TEXT ('new'|'requested'|'accepted'|'contacted'|...)   │
│ stage_history JSONB                                         │
│                                                             │
│ -- LinkedIn Connection State                                │
│ requested_at TIMESTAMP                                      │
│ invitation_id TEXT                                          │
│ accepted_at TIMESTAMP                                       │
│ contacted_at TIMESTAMP                                      │
│ replied_at TIMESTAMP                                        │
│                                                             │
│ -- Extension Features                                       │
│ matched_post JSONB                                          │
│ icp_match_reason TEXT                                       │
│ copilot_conversations JSONB                                 │
│ notes TEXT                                                  │
│ follow_up_date DATE                                         │
│ last_activity TIMESTAMP                                     │
│                                                             │
│ -- Timestamps                                               │
│ created_at TIMESTAMP                                        │
│ updated_at TIMESTAMP                                        │
└─────────────────────────────────────────────────────────────┘
```

---

## Why This Is Better

| Concern             | Current (Dual Tables)                    | Proposed (Single + CRM State)                  |
| ------------------- | ---------------------------------------- | ---------------------------------------------- |
| Source of truth      | Two tables, unclear which is primary     | One `leads` table                              |
| Sync complexity      | Bidirectional FKs, must keep in sync     | No sync needed                                 |
| "Who is a lead?"     | Query both tables                        | Query `leads`                                  |
| Extension CRM        | Mixed with lead identity                 | Separate concern in `linkedin_crm_state`       |
| Frontend queries     | Complex joins or dual queries            | Simple `SELECT FROM leads`                     |
| Extension queries    | Query `linkedin_leads`                   | `JOIN linkedin_crm_state` when needed          |
| Delete handling      | Must delete from both                    | `ON DELETE CASCADE` handles it                 |

---

## Key Insight

A **lead** is a person you want to reach. That is the entity.

The **CRM workflow** (requested, accepted, contacted, replied) is metadata about *how you are managing* that lead on a specific platform. It is not the lead itself.

The current architecture conflates these two concerns. The proposed architecture separates them.

---

## Migration Plan

### Phase 1: Prepare

1. Create new `leads` table (or rename `extracted_leads`)
2. Create `linkedin_crm_state` table with FK to `leads`
3. Add indexes for common queries

### Phase 2: Migrate Data

```sql
-- Create leads from extracted_leads (already done, just rename)
ALTER TABLE extracted_leads RENAME TO leads;

-- Create CRM state table
CREATE TABLE linkedin_crm_state (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  lead_id UUID NOT NULL REFERENCES leads(id) ON DELETE CASCADE,
  user_id UUID NOT NULL,

  stage TEXT DEFAULT 'new',
  stage_history JSONB DEFAULT '[]',

  requested_at TIMESTAMP,
  invitation_id TEXT,
  accepted_at TIMESTAMP,
  contacted_at TIMESTAMP,
  replied_at TIMESTAMP,

  matched_post JSONB,
  icp_match_reason TEXT,
  copilot_conversations JSONB DEFAULT '[]',
  notes TEXT,
  follow_up_date DATE,
  last_activity TIMESTAMP,

  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW(),

  UNIQUE(lead_id)  -- 1:1 relationship
);

-- Migrate existing linkedin_leads
INSERT INTO leads (user_id, name, username, linkedin_profile_url, public_identifier, headline, company, location, source, ...)
SELECT user_id, name, public_identifier, profile_url, public_identifier, headline, company, location, 'linkedin_extension', ...
FROM linkedin_leads
WHERE extracted_lead_id IS NULL;  -- Only those not already linked

INSERT INTO linkedin_crm_state (lead_id, user_id, stage, stage_history, ...)
SELECT
  COALESCE(ll.extracted_lead_id, new_lead.id),
  ll.user_id,
  ll.stage,
  ll.stage_history,
  ...
FROM linkedin_leads ll
LEFT JOIN leads new_lead ON ...;
```

### Phase 3: Update Code

**Backend:**

- Update extension endpoints to read/write `leads` + `linkedin_crm_state`
- Update main app to query `leads` only
- Remove bidirectional sync logic

**Extension:**

- Update queries: `SELECT l.*, lcs.* FROM leads l LEFT JOIN linkedin_crm_state lcs ON lcs.lead_id = l.id`
- Update inserts: Insert into `leads` first, then `linkedin_crm_state`

**Frontend:**

- No changes needed (already queries `leads`/`extracted_leads`)

### Phase 4: Cleanup

1. Verify all data migrated correctly
2. Drop `linkedin_leads` table
3. Remove old FKs (`extracted_leads.linkedin_lead_id`, `linkedin_leads.extracted_lead_id`)

---

## Queries After Migration

**Frontend - Get all leads:**

```sql
SELECT * FROM leads WHERE user_id = $1;
```

**Extension - Get LinkedIn leads with CRM state:**

```sql
SELECT l.*, lcs.*
FROM leads l
LEFT JOIN linkedin_crm_state lcs ON lcs.lead_id = l.id
WHERE l.user_id = $1
  AND l.linkedin_profile_url IS NOT NULL;
```

**Extension - Update CRM stage:**

```sql
UPDATE linkedin_crm_state
SET stage = $1, stage_history = stage_history || $2
WHERE lead_id = $3;
```

**Extension - Add new LinkedIn lead:**

```sql
-- Insert lead
INSERT INTO leads (user_id, name, linkedin_profile_url, source, ...)
VALUES ($1, $2, $3, 'linkedin_extension', ...)
RETURNING id;

-- Insert CRM state
INSERT INTO linkedin_crm_state (lead_id, user_id, stage, matched_post, ...)
VALUES ($lead_id, $1, 'new', $4, ...);
```

---

## When To Do This

Consider this refactor when:

- Sync bugs appear between `linkedin_leads` and `extracted_leads`
- You need cross-platform deduplication (same person on X and LinkedIn)
- Extension development slows due to dual-table complexity
- You want unified analytics across all lead sources

Not urgent if the current bidirectional sync is working. But worth planning for.

---

## Out of Scope (Further Future)

- Cross-platform identity resolution (same person on X + LinkedIn = one lead)
- CRM state for X/Twitter leads (if you add DM outreach tracking)
- Multi-workspace/team support
