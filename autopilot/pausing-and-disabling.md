# Pausing and Disabling Autopilot

You can pause or disable Autopilot at any time. Both options preserve your leads and conversation history — the difference is how much automation infrastructure is cleaned up.

## Pause vs. Disable

| | Pause | Disable |
|---|---|---|
| **Config status** | `paused` | `disabled` |
| **Searches** | Set to `daily_recurring: false` (preserved) | Deleted |
| **Sequences** | Set to `paused` status | Set to `paused` status, `auto_enroll_active_leads` set to `false` |
| **Target users (X)** | Unchanged | Set to `paused` status, `buyer_expansion: false` |
| **LinkedIn seed searches** | Unchanged | Set to `buyer_expansion: false` |
| **Lookalike accounts** | Preserved | Deleted |
| **Leads & conversations** | Preserved | Preserved |
| **Pipeline progress (Redis)** | Preserved | Cleared |
| **Resume** | Yes — instant | Must re-enable (creates fresh resources) |

## When to Pause

Pause when you want to temporarily stop all Autopilot operations and resume later exactly where you left off:

- Vacations or short breaks
- Account maintenance
- Adjusting settings before resuming

**To pause:** Go to the Autopilot Dashboard and click **Pause**.

**To resume:** Click **Resume**. Autopilot restores `daily_recurring: true` on searches, sets sequences back to `active`, and sets config status back to `active`. Operations resume on their regular intervals.

## When to Disable

Disable when you're stopping outreach for the long term or want a clean slate:

- Fully stopping outreach for an Offer
- Switching to manual-only mode
- Pivoting to a different ICP

**To disable:** Go to the Autopilot Dashboard, open Settings, and select **Disable Autopilot**.

Disabling cleans up automation infrastructure (searches, lookalike accounts, expansion settings) but preserves all leads, conversations, and historical data.

## Re-enabling After Disable

When you re-enable Autopilot after disabling:

- New sequences, searches, and lookalike accounts are created fresh
- AI generates a new campaign prompt and tone examples
- New seed accounts are discovered for follower extraction
- Existing leads in your database are preserved and can be re-scored
- The enable process is the same as the first time — runs in the background in 1–2 minutes

## Pausing Individual Sequences

You can pause a single sequence without affecting the rest of Autopilot:

1. Go to **Sequences**
2. Select the sequence
3. Click **Pause Sequence**

This stops outreach for that sequence only. Other sequences and Autopilot operations continue normally.

## Next Steps

- **[Enabling Autopilot](enabling.md)**: The enable/re-enable process
- **[Autopilot Overview](overview.md)**: All Autopilot operations at a glance
