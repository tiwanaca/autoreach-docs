# Account-Level Signal Aggregation

Account-Level Signal Aggregation combines buying signals from multiple leads at the same company into a single **heat score** — an indicator of company-wide purchase intent.

## How Heat Score Is Computed

The heat score (0–100) combines three factors:

- **Signal strength**: Each signal contributes points based on its strength (high, medium, or low)
- **Recency bonus**: Recent signals (last 7 days) receive additional weight
- **Diversity multiplier**: More leads at the same company showing signals amplifies the score — wider signal distribution across a team is a stronger indicator than concentrated signals from one person

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
