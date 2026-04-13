# Scheduling & Send Limits

AutoReach schedules sequence actions to look like natural human behavior — spacing actions across the day, clustering them into sessions with breaks, and enforcing daily and weekly limits to keep accounts healthy.

## Activity Window

The activity window defines when outreach actions execute. Actions scheduled outside the window are deferred until the window opens.

The start and end times are configured in your Settings along with your timezone.

| Setting | Default |
|---|---|
| Start | 09:00 |
| End | 21:00 |
| Timezone | User-configured |

**Enforcement:** The system checks your outreach window before executing each action. If the current time is outside the window (sleep period), the action is rescheduled to 30 minutes after the window reopens.

For example, with a 09:00–21:00 window, the sleep period is 21:00–09:00. Midnight crossing is handled correctly based on your timezone.

## Action Scheduling

### How Actions Are Scheduled

The scheduler creates action records for each lead. The system polls every **2 minutes** for pending actions whose scheduled time has arrived.

### Lead Priority

Leads are scheduled in buyer priority order:

1. **Purchase probability** (highest first)
2. **Signal date** (most recent first)
3. **Has explicit signal** (true before false)

Higher-priority leads get earlier time slots within the day.

### Time Slot Algorithm

Actions are distributed across the activity window using several techniques:

**Action scattering** — actions are distributed across scattered positions in the window so that X and LinkedIn actions alternate naturally instead of segregating by platform.

**Time-of-day weighting** — different hours have different activity weights. Peak activity occurs during lunch hours and after work, while early morning, evening, and night hours have reduced activity. This mirrors natural human behavior patterns.

**Global action spacing** — a minimum **5-minute gap** between any two actions across all sequences for the same user. Prevents simultaneous actions from looking automated.

### Session Clustering

Actions are grouped into human-like sessions with gaps:

| Daily Action Count | Sessions | Gap Between Sessions |
|---|---|---|
| 1–3 actions | 1 session | — |
| 4–30 actions | 2–3 sessions | 1 hour |
| 30+ actions | Single session | Micro-breaks instead |

**Micro-breaks** — every 3–7 actions, an 8–20 minute break is inserted, creating natural bursts separated by pauses.

**Deterministic jitter** — timing variance is deterministic per day + account + slot index, ensuring consistency across reschedules.

## Daily Send Limits

Daily limits are **per-sequence** (not per-account). Each sequence has its own counters.

### Action Limits

| Limit | Default | Maximum |
|---|---|---|
| Combined daily actions | 20 | 100 |
| LinkedIn daily actions | 20 | 100 |
| X daily actions | 40 | 100 |

All action types count toward the limit: like, reply, follow, dm, connection_request, view_profile. Condition steps do not count.

### DM Limits

A separate **daily DM limit** exists per sequence, tracked independently from the combined action limit. Both are checked — if either is reached, actions are blocked.

### Limit Reset

Limits reset at **midnight in the user's timezone**. The reset is lazy — triggered on the first action check after midnight. All daily counters (combined, LinkedIn, and X) are set to 0.

### Enforcement

Before each action, the system checks the appropriate counter against the limit:

- LinkedIn actions: checks LinkedIn-specific count/limit
- X actions: checks X-specific count/limit
- Other actions: checks combined count/limit

If the limit is reached, the action is rescheduled for the next day at a random time within the activity window.

## Weekly Connection Limits (LinkedIn)

LinkedIn connection requests have a separate weekly limit tracked per-account (not per-sequence), resetting Monday 00:00 UTC. When the limit is reached, pending connection request actions are batch-deferred to the following Monday (spaced 15-25 minutes apart). Other action types continue normally and leads stay in their sequences.

Set the weekly connection limit on each LinkedIn account to match your account type. See [Supported Actions](supported-actions.md#connection-request) for the limits by account type and detailed deferral behavior.

## Human Delay Simulation

All action execution includes anti-detection timing that simulates human behavior:

### Delay Types

| Delay | Duration | Applied When |
|---|---|---|
| Browse simulation | 3–8 seconds | Before any action |
| Read simulation | 1–20 seconds (based on text length) | Before like or reply |
| Typing simulation | Based on message length at ~45 WPM | Before DM or reply |
| Profile check | 1–3 seconds | Before DM |
| Think time | 5–10 seconds | Before DM |
| Open DM delay | 2–5 seconds | Before DM |
| Re-edit delay | 1–3 seconds | Before sending DM |

### Delay Multipliers

Delays are adjusted based on multiple factors to create realistic variation:

- **Time-of-day**: Actions are slower in early morning and late night, faster during peak productivity hours
- **Day-of-week**: Weekdays are faster than weekends, with mid-week being the most productive
- **Account personality**: Each account has a consistent behavioral profile that creates unique, persistent timing patterns

### Distraction Events

Occasional random pauses are inserted between actions to simulate natural distractions — brief pauses, medium breaks, or longer session breaks after extended activity. This creates organic-looking gaps in action timing.

## Anti-Burst Protection

When a paused sequence is resumed or actions become overdue, anti-burst protection activates.

**Trigger:** More than 5 past-due actions (overdue by 5+ minutes).

**Behavior:**
- First action executes immediately
- Remaining actions are rescheduled 15–25 minutes apart
- Example: 10 overdue actions → spread over 2–3 hours instead of firing all at once

This also applies when deferred LinkedIn connection requests resume on Monday.

## Max AI Responses Per Conversation

Limits how many times AI auto-replies in a single conversation:

| Setting | Default | Maximum |
|---|---|---|
| Max AI responses per conversation | 0 (unlimited) | 100 |

When set to 0, AI auto-replies are unlimited — the AI will continue responding as long as the conversation is active. When set to a positive number, AI responds up to that many times per conversation, then stops.

## Next Steps

- **[Building Sequences](building-sequences.md)**: Configure limits and timing per sequence
- **[Supported Actions](supported-actions.md)**: Action-specific rate limits and behaviors
- **[Outreach Overview](overview.md)**: How sequences work end-to-end
