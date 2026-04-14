# Continuous Operations

Once Autopilot is enabled, three continuous operations run in the background: auto-enrollment, buyer expansion, and monitor resurfacing. Together, they keep your pipeline growing and ensure qualified leads reach your sequences without manual intervention.

---

## Auto-Enrollment

Auto-enrollment is the bridge between lead scoring and outreach. It automatically moves qualified leads into sequences.

### How It Works

Autopilot regularly checks for enrollable leads. Each cycle:

1. Fetches leads in Active buyer state
2. Filters out leads already enrolled in the target sequence
3. Validates each lead has the required platform data
4. Enrolls qualified leads into the matching sequence

There is also a real-time enrollment hook: when scoring marks a lead as Active, enrollment can trigger immediately.

### Enrollment Criteria

A lead is enrolled when all conditions are met:

| Condition | Details |
|---|---|
| Buyer state | Must be Active |
| Sequence status | Must be active with auto-enrollment enabled |
| Offer match | Lead's offer must match the sequence's offer |
| Platform data | X requires an X profile; LinkedIn requires a LinkedIn profile |
| Not already enrolled | Lead must not already be in the sequence |

### Platform Routing

Leads are automatically routed to the correct platform sequence:

- Leads with X profile data go to the X sequence
- Leads with LinkedIn profile data go to the LinkedIn sequence
- Leads with both are enrolled in the sequence matching the Offer's primary platform

### Controlling Auto-Enrollment

When Autopilot is enabled, auto-enrollment is turned on for all newly created sequences by default. To review leads before enrollment, disable auto-enrollment on the sequence. Leads will then appear on the Buyers page for manual review.

---

## Buyer Expansion

Buyer Expansion discovers new prospects daily by mining your existing pipeline sources.

### X Expansion

On X, expansion works by increasing follower extraction targets on your seed accounts:

1. Calculates a daily batch of followers to extract
2. Increases the extraction target on the seed account
3. Triggers the extraction worker to pick up new followers
4. New followers enter the scoring pipeline automatically

Before expanding, Autopilot also triggers a **lead pool match** to find instant results from leads already in your database that match your ICP.

### LinkedIn Expansion

On LinkedIn, expansion takes a role-based approach:

1. Rotates through a priority list of decision-maker roles, one role per day
2. Searches for people matching the current role using your Offer's targeting criteria
3. If a role returns no results, immediately rotates to the next role

Roles are prioritized by seniority, searching for senior decision-makers first before moving to lower levels. This builds a well-rounded prospect list across different seniority levels at your target companies.

### Exhaustion Detection

Both platforms include automatic exhaustion detection:

- **X accounts**: Once all available followers are extracted, the source is marked exhausted. Lookalike rotation then finds a new seed account.
- **LinkedIn roles**: Once a role's results are exhausted, expansion moves to the next priority role.

---

## Monitor Resurfacing

Monitor Resurfacing re-checks lower-scored leads for new buying signals. Instead of abandoning leads that are not ready yet, Autopilot periodically evaluates them and upgrades them to active outreach when their signals improve.

### Check Frequency

Leads are checked on a regular schedule. Warmer leads are checked more frequently than colder leads, focusing attention on leads most likely to become ready for outreach soon.

### What Gets Checked

During each resurfacing window, Autopilot checks three categories of signals:

**Recent Activity** - Fetches new posts and social activity for the lead. New posts and engagement patterns are fed back into the scoring system.

**LinkedIn Headline Changes** - Compares the lead's current LinkedIn headline against the stored headline. If a change is detected, the lead receives a score boost and tenure is reset. A job change often indicates new priorities and buying intent.

**Company Jobs Refresh** - If the lead has an associated company and the company's hiring data is stale, Autopilot refreshes the company's job listings. Active hiring can indicate growth and budget availability.

### Score Upgrades

When resurfacing detects new signals and the lead's score improves:

- **Reaches Active threshold** - Lead is upgraded to Active buyer state and eligible for auto-enrollment into sequences
- **Score improves moderately** - Lead moves to a warmer tier with more frequent re-checks
- **No improvement** - Lead remains in its current tier and is re-checked at the next interval

Leads upgraded to Active are picked up by auto-enrollment and enrolled into the appropriate sequence.

## Next Steps

- **[Autopilot Overview](overview.md)**: All Autopilot operations at a glance
- **[Enabling and Disabling Autopilot](enabling.md)**: Setup, pausing, and disabling
