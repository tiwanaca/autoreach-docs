# Supported Actions by Platform

Reference for all sequence action types, how they execute on each platform, and the checks and behaviors that govern them.

## Actions Reference

| Action | X | LinkedIn | Description |
|---|---|---|---|
| Like | Y | Y | Like/react to a lead's recent post |
| Reply | Y | Y | Reply to a post (X) or comment on a post (LinkedIn) |
| Follow | Y |-  | Follow the account |
| DM | Y | Y | Send a direct message |
| Connection Request |-  | Y | Send a LinkedIn connection request |
| View Profile |-  | Y | View a lead's LinkedIn profile |
| Withdraw Connection |-  | Y | Withdraw a pending or accepted connection |
| Condition | Y | Y | Branch based on lead status |

## Action Details

### Like

**Platforms:** X, LinkedIn

Likes a lead's recent post. The post is selected automatically.

**Post selection:**
- Fetches the lead's recent posts
- Filters out posts already interacted with across **all sequences** (not just the current one)
- Respects the "prefer original posts" and "skip old posts" settings
- Selects the most recent qualifying post

**Execution:**
- **X:** Likes the tweet via the X API
- **LinkedIn:** Likes the post via the LinkedIn API

If no qualifying posts are found, the action is skipped and the sequence advances.

---

### Reply / Comment

**Platforms:** X (reply), LinkedIn (comment)

Replies to a lead's recent post with AI-generated text. On X this creates a thread reply; on LinkedIn it posts a comment.

**Post selection:**
- Same logic as Like but also filters out posts already replied to (global check across all sequences)
- If the skip negative content setting is enabled, posts with tragic or negative content are skipped (checked via AI)
- For LinkedIn, attempts to coordinate with a prior like action-  commenting on the same post that was recently liked

**Reply generation:**
- AI generates the reply using the post text as context
- Uses the step-level AI prompt if configured, otherwise falls back to the sequence's warmup prompt
- Supports multilingual replies via the offer's language setting

**Execution:**
- **X:** Posts a thread reply via the X API
- **LinkedIn:** Posts a comment via the LinkedIn API. If commenting is disabled on the first post, tries the next candidate post.

---

### Follow

**Platforms:** X only

Follows the lead's account on X. LinkedIn uses Connection Request instead.

**Execution:**
- Checks if already following-  skips if already following
- Simulates natural browsing behavior before following (profile view, etc.)
- Follows the account

---

### Send DM

**Platforms:** X, LinkedIn

Sends a direct message to the lead. The message template is personalized using lead data and AI.

**Platform routing:** Each DM step is configured for a specific platform. The system validates the lead has the required profile data for that platform before sending.

