# The Enrichment Pipeline

The enrichment pipeline transforms raw leads into rich, actionable profiles. Starting with just a name and company, AutoReach progressively layers on social profiles, work history, recent activity, and location data to build a complete picture of every lead.

## How Enrichment Works

The pipeline runs through several stages, each adding a new layer of intelligence to your leads:

### Profile Discovery

AutoReach searches for your leads across X and LinkedIn, matching them to verified social profiles. This gives you direct channels for outreach and unlocks the data needed for later stages.

### Profile Enrichment

Once profiles are found, AutoReach pulls structured data from each platform:

- **X**: Bio, follower count, engagement metrics, DM eligibility
- **LinkedIn**: Job title, company, work history, skills, education, network size

### Activity Enrichment

Recent posts, replies, and engagement are collected from each lead's social accounts. This activity data serves two purposes: it reveals what your leads are currently thinking about, and it gives AI the context it needs to write relevant, personalized messages.

### Location Enrichment

Location data from social profiles is validated and standardized, giving you accurate geographic information for each lead.

### Scoring

With all enrichment data in hand, the scoring engine evaluates each lead across three dimensions:

- **Fit**: How closely does this lead match your ideal customer profile?
- **Intent**: Are they showing signals that suggest interest in your type of solution?
- **Timing**: How recently have they been active and engaged?

Each lead receives a composite buyer readiness score from 0 to 100.

## Intent-Based Prioritization

Not all leads are created equal. Leads sourced from intent signals (people actively posting about problems your product solves) are fast-tracked through the pipeline. These high-priority leads are enriched and scored ahead of standard imports, so you can act on the strongest opportunities first.

## Resilient Processing

The enrichment pipeline is built to handle interruptions gracefully.

{% hint style="success" %}
**Automatic Recovery**: If processing stalls or a step fails, the system automatically detects and resumes enrichment. No manual intervention is needed. You can monitor progress in the **Activity Log**.
{% endhint %}

Failed steps are automatically retried before moving on. If a particular data source is temporarily unavailable, the pipeline continues with the remaining steps and fills in gaps when possible.

## From Enrichment to Outreach

Enriched data powers two core systems:

**Buyer Scoring** uses the full profile, activity history, and company context to calculate how likely a lead is to convert. Leads with richer enrichment data receive more accurate scores.

**Personalized Outreach** draws on enriched profiles to generate relevant messages. AI references recent posts, shared interests, role context, and company details to craft outreach that feels personal rather than templated.

{% hint style="warning" %}
**Enrichment Quality Matters**: Leads with incomplete social profiles or limited recent activity will receive lower scores and less personalized messaging. The more data available on a lead's public profiles, the better AutoReach can serve you.
{% endhint %}

## Next Steps

- **[Buyer Intelligence & Scoring](../core-concepts/buyer-scoring.md)**: Learn how enriched data powers fit, intent, and timing scores
- **[Outreach Overview](../outreach/overview.md)**: See how enriched profiles drive personalized messaging
