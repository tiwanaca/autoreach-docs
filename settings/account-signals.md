# Account-Level Signal Aggregation

Account-Level Signal Aggregation combines buying signals from multiple leads at the same company to create an account heat score: a single indicator of company-wide purchase intent.

## How It Works

When AutoReach detects multiple leads from the same company:

1. Collects all buying signals from each lead
2. Weighs signals by strength and recency
3. Applies a boost when more contacts from the same company are showing signals
4. Produces an account heat score (0-100)

This surfaces when an entire company is actively evaluating solutions, even if individual lead signals are light.

Recent signals are weighted more heavily than older ones, so accounts with fresh activity score higher than those with only historical signals.

When more contacts from the same company show signals, the account score increases beyond what any single lead would contribute on their own. Wider signal distribution across a team is a stronger indicator than concentrated signals from one person.

Signals from better-fit leads contribute more to the account score. Poor-fit contacts have less influence, which keeps account heat focused on the accounts most relevant to your ICP.

## Account Heat Categories

Account heat is categorized into three levels:

**Hot accounts** show strong, multi-threaded signals across the company. Multiple high-fit leads are active simultaneously, suggesting the buying group is engaged. These accounts warrant urgent, coordinated outreach.

**Warm accounts** show consistent signals from diverse team members, suggesting a buying cycle is likely underway. Treat these as a priority.

**Cool accounts** show light or isolated signals. A standard outreach cadence applies.

Individual lead scores also reflect the company's overall heat level, so leads at hot accounts are surfaced more prominently in your pipeline.

## Heat Trend

AutoReach tracks how account heat is evolving over time:

| Trend       | Meaning                                            |
| ----------- | -------------------------------------------------- |
| **Rising**  | Heat score increasing day-over-day                 |
| **Stable**  | Heat score flat (consistent signals)               |
| **Cooling** | Heat score decreasing (fewer recent signals)       |

Use trends to prioritize:
- **Rising** - urgency is increasing; reach out now
- **Stable** - sustained interest; normal outreach
- **Cooling** - interest declining; deprioritize for now

## Signal Types Aggregated

AutoReach aggregates the following categories of signals across all contacts at a company:

**Competitive behavior** - engagement with competitor accounts, patterns of category research, or signals that a contact is evaluating alternatives or considering a switch.

**Organizational activity** - hiring signals, mentions of tools or technologies, and searches for alternative solutions.

**Direct intent** - contacts who explicitly asked their network for recommendations, complained about a problem your solution addresses, or matched a custom intent signal you defined in your ICP.

**Business events** - funding rounds, product launches, mergers and acquisitions, geographic expansion, or IPO filings. These events often signal growth, scaling needs, or new integration requirements.

**Economic pressure** - signals that a company is operating under budget constraints, which can indicate urgency around cost-effective solutions.

**Your content** - contacts who engaged with your posts, replied to your content, or engaged multiple times across your activity.

## Using Account Heat in Strategy

### Prioritization

Account heat helps you rank companies, not just individual leads. Hot accounts should receive attention across the buying group, not just from a single contact. Warm accounts are worth targeting decision-makers specifically. Cool accounts are appropriate for standard, lower-frequency outreach.

### Multi-Threading

High account heat is a reliable indicator that reaching multiple contacts at the same company is warranted. When signals are distributed across several team members, engaging more than one person simultaneously increases your chances of reaching someone with active authority or urgency. Start broader at hotter accounts and narrower at cooler ones.

### Cadence Adjustment

- **Rising heat** - increase frequency
- **Stable heat** - maintain normal cadence
- **Cooling heat** - extend spacing or deprioritize

{% hint style="tip" %}
Account heat is your most reliable indicator of buying group alignment. When multiple team members show signals, your probability of closing a deal increases significantly.
{% endhint %}

## Limitations

Account heat requires:
- **Multiple contacts** from the same company (heat does not apply to single contacts)
- **Qualified leads** (only leads with sufficient fit contribute to the score)
- **Recent signals** (older signals decay over time)

If your leads are highly distributed across companies, account heat provides less value. It is most useful where you have density across target accounts.

## Next Steps

- **[Interaction Orbit](interaction-orbit.md)**: Detect dark funnel buying behavior through engagement patterns
- **[Buyer Intelligence & Scoring](../core-concepts/buyer-scoring.md)**: Understand how account heat influences individual lead scores
