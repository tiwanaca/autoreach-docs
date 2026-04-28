# Supported Actions by Platform

Reference for all sequence action types, how they execute on each platform, and the checks and behaviors that govern them.

## Actions Reference

| Action | X | LinkedIn | Email | Description |
|---|---|---|---|---|
| Like | Y | Y |-  | Like/react to a lead's recent post |
| Comment |-  | Y |-  | Comment on a lead's LinkedIn post |
| Follow | Y |-  |-  | Follow the account |
| DM | Y | Y |-  | Send a direct message |
| Email |-  |-  | Y | Send an email through your connected mailbox |
| Connection Request |-  | Y |-  | Send a LinkedIn connection request |
| Withdraw Connection |-  | Y |-  | Withdraw a pending or accepted connection |
| Condition | Y | Y | Y | Branch based on lead status |

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

### Comment

**Platforms:** LinkedIn only

Posts an AI-generated comment on a lead's recent LinkedIn post.

**Post selection:**
- Same logic as Like but also filters out posts already commented on (global check across all sequences)
- If the skip negative content setting is enabled, posts with tragic or negative content are skipped (checked via AI)
- Attempts to coordinate with a prior like action - commenting on the same post that was recently liked

**Comment generation:**
- AI generates the comment using the post text as context
- Uses the step-level AI prompt if configured, otherwise falls back to the sequence's comment prompt ("How AI comments on posts")
- Supports multilingual comments via the offer's language setting

**Execution:**
- Posts a comment via the LinkedIn API. If commenting is disabled on the first post, tries the next candidate post.

---

### Follow

**Platforms:** X only

Follows the lead's account on X. LinkedIn uses Connection Request instead.

**Execution:**
- Checks if already following-  skips if already following
- Simulates natural browsing behavior before following
- Follows the account

---

### Send DM

**Platforms:** X, LinkedIn

Sends a direct message to the lead. The message template is personalized using lead data and AI.

**Platform routing:** Each DM step is configured for a specific platform. The system validates the lead has the required profile data for that platform before sending.

**Message personalization:**
- Template variables are replaced with lead data: `{{name}}`, `{{first_name}}`, `{{bio}}`, `{{company}}`, `{{company_size}}`, `{{location}}`, `{{followers}}`, etc.
- Special placeholders: `{{post}}` (lead's latest post), `{{replied_post}}` (post from a prior comment action)
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

### Send Email

**Platforms:** Email (Gmail and/or Outlook)

Sends an email to the lead from one of your connected mailboxes. Subject and body support the same template variables and AI personalization as DMs.

**Mailbox routing:**
- Recipients on `@gmail.com` send from your Gmail account
- Recipients on `@outlook.com` / `@hotmail.com` / `@live.com` send from your Outlook account
- Everyone else sends from the **Primary** mailbox (you set this from the **Email** card on the parent account's detail page)

**Execution:**
- Validates the lead has an email address. If missing, the action is skipped.
- Confirms the relevant mailbox is connected and active. If not, the action is skipped.
- Skips leads with a recorded bounce on a previous send.
- Renders the subject and body templates, applies AI personalization if enabled, then sends.

**Reply handling:** Inbound replies are detected on the next mailbox poll and matched to the conversation. The reply appears in the unified Inbox.

See [Email Channel](email-channel.md) and [Connecting Email](../getting-started/connecting-email.md) for setup and configuration details.

---

### Connection Request

**Platforms:** LinkedIn only

Sends a LinkedIn connection request, optionally with a personalized note.

**Daily limits:** You can set a daily connection request limit per account to any whole number from 1 to 100 (default 15, which is the recommended starting point). Choose a limit that matches your account type and risk tolerance.

If the daily limit is reached, the action enters Deferred status and remaining connection request actions are deferred to the next day.

**Execution:**
- Checks daily limit
- Simulates natural browsing behavior before sending
- Personalizes the connection note if configured (supports `{{variable}}` placeholders, max 300 characters)
- Sends the connection request
- If auto-withdraw is configured, schedules a withdraw action after the specified number of days

---

### Withdraw Connection

**Platforms:** LinkedIn only

Withdraws a pending LinkedIn connection. This action is **automatically scheduled** by a connection request step's auto-withdraw setting - it is not available in the flow builder palette and cannot be manually added to sequences.

Does **not** count toward sequence progress or advance the lead.

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

Each sequence has a single unified daily action counter that covers all channels (X, LinkedIn, email). If the limit is reached, the action is rescheduled for the next day at a random time within the activity window.

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
| Cancelled | Action cancelled before execution (e.g., sequence paused, lead removed, superseded by a manual action) |
| Deferred | Rate-limited connection requests; auto-resumes the next day |

After every completed or skipped action, the next step is queued based on the flow graph.

## Error Handling

Errors are classified by severity:

- **Minor errors** (no content found, duplicate action)-  logged, sequence continues normally
- **Critical errors** (rate limit, bot detection, auth failure)-  may pause the account and notify you by email
- **Budget exhaustion**-  action rescheduled for the next day, preserving the sequence flow

## Human Delay Simulation

All actions include natural timing that simulates browsing, reading, and typing behavior. Delays vary by action type and context to create realistic patterns.

## Next Steps

- **[Building Sequences](building-sequences.md)**: Combine actions into multi-step campaigns
- **[DM Personalization](dm-personalization.md)**: How AI generates personalized first messages
- **[Scheduling & Send Limits](scheduling.md)**: Activity windows and rate limit details
