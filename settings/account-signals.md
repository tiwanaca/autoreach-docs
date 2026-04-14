# Interaction Orbit and Account Signals

AutoReach tracks two layers of buying behavior beyond what leads explicitly post about: **Interaction Orbit** (individual engagement patterns) and **Account-Level Signal Aggregation** (company-wide purchase intent).

---

## Interaction Orbit (Dark Funnel)

Interaction Orbit detects buying behavior revealed through who leads engage with on social media.

### How It Works

AutoReach tracks **who each lead replies to** on social media. When a lead replies to posts from specific accounts, those accounts become "orbit targets." The system builds a map of engagement targets per platform, tracking interaction count and first/last seen dates.

### Target Classification

Each orbit target is classified into categories like **Competitor**, **Adjacent Vendor**, **Thought Leader**, or **Peer** using your offer's competitor list and AI analysis.

### Cluster Detection

Orbit targets are grouped into **clusters** - collections of related accounts a lead engages with together within a recent time window.

Example: A prospect replies to 3 data warehouse companies and 2 BI tool accounts in a short period, forming a "data stack evaluation" cluster.

When a new cluster forms, it generates an orbit signal that feeds into buyer scoring. Competitor clusters are the strongest signal, as they indicate active evaluation of solutions in your space.

### Lead Profile Integration

When orbit data is available, the lead profile shows:

- **Orbit targets** - accounts the lead engages with
- **Clusters detected** - groups of related engagement targets
- **Cluster velocity** - engagement frequency (interactions per week)

### Privacy

Interaction Orbit only tracks **public engagement** - public replies, likes, and follows. Private DMs and conversations are never tracked. This is equivalent to what you would manually discover by viewing someone's social activity.

---

## Account-Level Signal Aggregation

Account-Level Signal Aggregation combines buying signals from multiple leads at the same company into a single **heat score** - an indicator of company-wide purchase intent.

### How Heat Score Works

The heat score reflects the overall buying intent at a company. It factors in:

- **Signal strength**: Stronger signals (like asking for recommendations) contribute more than weaker ones (like a single post like)
- **Recency**: Recent signals carry more weight than older ones
- **Team breadth**: Signals from multiple people at the same company are a stronger indicator than signals from just one person

### Company Identification

Companies are identified by LinkedIn company ID (preferred) or normalized company name. Generic values like self-employed, freelance, or consultant are filtered out.

Only companies with **2 or more leads** are included in heat scoring.

### Signal Types

The following signal types are aggregated across all leads at a company:

| Signal | Description |
|---|---|
| Competitor Engagement | Engaging with competitor accounts |
| Engagement Pattern | Category research patterns |
| Orbit Cluster | Dark funnel cluster detection |
| Hiring | Company hiring signals |
| Tool Mention | Mentions of tools or technologies |
| Switching | Signals of switching or evaluation |
| Alternative Search | Searching for alternatives |
| Asked Recommendation | Asked network for recommendations |
| Funding | Funding rounds |
| Pain Match | Matches a pain point your solution addresses |
| Product Launch | Product launches |
| Mergers and Acquisitions | M&A activity |
| Geographic Expansion | Geographic expansion |
| Cost Cutting | Budget pressure signals |
| IPO Filing | IPO filings |
| Complained | Complained about a problem you solve |
| Custom Intent | Custom intent signal from your ICP |
| Own Post Engagement | Engaged with your posts |
| Own Post Reply | Replied to your posts |
| Own Post Repeat Engagement | Engaged with your posts multiple times |

### Heat Categories

| Category | Description | Action |
|---|---|---|
| **Hot** | Strong, multi-threaded signals across the company | Urgent, coordinated outreach |
| **Warm** | Consistent signals from diverse team members | Priority outreach |
| **Cool** | Light or isolated signals | Standard cadence |

### Heat Trend

| Trend | Meaning |
|---|---|
| Rising | Score increasing day-over-day |
| Stable | Score flat |
| Cooling | Score decreasing |

## Next Steps

- **[Buyer Intelligence](../core-concepts/buyer-intelligence.md)**: How individual lead scoring works
- **[Analytics](analytics.md)**: Track overall pipeline performance
