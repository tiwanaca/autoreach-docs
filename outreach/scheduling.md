# Scheduling & Send Limits

AutoReach schedules sequence actions to look like natural human behavior-  spacing actions across the day, clustering them into sessions with breaks, and enforcing daily and weekly limits to keep accounts healthy.

## Activity Window

The activity window defines when outreach actions execute. Actions scheduled outside the window are deferred until the window opens.

The start and end times are configured in your Settings along with your timezone.

| Setting | Default |
|---|---|
| Start | 09:00 |
| End | 21:00 |
| Timezone | User-configured |

Actions scheduled outside the window are automatically deferred until the window opens.

## Action Scheduling

### How Actions Are Scheduled

The scheduler creates action records for each lead and processes them when their scheduled time arrives.

### Lead Priority

Higher-priority leads (based on buyer score and signal recency) get earlier time slots within the day.

### Timing Distribution

Actions are distributed across the activity window to simulate natural human behavior:

- **Natural spacing**-  actions are spread throughout the day with minimum gaps between them
- **Time-of-day variation**-  higher activity during peak hours, lower during early morning and evening
- **Session clustering**-  actions are grouped into human-like sessions with breaks between them
- **Day-of-week variation**-  weekday and weekend activity levels differ naturally

## Daily Send Limits

Daily limits are **per-sequence** (not per-account). Each sequence has its own counters.

### Action Limits

| Limit | Default | Maximum |
|---|---|---|
| LinkedIn daily actions | 20 | 100 |
| X daily actions | 40 | 100 |

All action types count toward their platform's limit: like, comment, follow, DM, connection request. Condition steps do not count.

### Enforcement

Limits reset at **midnight in your timezone**. If a limit is reached, remaining actions are deferred to the next day.

## Daily Connection Limits (LinkedIn)

LinkedIn connection requests have a separate daily limit tracked per-account (not per-sequence). When the limit is reached, pending connection requests are deferred to the next day. Other action types continue normally.

Set the daily connection limit on each LinkedIn account to match your account type. See [Supported Actions](supported-actions.md#connection-request) for the limits by account type.

## Natural Timing

All action execution includes natural pacing that simulates human behavior - browsing, reading, typing, and thinking pauses. Delays vary by action type, time of day, and day of week to create realistic patterns unique to each account.

Occasional random pauses are inserted between actions to simulate natural breaks and distractions.

## Gradual Resumption

When a paused sequence is resumed or actions become overdue, they are spread across time instead of firing all at once. This keeps activity patterns looking natural.

## Max AI Responses Per Conversation

Limits how many times AI auto-replies in a single conversation:

| Setting | Default | Maximum |
|---|---|---|
| Max AI responses per conversation | 0 (unlimited) | 100 |

When set to 0, AI auto-replies are unlimited-  the AI will continue responding as long as the conversation is active. When set to a positive number, AI responds up to that many times per conversation, then stops.

## Next Steps

- **[Building Sequences](building-sequences.md)**: Configure limits and timing per sequence
- **[Supported Actions](supported-actions.md)**: Action-specific rate limits and behaviors
- **[Outreach Overview](overview.md)**: How sequences work end-to-end
