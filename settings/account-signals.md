# Account-Level Signal Aggregation

Account-Level Signal Aggregation combines buying signals from multiple leads at the same company to create an "account heat score"—a single indicator of company-wide purchase intent.

## How It Works

When AutoReach detects multiple leads from the same company:

1. Collects all buying signals from each lead
2. Weighs signals by strength and recency
3. Applies a diversity multiplier (more contacts = higher score)
4. Produces an account heat score (0-100)

This surfaces when an entire company is actively evaluating solutions, even if individual lead signals are light.

## Signal Strength Points

Each buying signal contributes points based on its strength:

| Signal Strength | Points |
|---|---|
| **High** | +10 |
| **Medium** | +5 |
| **Low** | +2 |

Signal strength depends on the signal type and recency. Recent signals are weighted more heavily than older ones.

## Diversity Multiplier

The more contacts from the same company showing signals, the stronger the account-level intent:

| Contacts with Signals | Multiplier |
|---|---|
| 1 person | 1.0x (no boost) |
| 2 people | 1.3x |
| 3 people | 1.6x |
| 4+ people | 2.0x (capped) |

**Example:**
- 1 contact with signals totaling 15 points = 15 × 1.0 = 15 heat score
- 3 contacts with signals totaling 15 points = 15 × 1.6 = 24 heat score
- Same total signals, but wider distribution = stronger account signal

## Heat Score Formula

```
Heat Score = (Signal Strength Sum + Recency Bonus) × Diversity Multiplier
Capped at 100
```

### Recency Bonus
- **+5 points** for each signal from the last 7 days
- Older signals decay but still count (just less)

**Example:**
```
3 contacts from Acme Corp:
- Contact A: posted about tool searching (Medium, 2 days ago) = 5 + 5 = 10 points
- Contact B: engaged with competitor posts (Medium, 3 days ago) = 5 + 5 = 10 points
- Contact C: mentioned hiring (Low, 12 days ago) = 2 + 0 = 2 points
Total: 22 points × 1.6 diversity = 35 heat score
```

## Fit Gate

Not all signals are weighted equally. Signals only boost account heat if they come from leads with sufficient fit:

- **Fit ≥ 20** — Signal counts at full strength
- **Fit 20-59** — Signal strength is downgraded (50% weight)
- **Fit < 20** — Signal doesn't count toward account heat

This prevents "noise" signals from poor-fit contacts from inflating your account score.

## Heat Score Boosters

Account heat scores also receive direct boosts based on detected patterns:

### Heat ≥ 70 (Very Hot Account)
- **Boost** — +10 to buyer score for all contacts at this company
- **Meaning** — Multiple signals from multiple high-fit leads
- **Action** — Urgent outreach; company is actively evaluating

### Heat ≥ 50 (Warm Account)
- **Boost** — +5 to buyer score for all contacts at this company
- **Meaning** — Consistent signals from diverse team members
- **Action** — Priority outreach; buying cycle likely underway

### Heat < 50 (Cool Account)
- **Boost** — None
- **Meaning** — Light or isolated signals
- **Action** — Standard outreach cadence

## Heat Trend

AutoReach tracks how account heat is evolving:

| Trend | Meaning |
|-------|---------|
| **Rising** | Heat score increasing day-over-day (3-day average) |
| **Stable** | Heat score flat (consistent signals) |
| **Cooling** | Heat score decreasing (fewer recent signals) |

Use trends to prioritize:
- **Rising** — Urgency is increasing; reach out now
- **Stable** — Sustained interest; normal outreach
- **Cooling** — Interest declining; save for later

## Complete List of Account Signal Types

AutoReach aggregates these signal types across team members:

| Signal Category | Signal Types |
|---|---|
| **Competitive Behavior** | competitor_engagement, engagement_pattern, orbit_cluster, switching |
| **Organizational Activity** | hiring, tool_mention, alternative_search |
| **Direct Intent** | asked_recommendation, complained, custom_intent |
| **Business Events** | funding, product_launch, mergers_acquisitions, geographic_expansion, ipo_filing |
| **Economic Pressure** | cost_cutting |
| **Your Content** | own_post_reply, own_post_repeat_engagement, own_post_engagement |

### Signal Type Definitions

- **Competitor Engagement** — Lead engages with competitor accounts
- **Engagement Pattern** — Consistent pattern of tool/category engagement
- **Orbit Cluster** — Detected cluster of related engagement targets
- **Hiring** — Company posting open roles (signals growth/scaling)
- **Tool Mention** — Company mentions using a specific tool
- **Switching** — Signals intent to switch providers
- **Alternative Search** — Searching for alternatives to current solution
- **Asked Recommendation** — Explicitly asked audience for recommendations
- **Funding** — Company raised funding (signals scale/acceleration)
- **Pain Match** — Expressed problem matching your ICP pain points
- **Product Launch** — Company launched new product (signals scaling)
- **Mergers & Acquisitions** — M&A activity (signals integration needs)
- **Geographic Expansion** — Company expanding to new region (signals growth)
- **Cost Cutting** — Company signaling budget constraints
- **IPO Filing** — Company filing for IPO (signals scaling, integration, expansion)
- **Complained** — Team member complained about problem your solution solves
- **Custom Intent** — Custom signals you defined in your ICP
- **Own Post Reply** — Lead replied to your posted content
- **Own Post Repeat Engagement** — Lead engaged multiple times with your content
- **Own Post Engagement** — Lead engaged once with your content

## Lead Profile Display

When you view a lead's profile, you see company heat if multiple contacts exist:

```
LEAD PROFILE
Name: John Smith | Company: Acme Corp

COMPANY HEAT: 67 (Warm) ↑ Rising
├── Other Contacts: 2
├── Recent Signals: 5 (last 7 days)
├── Signals at Company: competitor_engagement, hiring, complained
└── Buyer Score Boost: +5
```

## Using Account Heat in Strategy

### Prioritization
- **Account Heat ≥ 70** → Top tier; reach out to all relevant contacts
- **Account Heat 50-69** → Second tier; target decision-makers
- **Account Heat < 50** → Standard approach; patience is fine

### Multi-Threading
Account heat justifies multi-threading (reaching multiple contacts):
- High heat (≥ 70) = Reach 2-3 contacts simultaneously
- Medium heat (50-69) = Reach 2 contacts with slight delays
- Low heat (< 50) = Single contact first, expand later

### Cadence Adjustment
- **Rising heat** → Increase frequency (every 3-4 days)
- **Stable heat** → Normal cadence (every 5-7 days)
- **Cooling heat** → Extend spacing (every 10+ days)

{% hint style="tip" %}
Account heat is your most reliable indicator of buying group alignment. When multiple team members show signals, your probability of deal significantly increases.
{% endhint %}

## Limitations

Account heat requires:
- **Multiple contacts** from the same company (heat doesn't apply to single contacts)
- **Fit qualification** (only leads with fit ≥ 20 count)
- **Recent signals** (older signals decay over time)

If your leads are highly distributed across companies, account heat provides less value. Use it where you have density (3+ contacts per target company).
