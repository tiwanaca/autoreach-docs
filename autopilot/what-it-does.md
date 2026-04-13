# What Autopilot Does

Once enabled, Autopilot runs five continuous operations in the background. Here's what each one does.

## Lookalike Rotation

Autopilot keeps your lead discovery fresh by rotating seed accounts automatically.

**How it works:**

1. Checks periodically whether the current extraction source is exhausted
2. For X: checks if the follower extraction has completed or all available followers have been extracted
3. For LinkedIn: checks if the seed search is complete and the role expansion queue is empty
4. When exhausted, searches for a new influencer account in your space using AI
5. Creates a new seed account and begins extracting followers
6. Tracks previously used accounts to avoid repeats

If Autopilot can't find a new seed after 3 consecutive attempts (all candidates already used), it sends a notification so you can add new accounts manually.

## Auto-Enrollment

Autopilot checks regularly for newly scored leads ready for outreach.

**Enrollment criteria:**

- Lead must be in Active buyer state
- Lead must not already be enrolled in the sequence
- Lead must have the required platform data (X profile for X sequences; LinkedIn profile for LinkedIn sequences)
- Sequence must have auto-enrollment enabled and be in an active status
- Lead's scored offer must match the sequence's offer

**Platform routing:** Leads are enrolled into the matching platform sequence -- X leads go to the X sequence, LinkedIn leads go to the LinkedIn sequence.

Auto-enrollment also has a real-time hook: when scoring completes and a lead becomes Active, enrollment can trigger immediately.

## Buyer Expansion

Expansion discovers new prospects daily from your existing pipeline.

**X expansion:**
- Increases the follower extraction target by a daily batch
- Triggers the extraction worker to pick up new followers
- Also triggers a lead pool match job to find instant results from existing database leads

**LinkedIn expansion:**
- Rotates through role-based keyword searches, one role per day
- Searches for senior decision-makers by role seniority
- If a role returns no results, it immediately rotates to the next role

**Both platforms:** Expansion runs periodically with a cooldown between runs. It respects the user's activity window and skips execution during sleep hours.

## Monitor Resurfacing

Resurfacing re-checks lower-scored leads on a tiered schedule, giving them another chance when new signals appear.

**Tiered check frequency:**

| Tier | Score Range | Re-check Interval |
|---|---|---|
| 1 (warmest) | 50–59 | Every 5 days |
| 2 | 40–49 | Every 10 days |
| 3 | 30–39 | Every 14 days |
| 4 (coldest) | 0–29 | Every 21 days |

**What it checks:**
- **Recent activity**: Fetches new posts and social signals
- **LinkedIn headline changes**: Detects job changes -- a strong buying signal that boosts the lead's score and resets tenure
- **Company jobs refresh**: Updates hiring data periodically

**Score upgrades:**
- Score reaches Active threshold -- lead is upgraded to Active buyer state and eligible for auto-enrollment
- Score improves moderately -- lead moves from Poor Fit to Monitor state for more frequent re-checks

## Signal Search

The signal search loop runs periodically, checking for intent signal searches that need their first run. Once initial lead extraction completes, it triggers the signal search to find prospects actively posting about topics related to your offer.

## Next Steps

- **[Auto-Enrollment](auto-enrollment.md)**: Enrollment criteria and platform routing details
- **[Buyer Expansion](buyer-expansion.md)**: How X and LinkedIn expansion work
- **[Monitor Resurfacing](monitor-resurfacing.md)**: Tiered resurfacing and score upgrades
