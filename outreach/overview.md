# Outreach & Sequences Overview

Sequences are automated multi-step campaigns that execute engagement actions across X and LinkedIn. Each sequence walks leads through a configured flow of actions - likes, follows, DMs, replies, connection requests - with AI-personalized messaging and natural timing.

## What Is a Sequence?

A sequence is a series of steps that execute automatically against enrolled leads. Each step performs an action (like a post, send a DM, follow the account) with configurable delays between steps. Sequences support branching logic via condition steps that route leads based on whether they replied.

A typical sequence might look like:

1. Day 1: Like their recent post
2. Day 2: Follow them
3. Day 3: Send a personalized DM
4. Day 5: Condition-  if replied, stop. If not, send a follow-up DM.

### Sequence Statuses

| Status | Description |
|---|---|
| Draft | Initial state-  can be configured and edited |
| Scheduling | Actions are being scheduled for enrolled leads |
| Active | Running-  actions are scheduled and executing |
| Paused | Temporarily stopped (can be resumed) |
| Completed | All leads have finished the sequence |
| Failed | Sequence encountered a critical error |

### Platform Support

When creating a sequence, you select which accounts to use - an X account, a LinkedIn account, or both. At least one account is required. Individual steps specify which platform they target, so a single sequence can include steps that execute on X and others that execute on LinkedIn.

## Supported Actions

Each step in a sequence performs one of these action types:

| Action | Platforms | Description |
|---|---|---|
| DM | X, LinkedIn | Send a direct message (AI-personalized) |
| Like | X, LinkedIn | Like/react to a lead's recent post |
| Reply | X, LinkedIn | Reply to a post (X) or comment on a post (LinkedIn) |
| Follow | X | Follow the account |
| Connection Request | LinkedIn | Send a LinkedIn connection request |
| View Profile | LinkedIn | View the lead's LinkedIn profile |
| Condition |-  | Branch based on lead status (replied vs. not replied) |

Each step has a defined order, platform-specific settings, positioning data for the visual flow editor, and a reference to the next step for linear flow progression.

## AI Message Personalization

Every message sent through a sequence is personalized using the lead's enriched data. The system supports two layers:

**Direct substitution** - template variables replaced with lead data (identity, network stats, company info, enrichment insights, contact info, and more)

**AI-inferred placeholders** - filled by the AI model from lead context (`{{role}}`, `{{pain_point}}`, `{{question}}`, and any custom placeholder you define)

AutoReach provides 30+ built-in template variables across categories like identity, company data, professional profile, web enrichment insights, and contact info. The AI draws on the lead's profile data, recent activity, enrichment intelligence (tech stack, funding, company context), the offer's knowledge base (RAG), and tone examples configured on the sequence.

See **[DM Personalization](dm-personalization.md)** for the full variable reference.

## Sequence Execution

### Scheduling

Actions are scheduled automatically and executed one at a time to avoid rate limit issues.

**Lead selection order:** Higher-priority leads (based on buyer score and signal recency) get earlier time slots.

**Step progression:** Each step's connection determines what happens next. Condition steps evaluate lead status and branch accordingly. After each action completes, the next step is queued with the configured delay.

### Natural Timing

Sequence execution uses natural pacing - actions are spaced across the day, grouped into human-like sessions, and include realistic delays for reading and typing. Activity varies by time of day and day of week to match natural patterns.

### Activity Window

Outreach only executes during the configured activity window. Defaults to **09:00–21:00** in the user's timezone. Actions outside the window are deferred to the next open slot.

## Lead Statuses in a Sequence

| Status | Description |
|---|---|
| Pending | Enrolled but not yet contacted |
| Active | First action executed, progressing through steps |
| Paused | Temporarily paused (sequence paused or manual) |
| Replied | Lead has replied to at least one message |
| Meeting Booked | Meeting scheduled |
| Completed | Sequence flow completed for this lead |
| Failed | Action execution failed |
| Lost | Manually removed from sequence |

## Daily Send Limits

Each sequence has configurable daily action limits that protect account health. Limits reset at midnight in your timezone. If a limit is reached, remaining actions are deferred to the next day. See [Scheduling](scheduling.md) for the full limits table, enforcement details, and weekly connection limits.

## Conversation Follow-Ups

Sequences support automatic follow-ups for stale conversations:

| Setting | Default | Range |
|---|---|---|
| Conversation follow-up enabled | false |-  |
| Follow-up wait days | 3 | 1–30 |
| Max follow-up count | 2 | 1–10 |

The system finds conversations with no recent activity and schedules follow-up messages automatically.

## Adding Leads to Sequences

**Validation before enrollment:**
- Lead must have platform data matching the sequence (X profile for X sequences, LinkedIn for LinkedIn sequences)
- Lead must not already be enrolled in this sequence
- Lead must not be blacklisted
- If "Skip contacted leads" is enabled: lead must have no previous contact history
- For X sequences: lead must be able to receive DMs

Leads failing validation are skipped with a reason. If the sequence is active, scheduling begins immediately for new leads.

## Reply Detection and Opt-Out

**Reply detection** is passive-  incoming messages in a conversation update the lead's status to "Replied" and increment the sequence's reply counter.

**Opt-out handling** uses a blacklist system:
- Blacklist accounts manually from the Leads page
- Blacklisted leads are automatically removed from all sequences
- Blacklisted accounts cannot be re-enrolled
- The system does not auto-blacklist based on replies-  opt-out decisions are left to the user

## Sequence Metrics

| Metric | Description |
|---|---|
| Leads Added | Total leads enrolled |
| Contacted | Leads that received at least one action |
| Replied | Leads with status "Replied" or "Meeting Booked" |
| Meetings | Leads with a meeting scheduled |
| Reply Rate | Replied / Contacted |
| Conversion Rate | Meetings / Replied |
| Acceptance Rate | Connection requests accepted / sent (LinkedIn only) |

Metrics are updated automatically when lead statuses change. Step-level execution stats are available via the activity log, which tracks every action with status, timestamps, and execution data.

## Key Sequence Settings

| Setting | Description |
|---|---|
| LinkedIn Daily Limit | Max LinkedIn actions per day (default 20) |
| X Daily Limit | Max X actions per day (default 40) |
| Auto-Enroll Active Buyers | Automatically add leads scored as active for this offer |
| AI Prompt | Custom AI instructions for message generation |
| DM Generation Prompt | Specific prompt for cold DM generation |
| Warmup Prompt | Prompt for warmup engagement |
| Skip Contacted Leads | Skip leads with prior contact history |
| Skip Negative Posts | Skip leads with negative content in recent posts |
| Skip Old Posts (days) | Skip leads whose recent posts are older than N days |
| Prefer Original Posts | Prefer original posts over reposts for engagement |
| AI Replies Off by Default | Disable AI auto-responses for new conversations |
| Max AI Responses per Conversation | Cap on AI responses per conversation (default 0 = unlimited) |

## Next Steps

- **[Building Sequences (Flow Editor)](building-sequences.md)**: Learn the sequence builder interface
- **[Supported Actions by Platform](supported-actions.md)**: Detailed reference for each action type on X vs LinkedIn
- **[DM Personalization](dm-personalization.md)**: How AI generates personalized first messages
- **[Scheduling](scheduling.md)**: Activity windows, timing, and send cadence
- **[Simulation and A/B Testing](simulation-and-testing.md)**: Preview messages and compare variants
