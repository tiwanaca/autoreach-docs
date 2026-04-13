# Template Variables

Template variables let you write message templates with `{{placeholder}}` syntax that AutoReach fills in with real lead data at send-time. The system uses a two-pass approach: direct substitution for known variables, then AI inference for unknown placeholders.

## How Variable Replacement Works

### Two-Pass System

**Pass 1 — Direct Substitution:** 27 known variables are replaced with values from lead data. If a variable has no data, it's replaced with an empty string.

**Pass 2 — AI Inference:** Any remaining `{{placeholders}}` (including custom ones you create) are sent to the AI model along with the lead's profile, enrichment data, and offer context. The AI either fills them with explicit information from the lead's data (2–5 words max) or removes the placeholder and surrounding incomplete text. The AI never invents or guesses information.

### Validation

After both passes, a safety check scans for any unresolved `{{}}` placeholders. **Messages with unresolved variables are blocked** — they are never sent. The personalizer returns null, and the caller handles it gracefully.

## Known Variables (Direct Substitution)

These 27 variables are replaced directly from lead data in the first pass.

### Identity

| Variable | Source |
|---|---|
| `{{name}}` | Full name, falls back to username |
| `{{first_name}}` | Extracted from full name |
| `{{username}}` | Platform handle |
| `{{bio}}` | Lead bio |
| `{{location}}` | Lead location |
| `{{email}}` | Lead email |

### Network

| Variable | Source |
|---|---|
| `{{followers}}` | Follower count |
| `{{following}}` | Following count |

### Profile Links

| Variable | Source |
|---|---|
| `{{website}}` | Lead website URL |
| `{{linkedin_url}}` | LinkedIn profile URL |
| `{{x_profile_url}}` | X profile URL |

### Professional Profile

| Variable | Source |
|---|---|
| `{{headline}}` | LinkedIn headline, falls back to bio |
| `{{summary}}` | Profile summary (max 200 characters) |
| `{{current_role}}` | Current job title from LinkedIn experience |
| `{{skills}}` | Top 5 skills, comma-separated |

### Company Data

| Variable | Source |
|---|---|
| `{{company_name}}` | Company name from enrichment or profile |
| `{{company_size}}` | Employee count range (e.g., "51-200") |
| `{{company_industry}}` | Company industry from enrichment or profile |
| `{{funding_stage}}` | Company funding stage |
| `{{tech_stack}}` | Top 5 technologies, comma-separated |

### Web Enrichment Insights

| Variable | Source | Notes |
|---|---|---|
| `{{achievements}}` | Notable achievements | Filtered by recency + current company, first 2 items |
| `{{speaking}}` | Speaking engagements | First 2 items |
| `{{podcasts}}` | Podcast appearances | First 2 items |
| `{{enrichment_summary}}` | Web enrichment summary | Max 150 characters |

Achievements, speaking engagements, and podcasts are filtered to the lead's current company — data from previous employers is excluded.

### Sender & Booking

| Variable | Source |
|---|---|
| `{{user_name}}` | Sender's display name (passed as parameter) |
| `{{booking_link}}` | Calendar URL with lead-specific tracking (see below) |

## Special Variables (Fetched at Send-Time)

These variables trigger data fetching when used in a template.

### `{{post}}` / `{{tweet}}`

Both map to the same logic (`{{tweet}}` is a backwards-compatible alias). Fetches the lead's recent post content using this priority chain:

1. **Stored X intent stream** — if lead was sourced from X search with original content
2. **Stored LinkedIn intent stream** — if lead was sourced from LinkedIn search with original content
3. **Live X tweet fetch** — fetches latest tweet from X (retries up to 8 times over 30 minutes)
4. **Cached LinkedIn posts** — from enrichment cache
5. **Live LinkedIn post fetch** — via LinkedIn API
6. **Bio fallback** — instructs AI to use bio for personalization instead

For commenter-sourced leads, the context includes both the original post and the lead's reply:
```
ORIGINAL POST: "[post text]"
THEIR REPLY: "[reply text]"
```

### `{{replied_post}}`

References a post that was replied to in a **prior sequence step**. If a reply action executed earlier in the sequence, this variable provides the original post text and your reply text so the DM can reference prior engagement.

If no prior reply happened (step was skipped), the AI is instructed not to claim engagement and uses a generic opener instead.

## Custom Variables (AI-Inferred)

Any `{{placeholder}}` that isn't in the 27 known variables is treated as a custom variable. The AI model attempts to fill it using explicit information from the lead's profile, enrichment data, and offer context.

**Rules the AI follows:**
1. Look for **explicit** information in the lead's bio, profile, or enrichment data
2. If clearly stated: use it (2–5 words max)
3. If **not** clearly stated: remove the placeholder and any surrounding text that would be incomplete without it
4. Never invent, assume, or guess

Common AI-inferred variables:

| Variable | What AI looks for |
|---|---|
| `{{role}}` | Job title from bio, headline, or enrichment |
| `{{company}}` | Company name from bio or enrichment |
| `{{industry}}` | Industry from bio or enrichment |
| `{{pain_point}}` | Relevant challenge based on offer + lead context |
| `{{question}}` | Contextual question based on lead + offer |

You can use any custom placeholder name — the system doesn't reject unknown variables.

## Booking Link Tracking

The `{{booking_link}}` variable injects your calendar URL with lead-specific tracking parameters:

| Provider | Parameter | Value |
|---|---|---|
| Calendly | `a1` | Lead identifier |
| Cal.com | `x_username` | Lead identifier |
| Other | `a1` (fallback) | Lead identifier |

The tracking value is the lead's LinkedIn identifier (prefixed) for LinkedIn leads or the X username for X leads.

Example: `https://calendly.com/user` → `https://calendly.com/user?a1=li:john-smith-123`

## Platform Behavior

All 27 known variables work identically on both X and LinkedIn. There are no platform-specific variables.

Platform differences affect the AI's tone and context, not variable availability:

| Aspect | X | LinkedIn |
|---|---|---|
| Username prefix | `@username` | `username` (no prefix) |
| Tone instruction | Casual and direct | Slightly more professional |
| `{{post}}` label | "on X" | "on LinkedIn" |

## Example Template

```
hey {{first_name}},

saw you're {{current_role}} at {{company_name}} which probably means {{pain_point}}

I help with {{tech_stack}} teams — think {{enrichment_summary}}.

quick 15-min review, no cost.

interested?

{{user_name}}
{{booking_link}}
```

**Pass 1** replaces `{{first_name}}`, `{{current_role}}`, `{{company_name}}`, `{{tech_stack}}`, `{{enrichment_summary}}`, `{{user_name}}`, `{{booking_link}}` with lead data.

**Pass 2** sends `{{pain_point}}` to AI, which infers it from the lead's profile and offer context or removes it with surrounding text.

## Next Steps

- **[Cold DM Generation](cold-dm-generation.md)**: AI-powered message generation using these variables
- **[Building Sequences](building-sequences.md)**: Write templates in the flow editor
- **[Simulation & A/B Testing](simulation.md)**: Preview variable substitution with real leads
