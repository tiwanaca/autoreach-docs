# Buyer Expansion

Buyer Expansion discovers new prospects daily by mining your existing pipeline sources. It runs every hour, checking if conditions are met for a new expansion cycle.

## How Expansion Works

Each expansion cycle has a cooldown period between runs. Expansion respects the user's activity window and skips execution during sleep hours.

Before expanding, Autopilot triggers a **lead pool match** job to find instant results from leads already in your database that match your ICP.

## X Expansion

On X, expansion works by increasing follower extraction targets on your seed accounts:

1. Calculates a daily batch of followers to extract
2. Increases the extraction target on the seed account
3. Triggers the extraction worker to pick up new followers
4. New followers enter the scoring pipeline automatically

This keeps a steady flow of new prospects from your seed accounts without exhausting them all at once.

## LinkedIn Expansion

On LinkedIn, expansion takes a role-based approach:

1. Rotates through a priority list of decision-maker roles, one role per day
2. Searches for people matching the current role using your Offer's targeting criteria
3. If a role returns no results, immediately rotates to the next role without waiting

Roles are prioritized by seniority, searching for senior decision-makers first before moving to lower levels.

This rotation builds a well-rounded prospect list across different seniority levels at your target companies.

## Exhaustion Detection

Both platforms include automatic exhaustion detection:

- **X accounts**: Once all available followers are extracted, the source is marked exhausted. Lookalike rotation then finds a new seed account.
- **LinkedIn roles**: Once a role's pagination is complete, expansion moves to the next priority role in the queue.

## Next Steps

- **[Auto-Enrollment](auto-enrollment.md)**: How expanded leads get enrolled into sequences
- **[Monitor Resurfacing](monitor-resurfacing.md)**: How leads below enrollment threshold get re-checked
