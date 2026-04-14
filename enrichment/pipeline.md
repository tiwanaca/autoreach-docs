# The Enrichment Pipeline

The enrichment pipeline transforms raw leads into rich, actionable profiles. Starting with just a name and platform URL, AutoReach progressively layers on social profiles, work history, recent activity, and scoring to build a complete picture of every lead.

## Pipeline Architecture

The pipeline runs all enrichment phases sequentially in a single job per lead. Each lead progresses through the phases below in order.

## Pipeline Phases

### Phase 1: Profile Enrichment

LinkedIn and X profile enrichment run **in parallel**:

**X enrichment** (when an X profile URL exists):
- Fetches profile data: user ID, DM availability, follower/following counts, verified status, profile image, bio, and name

**LinkedIn enrichment** (when a LinkedIn profile URL exists):
- Extracts full profile data: job title, company, work history, education, skills, certifications, languages, and network size

Failure on one platform does not block the other-  the pipeline continues with whatever data is available.

### Phase 2: Activity Enrichment

Fetches recent posts and engagement from LinkedIn (preferred) or X.

**What gets collected:**
- Recent posts (structured data and text for AI consumption)
- Interaction orbit-  who the lead interacts with on social media (powers Dark Funnel / orbit cluster signals)
- Signal date-  updated if any post is more recent than the current value

Activity failure is non-fatal-  the pipeline continues.

### Phase 3: Scoring

A full AI-powered analysis that evaluates fit, intent, and timing against your offer.

Post-scoring, several operations trigger:
- **Account signals:** Dark Funnel aggregation
- **Autopilot enrollment:** Checks if the lead qualifies for automatic sequence enrollment

### Phase 4: Finalize

- Lead status is set to ready
- Lead is added to the Lead Pool (for instant matching on future offers)
- Source search completion is checked

## Cross-Platform Profile Finding

Profile finding (searching for the lead's profile on the other platform) runs in **separate dedicated processes**, not as part of the main pipeline.

Profile finding only triggers when explicitly enabled-  this is not the default flow. See [Lead Pool](../finding-leads/lead-pool.md) for details.

## Web Enrichment (Optional)

A **separate, optional process** that is NOT part of the standard pipeline. Must be triggered independently.

Gathers company info, social profiles, and additional context from the web. See [Web Enrichment](web-enrichment.md) for details.

## Pipeline Modes

| Mode | What Runs | Use Case |
|---|---|---|
| **Full pipeline** | All phases (enrich + score) | Default for new leads |
| **Scoring-only** | Scoring phase only (profile and activity enrichment skipped) | Lead Pool matches |
| **Enrich-only** | Profile and activity enrichment only (no scoring) | Manual re-enrichment |
| **Manual re-enrich** | Selected enrichment types only | Targeted refresh of specific data |
| **No-op** | Leads immediately set to ready | When neither enrich nor scoring is needed |

## Pipeline Status Values

| Status | Meaning |
|---|---|
| Pending | Pipeline job queued but not yet started |
| Processing | Pipeline job is actively running |
| Ready | All phases complete |
| Billing Paused | Paused due to billing/credits issue |
| Outside Outreach Window | Deferred until outreach window opens |

## Pipeline Progress Tracking

Progress is tracked in real time and includes:
- Overall status: running, completed, or paused
- Counters: total, completed, enriching, scoring

## Recovery and Resilience

The pipeline automatically recovers from various failure scenarios-  stuck leads, interrupted jobs, and billing pauses are all handled without manual intervention. Leads that get stuck are automatically retried and eventually marked as ready so they don't block the pipeline.

## Intent-Based Prioritization

Leads sourced from intent signals (people actively posting about problems your product solves) are enriched and scored ahead of standard imports. High-priority leads enter the pipeline with higher priority scores and are processed first.

## From Enrichment to Outreach

Enriched data powers two core systems:

**Buyer Scoring** uses the full profile, activity history, and company context to calculate how likely a lead is to convert. Leads with richer enrichment data receive more accurate scores.

**Personalized Outreach** draws on enriched profiles to generate relevant messages. AI references recent posts, shared interests, role context, and company details to craft outreach that feels personal rather than templated.

**Enrichment quality matters**: Leads with incomplete social profiles or limited recent activity will receive lower scores and less personalized messaging. The more data available on a lead's public profiles, the better AutoReach can serve you.

## Next Steps

- **[Buyer Intelligence & Scoring](../core-concepts/buyer-intelligence.md)**: Learn how enriched data powers fit, intent, and timing scores
- **[Outreach Overview](../outreach/overview.md)**: See how enriched profiles drive personalized messaging
