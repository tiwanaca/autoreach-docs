# Interaction Orbit (Dark Funnel)

Interaction Orbit detects buying behavior that leads don't explicitly post about — revealed through who they engage with.

## How It Works

AutoReach tracks **who each lead replies to** on social media. When a lead replies to posts from specific accounts, those accounts become "orbit targets." The system builds a map of engagement targets per platform and username, tracking interaction count and first/last seen dates.

Orbit snapshots are merged over time — the highest interaction count wins, and the earliest first-seen date is preserved.

## Target Classification

Each orbit target is classified into one of 5 categories:

| Classification | Description |
|---|---|
| Competitor | Directly selling in your space |
| Adjacent Vendor | Related tools or services |
| Thought Leader | Industry experts and analysts |
| Peer | Same-level professionals |
| Unknown | Unclassified |

Classification uses two passes:
1. **String matching** — zero-cost check against your offer's competitor list
2. **AI classification** — lightweight AI model classifies based on bio and headline enrichment data

## Cluster Detection

Orbit targets are grouped into **clusters** — collections of related accounts a lead engages with together within a recent time window.

Example: A prospect replies to 3 data warehouse companies and 2 BI tool accounts in a short period, forming a "data stack evaluation" cluster.

### New Cluster Detection

When a cluster forms for the first time, it generates an orbit cluster signal that feeds into the buyer scoring system. Competitor clusters produce stronger signals than other cluster types, directly boosting the lead's intent score.

## How Orbit Data Feeds Scoring

Orbit signals flow into two systems:

1. **Account Signal Service** — orbit clusters contribute to the company-level heat score. Leads interacting with multiple accounts in your orbit score higher.
2. **Buyer Intelligence** — the scoring prompt includes orbit data, highlighting active competitor evaluations and high-velocity engagement patterns

## Lead Profile Integration

When orbit data is available, the lead profile shows:

- **Orbit targets** — accounts the lead engages with
- **Clusters detected** — groups of related engagement targets
- **Cluster velocity** — engagement frequency trend (Rising, Stable, Cooling)

## Privacy

Interaction Orbit only tracks **public engagement** — public replies, likes, and follows. Private DMs and conversations are never tracked. This is equivalent to what you'd manually discover by viewing someone's social activity.

## Next Steps

- **[Account Signals](account-signals.md)**: How orbit data feeds company-level heat scoring
