# Pipeline Cost Estimation

AutoReach provides real-time cost estimates for your lead discovery and outreach pipeline. Costs are dynamically calculated based on your AI model configuration and the specific operations you run.

## How Cost Estimation Works

Cost estimates reflect the actual AI models you have configured in your account settings. When you change your model selections, the estimate updates immediately to reflect the new pricing.

- **Model-Driven Pricing** - costs are based on your chosen primary and fallback models
- **Real-Time Updates** - the cost display refreshes as you change models or lead volume

{% hint style="info" %}
Cost estimates are based on average operation costs. Individual operations may vary slightly depending on content length, profile complexity, and AI provider pricing changes.
{% endhint %}

## Cost Components

AutoReach runs several operations to discover, enrich, and score each lead. The main cost drivers are:

**Highest Cost: Web Enrichment**
- Deep analysis of company websites and public data
- The most resource-intensive operation in the pipeline
- Can be disabled if you do not need rich company context

**Medium Cost: Profile Discovery**
- Finding cross-platform profiles (LinkedIn to X and vice versa)
- Requires search and validation steps

**Lower Cost: Basic Enrichment**
- LinkedIn and X profile data extraction
- Structured data processing

**Email Finding**
- Uses a third-party email discovery service via your own API key
- No additional AutoReach cost

## Reducing Costs

### Disable Web Enrichment

If you do not need deep company analysis, disable web enrichment in your discovery settings. This is the most effective way to reduce per-lead enrichment costs.

### Use a Lower-Cost Fallback Model

Choosing a more economical fallback model in your AI configuration can meaningfully reduce overall costs. Visit **Settings > AI Configuration** to review your model selections.

### Filter Early

Apply keyword filters and basic signals before running enrichment. Reducing the number of leads that enter the enrichment pipeline is one of the best ways to control spend.

### Batch Processing

Processing leads in larger batches allows AutoReach to optimize token usage and reduce per-lead costs.

## Monitoring Your Costs

Visit **Dashboard > Cost Overview** to see:

- **This Month's Spend** - total costs for the current billing period
- **Cost per Lead** - average spend from discovery through activation
- **Cost Breakdown by Phase** - enrichment vs. scoring vs. outreach
- **Projected Monthly Cost** - extrapolated based on current usage

{% hint style="tip" %}
Run a pilot with 10-20 leads using your chosen model configuration. Compare estimated costs to actual costs to calibrate your projections before scaling up.
{% endhint %}

## Cost Estimation Accuracy

Estimates are calculated using real token-count data and current API pricing from each provider. Factors that may cause actual costs to differ from estimates:

- Complex leads requiring multiple search queries
- Longer company descriptions or web content
- API provider price increases
- Fallback model activation when the primary model is unavailable

## Next Steps

- **[AI Model Configuration](ai-models.md)**: Customize your model choices to optimize cost and quality
- **[Finding Leads Overview](../finding-leads/overview.md)**: Explore discovery methods and their associated costs
