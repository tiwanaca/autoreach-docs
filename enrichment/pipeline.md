# The Enrichment Pipeline

The enrichment pipeline transforms raw leads into rich, actionable profiles. Starting with just a name and platform URL, AutoReach progressively layers on social profiles, work history, recent activity, and scoring to build a complete picture of every lead.

## Pipeline Architecture

The pipeline runs all enrichment phases sequentially in a single job per lead. Each lead progresses through the phases below in order.

## Pipeline Phases

### Pre-check: Outreach Window

Before enrichment begins, the system checks if the LinkedIn/X account is in its outreach window sleep period. If so, the job is deferred until the window opens.

### Phase 1: Profile Enrichment

LinkedIn and X profile enrichment run **in parallel**:

**X enrichment** (when an X profile URL exists):
- Fetches profile data: user ID, DM availability, follower/following counts, verified status, profile image, bio, and name

**LinkedIn enrichment** (when a LinkedIn profile URL exists):
- Extracts full profile data: job title, company, work history, education, skills, certifications, languages, and network size

Transient errors (budget exceeded, gateway timeout, account paused) cause the job to be retried later. Permanent errors are logged and the pipeline continues -- failure on one platform does not block the other.

### Phase 2: Activity Enrichment

Fetches recent posts and engagement from LinkedIn if available, otherwise falls back to X.

**What gets collected:**
- Recent posts (structured data and text for AI consumption)
- Interaction orbit -- who the lead interacts with on social media (powers Dark Funnel / orbit cluster signals)
- Signal date -- updated if any post is more recent than the current value

Posts older than 6 months are filtered out. If the fetch succeeds with 0 posts, the lead is flagged to prevent repeated fetches on inactive accounts.

Activity failure is non-fatal -- the pipeline continues.

### Phase 3: Location Enrichment (Conditional)

**Only runs when explicitly opted into** and a Twitter account is available. This is not a default step -- most leads skip it.

Failure is non-fatal.

### Phase 4: Scoring

Only runs in full pipeline mode when scoring is not explicitly skipped. This is a full LLM-powered analysis that evaluates fit, intent, and timing.

Special handling for own-post engagement leads with no explicit offer: scored against all active offers, and the best-scoring one is assigned.

Post-scoring, several operations trigger:
- **Webhook:** Lead scored event
- **Account signals:** Dark Funnel aggregation
- **Autopilot enrollment:** Checks if the lead qualifies for automatic sequence enrollment

If the user's billing is paused, the pipeline halts until billing is restored.

### Phase 5: Finalize

- Lead status is set to ready
- Pipeline progress counters are updated
- Lead is added to the global Lead Pool (for cross-user matching)
- Enrichment completed webhook fires
- Source search completion is checked

## Cross-Platform Profile Finding

Profile finding (searching for the lead's profile on the other platform) runs in **separate dedicated processes**, not as part of the main pipeline:

| Type | Rate Limit |
|---|---|
| X profile finder | -- |
| LinkedIn profile finder | 2/min |

Profile finding only triggers when explicitly enabled -- this is not the default flow. If no profile is found, the corresponding enrichment step is skipped.

## Web Enrichment (Optional)

A **separate, optional process** (rate limit: 5/min) that is NOT part of the standard pipeline. Must be triggered independently.

Requires the lead to have a LinkedIn profile URL, website URL, or bio longer than 20 characters. Gathers company info, social profiles, and a confidence score. Also promotes company size to the employee count field if not already set.

## Pipeline Modes

| Mode | What Runs | Use Case |
|---|---|---|
| **Full pipeline** | All phases (enrich + score) | Default for new leads |
| **Scoring-only** | Phase 4 only (Phases 1-3 skipped) | Lead Pool matches |
| **Enrich-only** | Phases 1-3 only (no scoring) | Manual re-enrichment |
| **Manual re-enrich** | Selected enrichment types only | Targeted refresh of specific data |
| **No-op** | Leads immediately set to ready | When neither enrich nor scoring is needed |

## Pipeline Status Values

| Status | Meaning |
|---|---|
| Processing | Pipeline job is actively running |
| Ready | All phases complete |
| Billing Paused | Paused due to billing/credits issue |
| Outside Outreach Window | Deferred until outreach window opens |

## Pipeline Progress Tracking

Progress is tracked in real time and includes:
- Overall status: running, completed, or paused
- Counters: total, completed, enriching, scoring

## Recovery and Resilience

The system automatically recovers from various failure scenarios:

1. **Stuck leads** -- leads stuck in processing for too long are automatically retried. After multiple recovery attempts, the lead is marked as ready so it does not block the pipeline indefinitely.
2. **Scored but not finalized** -- leads with scores that were never marked as ready are automatically corrected.
3. **Unscored ready leads** -- leads that reached ready without being scored are picked up and scored.
4. **Leads that never started** -- leads with pipeline config that never began processing are automatically started.
5. **Stuck searches** -- source searches stuck in an active state are recovered.
6. **Billing-paused leads** -- automatically resumed when credits are restored.

## Throughput Summary

| Enrichment Type | Rate Limit |
|---|---|
| X profile enrichment | 3/min |
| X profile finder | -- |
| LinkedIn profile enrichment | 5/min (per account) |
| LinkedIn profile finder | 2/min |
| Web enrichment | 5/min |

## Intent-Based Prioritization

Leads sourced from intent signals (people actively posting about problems your product solves) are enriched and scored ahead of standard imports. High-priority leads enter the pipeline with higher priority scores and are processed first.

## From Enrichment to Outreach

Enriched data powers two core systems:

**Buyer Scoring** uses the full profile, activity history, and company context to calculate how likely a lead is to convert. Leads with richer enrichment data receive more accurate scores.

**Personalized Outreach** draws on enriched profiles to generate relevant messages. AI references recent posts, shared interests, role context, and company details to craft outreach that feels personal rather than templated.

**Enrichment quality matters**: Leads with incomplete social profiles or limited recent activity will receive lower scores and less personalized messaging. The more data available on a lead's public profiles, the better AutoReach can serve you.

## Next Steps

- **[Buyer Intelligence & Scoring](../core-concepts/buyer-scoring.md)**: Learn how enriched data powers fit, intent, and timing scores
- **[Outreach Overview](../outreach/overview.md)**: See how enriched profiles drive personalized messaging
