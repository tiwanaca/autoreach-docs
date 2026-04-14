# Account-Level Signal Aggregation

Account-Level Signal Aggregation combines buying signals from multiple leads at the same company into a single **heat score** — an indicator of company-wide purchase intent.

## How Heat Score Works

The heat score (0–100) reflects the overall buying intent at a company. It factors in:

- **Signal strength**: Stronger signals (like asking for recommendations) contribute more than weaker ones (like a single post like)
- **Recency**: Recent signals carry more weight than older ones
- **Team breadth**: Signals from multiple people at the same company are a stronger indicator than signals from just one person

## Company Identification

Companies are identified by LinkedIn company ID (preferred) or normalized company name. Self-employed, freelance, consultant, and similar generic values are filtered out.

Only companies with **2 or more leads** are included in heat scoring.

### Lead Filtering

- Leads with very low fit scores or in "Disqualified" state are excluded
- Leads with moderate fit scores have their signal strengths downgraded

## Signal Types

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
| Mergers & Acquisitions | M&A activity |
| Geographic Expansion | Geographic expansion |
| Cost Cutting | Budget pressure signals |
| IPO Filing | IPO filings |
| Complained | Complained about a problem you solve |
| Custom Intent | Custom intent signal from your ICP |
| Own Post Engagement | Engaged with your posts |
| Own Post Reply | Replied to your posts |
| Own Post Repeat Engagement | Engaged with your posts multiple times |

## Heat Categories

| Category | Description | Action |
|---|---|---|
| **Hot** | Strong, multi-threaded signals across the company | Urgent, coordinated outreach |
| **Warm** | Consistent signals from diverse team members | Priority outreach |
| **Cool** | Light or isolated signals | Standard cadence |

## Heat Trend

| Trend | Meaning |
|---|---|
| Rising | Score increasing day-over-day |
| Stable | Score flat |
| Cooling | Score decreasing |

## Next Steps

- **[Interaction Orbit](interaction-orbit.md)**: Dark funnel detection through engagement patterns