**Message personalization:**
- Template variables are replaced with lead data: `{{name}}`, `{{first_name}}`, `{{bio}}`, `{{company}}`, `{{company_size}}`, `{{location}}`, `{{followers}}`, etc.
- Special placeholders: `{{tweet}}` (lead's latest tweet), `{{replied_post}}` (post from a prior reply action)
- AI fills remaining smart placeholders (`{{role}}`, `{{pain_point}}`, custom placeholders) using enrichment data, web enrichment, and knowledge base context
- Booking URL is injected with platform-specific tracking if configured

**X DM execution:**
- Checks whether the lead can receive DMs-  if not, the lead is removed from the sequence
- Creates or retrieves the conversation
- Sends via the X API

**LinkedIn DM execution:**
- Checks connection status-  LinkedIn requires an accepted connection to send DMs
- If an existing conversation already has messages, skips the template DM and queues an AI response instead (avoids duplicate cold outreach)
- Sends via the LinkedIn API

**Duplicate prevention:** The system detects crash/retry scenarios and prevents double-sending.

---

### Connection Request

**Platforms:** LinkedIn only

Sends a LinkedIn connection request, optionally with a personalized note.

**Weekly limits by account type:**

| Account Type | Weekly Limit |
|---|---|
| Free | 100 |
| Premium | 150 |
| Sales Navigator | 200 |

If the weekly limit is reached, the action enters Deferred status and all remaining connection request actions in the sequence are batch-deferred to the following Monday.

**Execution:**
- Checks weekly limit
- Simulates natural browsing behavior before sending
- Personalizes the connection note if configured (supports `{{variable}}` placeholders, max 300 characters)
- Sends the connection request
- If auto-withdraw is configured, schedules a withdraw action after the specified number of days

---

### View Profile

**Platforms:** LinkedIn only

Visits the lead's LinkedIn profile, triggering a "who viewed your profile" notification on their end.

Visits the lead's LinkedIn profile, triggering a "who viewed your profile" notification. Typically used as a warm-up step before sending a connection request.

---

### Withdraw Connection

**Platforms:** LinkedIn only

Withdraws a pending or accepted LinkedIn connection. Usually auto-scheduled by a connection request step's auto-withdraw setting, not manually added to flows.

Withdraws the connection if it's still pending. Does **not** count toward sequence progress or advance the lead.

---

### Condition

**Platforms:** X, LinkedIn (condition types vary by platform)

Evaluates a condition and routes the lead to the TRUE or FALSE branch.

**Condition types:**

| Type | Platform | How It's Checked |
|---|---|---|
| Replied | X, LinkedIn | Checks if the lead has replied or sent inbound messages |
| Followed Back | X | Checks if the lead followed you back on X |
| Connection Accepted | LinkedIn | Checks if the LinkedIn connection request was accepted; if so, cancels pending withdrawal |
| Has Profile | X, LinkedIn | Checks if lead has a filled-out profile on the target platform |

**Retry logic:** If the condition is not met and retries are configured (retry interval and max attempts):
- A new condition action is scheduled for the same step after the retry interval
- The retry attempt counter is incremented
- Current action is marked as completed (not failed)
- The FALSE branch only executes after all retries are exhausted

## Pre-Action Checks

Before every action executes, the system runs these checks in order:

| Check | Behavior if Failed |
|---|---|
| Action status is Pending or Queued | Skip |
| Lead not in terminal status (Replied, Meeting Booked, Lost, Completed) | Skip |
| Lead not in CRM at non-"new" stage | Skip |
| Lead not marked as competitor | Skip |
| Lead not blacklisted | Skip |
| For X DMs: lead can receive DMs | Remove lead from sequence |
| Daily action limit not exceeded | Reschedule for tomorrow |
| Lead has required platform data for action type | Skip |

Daily limits are platform-specific: X and LinkedIn have separate counters. If a limit is reached, the action is rescheduled for the next day at a random time within the activity window.

## Action Lifecycle

Every action moves through these states:

| Status | Description |
|---|---|
| Pending | Waiting for scheduled time |
| Queued | Scheduled time reached, in the processing queue |
| In Progress | Being executed (includes human delay simulation) |
| Completed | Successfully executed |
| Skipped | Bypassed (no content, missing platform data, blacklisted, error) |
| Failed | Could not complete (rarely used-  most failures become skipped) |
| Deferred | Rate-limited connection requests; auto-resumes Monday |

After every completed or skipped action, the next step is queued based on the flow graph.

## Error Handling

Errors are classified by severity:

- **Minor errors** (no content found, duplicate action)-  logged, sequence continues normally
- **Critical errors** (rate limit, bot detection, auth failure)-  may pause the account and notify you by email
- **Budget exhaustion**-  action rescheduled for the next day, preserving the sequence flow

## Human Delay Simulation

All actions include anti-detection timing that simulates natural browsing, reading, and typing behavior. Delays vary by action type and context to create realistic patterns.

## Next Steps

- **[Building Sequences](building-sequences.md)**: Combine actions into multi-step campaigns
- **[DM Personalization](dm-personalization.md)**: How AI generates personalized first messages
- **[Scheduling & Send Limits](scheduling.md)**: Activity windows and rate limit details
