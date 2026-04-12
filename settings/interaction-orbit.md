# Interaction Orbit (Dark Funnel)

Interaction Orbit detects the "dark funnel": buying behavior your leads do not explicitly post about but reveal through who they engage with.

## What Is the Dark Funnel?

Most buying signals are explicit: posting about a problem, asking for recommendations, mentioning a competitor. But many buying conversations happen privately in comments, DMs, and direct interactions, never visible in a post.

Interaction Orbit solves this by tracking **who your leads engage with** as a proxy for buying activity. If your lead is actively engaging with competitors, vendors in your space, and thought leaders, they are likely evaluating solutions.

## How It Works

AutoReach tracks engagement targets for each lead:

- **Likes, replies, comments** on posts
- **Profile visits** and follow patterns
- **Engagement frequency** over time

These targets are classified by relevance to your ICP, and patterns are detected in the last 30 days.

## Target Classifications

Each engagement target falls into one of these categories:

| Classification      | Signal Strength | Examples                             |
| ------------------- | --------------- | ------------------------------------ |
| **Competitor**      | High            | Directly selling in your space       |
| **Adjacent Vendor** | Medium          | Related tools or services            |
| **Thought Leader**  | Medium          | Industry experts, analysts           |
| **Influencer**      | Low             | Popular but not category-specific    |
| **Unknown**         | None            | Unclassified targets                 |

## Cluster Detection

AutoReach groups engagement targets into **clusters**: collections of related accounts your lead engages with together.

Example: A prospect actively engages with 3 data warehousing companies, 2 BI tool accounts, and 4 data engineering thought leaders. This forms a "data stack evaluation" cluster.

### Cluster Scoring

AutoReach scores clusters based on two key patterns:

- **New Cluster Activity**: When a lead begins engaging with competitor or vendor accounts for the first time, this signals they are actively evaluating solutions and boosts their intent score.
- **High Velocity Engagement**: When a lead frequently engages with offer-relevant clusters, this signals strong readiness to buy and boosts their timing score.

## Orbit Score Interpretation

| Score                            | Meaning                              | Action                       |
| -------------------------------- | ------------------------------------ | ---------------------------- |
| **New Cluster + Offer Match**    | Actively evaluating alternatives     | High priority for outreach   |
| **High Velocity + Relevant**     | Evaluating solutions actively        | Urgent. Timing is right      |
| **Moderate Engagement**          | Interested but not actively evaluating | Normal outreach priority   |
| **No Engagement**                | Not showing buying signals           | Lower priority               |

## Dark Funnel Advantages

### Reach Decision Makers Earlier
Leads show intent before posting publicly about it. You can reach them while they are still exploring.

### Avoid the Crowded Explicit Signal
When a prospect posts "Looking for a data warehouse," 50 vendors flood their inbox. Interaction Orbit finds them before that moment.

### Detect Account-Level Urgency
Multiple team members engaging with competitors signals company-wide evaluation. Interaction Orbit clusters this activity.

## Lead Profile Integration

When interaction orbit data is available, it appears on the lead profile as:

- **Orbit Targets** - list of accounts this lead engages with
- **Clusters Detected** - groups of related engagement targets
- **Cluster Velocity** - how frequently they are engaging (Rising, Stable, Cooling)
- **Timing Signal** - whether AutoReach detected high-intent engagement patterns

You can see which accounts the lead engages with, which clusters have been detected, how engagement velocity is trending, and whether any high-intent timing signals have been identified.

## Using Orbit Data in Sequences

When enrolling leads, filter by orbit signals:

- **Has Recent Cluster** - leads with new competitor/vendor engagement
- **High Velocity** - leads actively evaluating solutions
- **Offer-Relevant** - clusters matching your specific offering

This creates a highly targeted audience of leads showing both fit **and** intent.

{% hint style="tip" %}
Orbit data typically surfaces intent 2-4 weeks before explicit signals appear. This is your competitive advantage to reach prospects early.
{% endhint %}

## Privacy & Ethics

AutoReach only tracks public engagement:

- Public likes and replies (not DMs or private conversations)
- Public profile follows (not private contacts)
- Data aggregated at the lead level, never shared externally

This is similar to what you would manually discover by viewing someone's X or LinkedIn activity. AutoReach simply scales it.

## When Orbit Data Is Unavailable

Interaction Orbit requires:

- **Active social media presence** - lead must have posted or engaged in last 30 days
- **Trackable engagement** - platform allows viewing public engagement history
- **Target classification data** - database of competitor/vendor/thought leader accounts

If a lead lacks engagement history or accounts are private, Orbit data simply will not be available. AutoReach continues with other signals (explicit posts, profile data, fit scoring).

{% hint style="info" %}
Not all leads will have rich interaction orbit data. Focus on those who do. They are your highest-intent prospects.
{% endhint %}

## Next Steps

- **[Account-Level Signal Aggregation](account-signals.md)**: See how signals from multiple leads at one company combine
- **[Signal Detection](../core-concepts/signals.md)**: Review all the signal types that feed into scoring
