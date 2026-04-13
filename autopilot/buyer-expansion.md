# Buyer Expansion

Buyer Expansion discovers new prospects daily by mining your existing pipeline sources. It runs every hour, checking if conditions are met for a new expansion cycle.

## How Expansion Works

Each expansion cycle has a 24-hour cooldown (`buyer_expansion_last_run_at`) and a random 0–6 hour delay before triggering. Expansion respects the user's activity window and skips execution during sleep hours.

Before expanding, Autopilot triggers a **lead pool match** job to find instant results from leads already in your database that match your ICP.

## X Expansion

On X, expansion works by increasing follower extraction targets on your seed accounts:

1. Calculates a daily batch size (100–200 followers, based on total available followers)
2. Increments `total_to_extract` on the target user by the batch amount
3. Resets extraction status to `pending` so the extraction worker picks it up
4. New followers enter the scoring pipeline automatically

This keeps a steady flow of new prospects from your seed accounts without exhausting them all at once.

## LinkedIn Expansion

On LinkedIn, expansion takes a role-based approach:

1. Rotates through a priority list of decision-maker roles, one role per day
2. Searches for people matching the current role using your Offer's targeting criteria
3. Caps each daily search at **100 leads**
4. If a role returns 0 results, immediately rotates to the next role without waiting

**Priority roles (in order):** CEO, CTO, CFO, COO, Founder, VP, Director, Head, Manager, Lead, Partner, Owner

This rotation builds a well-rounded prospect list across different seniority levels at your target companies.

## Exhaustion Detection

Both platforms include automatic exhaustion detection:

- **X accounts**: Once all available followers are extracted, the source is marked exhausted. Lookalike rotation (every 2 hours) then finds a new seed account.
- **LinkedIn roles**: Once a role's pagination is complete, expansion moves to the next priority role in the queue.

## Next Steps

- **[Auto-Enrollment](auto-enrollment.md)**: How expanded leads get enrolled into sequences
- **[Monitor Resurfacing](monitor-resurfacing.md)**: How leads below enrollment threshold get re-checked
