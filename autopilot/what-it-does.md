# What Autopilot Does

Once enabled, Autopilot runs five continuous operations in the background. Here's what each one does.

## Lookalike Rotation

Autopilot keeps your lead discovery fresh by rotating seed accounts automatically.

**How it works:**

1. Checks every 2 hours whether the current extraction source is exhausted
2. For X: checks if the target user's status is `failed`, `exhausted`, or all available followers have been extracted
3. For LinkedIn: checks if the seed search is marked exhausted and the role expansion queue is empty
4. When exhausted, searches for a new influencer account in your space using AI
5. Creates a new seed account and begins extracting followers
6. Tracks previously used accounts to avoid repeats

If Autopilot can't find a new seed after 3 consecutive attempts (all candidates already used), it sends a notification so you can add new accounts manually.

## Auto-Enrollment

Autopilot checks every 5 minutes for newly scored leads ready for outreach.

**Enrollment criteria:**

- Lead must be in `active` buyer state (score 60+)
- Lead must not already be enrolled in the sequence
- Lead must have the required platform data (X profile for X sequences; LinkedIn profile for LinkedIn sequences)
- Sequence must have `auto_enroll_active_leads` enabled and be in `active` or `scheduling` status
- Lead's scored offer must match the sequence's offer

**Per cycle:** Up to 200 leads are fetched from the database, filtered, and a maximum of **50 leads are enrolled per cycle**.

**Platform routing:** Leads are enrolled into the matching platform sequence — X leads go to the X sequence, LinkedIn leads go to the LinkedIn sequence.

Auto-enrollment also has a real-time hook: when scoring completes and a lead becomes `active`, enrollment can trigger immediately without waiting for the next 5-minute cycle.

## Buyer Expansion

Expansion discovers new prospects daily from your existing pipeline.

**X expansion:**
- Increases the follower extraction target by a daily batch (100–200 followers)
- Resets extraction status to `pending` so the extraction worker picks it up
- Also triggers a lead pool match job to find instant results from existing database leads

**LinkedIn expansion:**
- Rotates through role-based keyword searches, one role per day
- Priority roles: CEO, CTO, CFO, COO, Founder, VP, Director, Head, Manager, Lead, Partner, Owner
- Each daily run searches for one role with a cap of 100 leads
- If a role returns 0 results, it immediately rotates to the next role

**Both platforms:** Random 0–6 hour delay before triggering. 24-hour cooldown between runs. Respects the user's activity window (skips if in sleep mode).

Expansion runs every hour, checking if conditions are met for a new expansion cycle.

## Monitor Resurfacing

Resurfacing re-checks lower-scored leads on a tiered schedule, giving them another chance when new signals appear.

**Tiered check frequency:**

| Tier | Score Range | Re-check Interval |
|---|---|---|
| 1 (warmest) | 50–59 | Every 5 days |
| 2 | 40–49 | Every 10 days |
| 3 | 30–39 | Every 14 days |
| 4 (coldest) | 0–29 | Every 21 days |

**Resurfacing window:** Runs approximately every 8 hours with random jitter (0–60 minutes). Each window processes up to 40–60 leads within a 20-minute time budget per user.

**What it checks:**
- **Recent activity**: Fetches new posts and social signals
- **LinkedIn headline changes**: Detects job changes — triggers a +25 score boost and tenure reset
- **Company jobs refresh**: Updates hiring data if the lead's company jobs data is older than 7 days

**Score upgrades:**
- Score reaches 60+ → lead is upgraded to Active buyer state and eligible for auto-enrollment
- Score reaches 30–59 → lead moves from Poor Fit to Monitor state for more frequent re-checks

## Signal Search

The signal search loop runs every 5 minutes, checking for intent signal searches that need their first run. Once initial lead extraction completes, it triggers the signal search to find prospects actively posting about topics related to your offer.

## Next Steps

- **[Auto-Enrollment](auto-enrollment.md)**: Enrollment criteria and platform routing details
- **[Buyer Expansion](buyer-expansion.md)**: How X and LinkedIn expansion work
- **[Monitor Resurfacing](monitor-resurfacing.md)**: Tiered resurfacing and score upgrades
