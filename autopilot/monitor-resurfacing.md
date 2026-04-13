# Monitor Resurfacing

Monitor Resurfacing re-checks lower-scored leads for new buying signals on a tiered schedule. Instead of abandoning leads that aren't ready yet, Autopilot periodically evaluates them and upgrades them to active outreach when their signals improve.

## Tiered Check Frequency

Leads are grouped into tiers based on their current score. Warmer leads are checked more frequently:

| Tier | Score Range | Re-check Interval |
|---|---|---|
| 1 (warmest) | 50–59 | Every 5 days |
| 2 | 40–49 | Every 10 days |
| 3 | 30–39 | Every 14 days |
| 4 (coldest) | 0–29 | Every 21 days |

## Resurfacing Schedule

The resurfacing process runs periodically throughout the day.

## What Gets Checked

During each resurfacing window, Autopilot checks three categories of signals:

### Recent Activity

Fetches new posts and social activity for the lead using the standard activity fetching pipeline. New posts and engagement patterns are fed back into the scoring system.

### LinkedIn Headline Changes

Compares the lead's current LinkedIn headline against the stored headline. If a change is detected:

- Lead receives a score boost
- Tenure (time in current role) is reset
- This is one of the highest-signal events -- a job change often indicates new priorities and buying intent

### Company Jobs Refresh

If the lead has an associated company and the company's hiring data is stale, Autopilot refreshes the company's job listings. Active hiring can indicate growth and budget availability.

## Score Upgrades

When resurfacing detects new signals and the lead's score improves:

| New Score | Action |
|---|---|
| 60+ | Lead is upgraded to Active buyer state — eligible for auto-enrollment into sequences |
| 30–59 | Lead moves from Poor Fit to Monitor state, entering a more frequent re-check tier |
| Below 30 | Lead remains in its current tier and is re-checked at the tier's interval |

Leads upgraded to Active are picked up by the auto-enrollment loop and enrolled into the appropriate sequence.

## Why Tiered Frequency

Checking all leads daily would create unnecessary load without meaningful benefit. Tiered frequency focuses attention on warmer prospects (more likely to cross the activation threshold soon) while still monitoring colder leads at reasonable intervals.

## Next Steps

- **[Auto-Enrollment](auto-enrollment.md)**: How upgraded leads get enrolled into sequences
- **[What Autopilot Does](what-it-does.md)**: All continuous Autopilot operations
