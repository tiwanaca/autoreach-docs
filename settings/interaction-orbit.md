# Interaction Orbit (Dark Funnel)

Interaction Orbit detects the "dark funnel"—buying behavior your leads don't explicitly post about but reveal through who they engage with.

## What Is the Dark Funnel?

Most buying signals are explicit: posting about a problem, asking for recommendations, mentioning a competitor. But many buying conversations happen privately—in comments, DMs, direct interactions—never visible in a post.

Interaction Orbit solves this by tracking **who your leads engage with** as a proxy for buying activity. If your lead is actively engaging with competitors, vendors in your space, and thought leaders, they're likely evaluating solutions.

## How It Works

AutoReach tracks engagement targets for each lead:

- **Likes, replies, comments** on posts
- **Profile visits** and follow patterns
- **Engagement frequency** over time

These targets are classified by relevance to your ICP, and patterns are detected in the last 30 days.

## Target Classifications

Each engagement target falls into one of these categories:

| Classification | Signal Strength | Examples |
|---|---|---|
| **Competitor** | High | Directly selling in your space |
| **Adjacent Vendor** | Medium | Related tools or services |
| **Thought Leader** | Medium | Industry experts, analysts |
| **Influencer** | Low | Popular but not category-specific |
| **Unknown** | None | Unclassified targets |

## Cluster Detection

AutoReach groups engagement targets into **clusters**—collections of related accounts your lead engages with together.

Example: A prospect actively engages with 3 data warehousing companies, 2 BI tool accounts, and 4 data engineering thought leaders. This forms a "data stack evaluation" cluster.

### Cluster Scoring

**New Cluster Boost** (last 30 days):
- Lead engages with 2+ accounts in competitor/vendor clusters for first time
- Signal: `intent_score >= 65` (high purchase intent)
- Reasoning: Evaluating solutions they haven't engaged with before

**High Velocity Boost** (frequent engagement):
- Lead engages 3+ times with offer-relevant clusters in last 30 days
- Signal: `timing_score >= 70` (high readiness to buy)
- Reasoning: Active, ongoing evaluation behavior

## Orbit Score Interpretation

| Score | Meaning | Action |
|-------|---------|--------|
| **New Cluster + Offer Match** | Actively evaluating alternatives | High priority for outreach |
| **High Velocity + Relevant** | Evaluating solutions actively | Urgent—timing is right |
| **Moderate Engagement** | Interested but not actively evaluating | Normal outreach priority |
| **No Engagement** | Not showing buying signals | Lower priority |

## Dark Funnel Advantages

### Reach Decision Makers Earlier
Leads show intent before posting publicly about it. You can reach them while they're still exploring.

### Avoid the Crowded Explicit Signal
When a prospect posts "Looking for a data warehouse," 50 vendors flood their inbox. Interaction Orbit finds them before that moment.

### Detect Account-Level Urgency
Multiple team members engaging with competitors signals company-wide evaluation. Interaction Orbit clusters this activity.

## Lead Profile Integration

When interaction orbit data is available, it appears on the lead profile as:

- **Orbit Targets** — List of accounts this lead engages with
- **Clusters Detected** — Groups of related engagement targets
- **Cluster Velocity** — How frequently they're engaging (Rising, Stable, Cooling)
- **Timing Signal** — Whether AutoReach detected high-intent engagement patterns

Example display:
```
ORBIT ACTIVITY (last 30 days)
├── Data Stack Cluster (Velocity: Rising)
│   ├── Competitor: Snowflake (2 likes, 1 reply)
│   ├── Vendor: dbt Labs (1 like, 2 replies)
│   └── Thought Leader: @data_eng_podcast (3 likes)
└── Recommendation Signal Detected (timing_score: 72)
```

## Using Orbit Data in Sequences

When enrolling leads, filter by orbit signals:

- **Has Recent Cluster** — Leads with new competitor/vendor engagement
- **High Velocity** — Leads actively evaluating solutions
- **Offer-Relevant** — Clusters matching your specific offering

This creates a highly targeted audience of leads showing both fit **and** intent.

{% hint style="tip" %}
Orbit data typically surfaces intent 2-4 weeks before explicit signals appear. This is your competitive advantage to reach prospects early.
{% endhint %}

## Privacy & Ethics

AutoReach only tracks public engagement:

- Public likes and replies (not DMs or private conversations)
- Public profile follows (not private contacts)
- Data aggregated at the lead level, never shared externally

This is similar to what you'd manually discover by viewing someone's Twitter or LinkedIn activity—AutoReach just scales it.

## When Orbit Data Is Unavailable

Interaction Orbit requires:

- **Active social media presence** — Lead must have posted or engaged in last 30 days
- **Trackable engagement** — Platform allows viewing public engagement history
- **Target classification data** — Database of competitor/vendor/thought leader accounts

If a lead lacks engagement history or accounts are private, Orbit data simply won't be available. AutoReach continues with other signals (explicit posts, profile data, fit scoring).

{% hint style="info" %}
Not all leads will have rich interaction orbit data. Focus on those who do—they're your highest-intent prospects.
{% endhint %}
