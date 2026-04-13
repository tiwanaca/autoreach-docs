# Auto-Enrollment

Auto-enrollment is the bridge between lead scoring and outreach. It automatically moves qualified leads into sequences without manual intervention.

## How It Works

Autopilot checks for enrollable leads every **5 minutes**. Each cycle:

1. Fetches up to 200 leads in "Active" buyer state (score 60+)
2. Filters out leads already enrolled in the target sequence
3. Validates each lead has the required platform data
4. Enrolls up to **50 leads per cycle** into the matching sequence

There is also a real-time enrollment hook: when scoring marks a lead as "Active", enrollment can trigger immediately without waiting for the next 5-minute cycle.

## Enrollment Criteria

A lead is enrolled when all conditions are met:

| Condition | Details |
|---|---|
| Buyer state | Must be "Active" (score 60+) |
| Sequence status | Must be "Active" or "Scheduling" with auto-enrollment enabled |
| Offer match | Lead's offer must match the sequence's offer |
| Platform data | X requires an X profile; LinkedIn requires a LinkedIn profile |
| Not already enrolled | Lead must not already be enrolled in the sequence |

## Platform Routing

Leads are automatically routed to the correct platform sequence:

- Leads with X profile data → X sequence
- Leads with LinkedIn profile data → LinkedIn sequence
- Leads with both → enrolled in the sequence matching the Offer's primary platform

## When Auto-Enroll Is Active

When Autopilot is enabled, auto-enrollment is turned on for all newly created sequences by default. This means qualified leads go directly into sequences and do **not** appear on the Buyers page.

To review leads before enrollment, disable auto-enrollment on the sequence. Leads will then appear on the Buyers page for manual review.

## Avoiding Double-Enrollment

The system checks for existing enrollment before each attempt to prevent duplicates. A lead is skipped if they are already in the sequence at any status (active, paused, completed, replied, etc.).

## Next Steps

- **[Buyer Expansion](buyer-expansion.md)**: How Autopilot discovers new leads to feed enrollment
- **[Monitor Resurfacing](monitor-resurfacing.md)**: How lower-scored leads get re-checked and upgraded to enrollment eligibility
