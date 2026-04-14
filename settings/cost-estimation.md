# Pipeline Cost Estimation

AutoReach provides real-time cost estimates for your lead discovery and enrichment pipeline. Costs are dynamically calculated based on your AI model configuration.

## Dynamic Pricing

Cost estimates reflect your **actual model selections**. When you change models in Settings, the estimate updates immediately.

### Blended Pricing

Each category's cost is blended between your primary and fallback models based on observed fallback rates. This means your cost estimate reflects real-world usage rather than assuming the primary model handles every request.

## Cost Components

The main cost drivers per lead:

### Extraction (Lead Discovery)

- Keyword generation
- Sentiment analysis

### Enrichment

- **LinkedIn profile finding**-  web search to find LinkedIn profiles for X-sourced leads
- **Website finding**-  web search for company websites
- **Web enrichment**-  deep company analysis from websites (most expensive per-lead operation)
- **Email finding**-  third-party API cost (your own Findymail key, no AutoReach markup)

### Deep AI Analysis

Scoring costs depend on the amount of profile data available for each lead. Leads with more enrichment data (posts, company info, web research) cost more to score than leads with minimal profile information.

## Example Cost Scenarios

The following examples give a rough sense of costs for common workflows. Actual costs depend on your model selections, lead data completeness, and enrichment settings.

**Finding 100 leads from a tweet search (default models):**
- Extraction (keyword generation + sentiment analysis): ~$0.01-0.03
- Enrichment (LinkedIn profile finding, website finding, web enrichment): ~$0.80-1.50
- Buyer scoring: ~$0.02-0.05
- **Estimated total: ~$0.85-1.60 for 100 leads**

Web enrichment (deep company analysis from websites) is by far the most expensive single operation. If you disable it, enrichment costs drop significantly.

**Scoring 500 existing leads (rescore only, no enrichment):**
- Using the default nano model for scoring: ~$0.05-0.15
- Using a premium model for scoring: ~$0.50-2.00

**LinkedIn content search with 50 posts, 3 intent categories:**
- Similar extraction costs to tweet search
- No LinkedIn profile finding needed (leads already have LinkedIn URLs)
- **Estimated total: ~$0.15-0.60 for the discovered leads**

## How Model Selection Affects Costs

Your choice of AI models has a dramatic impact on per-lead costs. Nano-class models (designed for classification and scoring) cost roughly 10-30x less per token than premium models (designed for content writing).

- **Nano models** (best for scoring, classification, keywords): Lowest cost, suitable for high-volume operations where speed matters more than nuance
- **Mid-tier models** (Sonnet-class): Good balance of quality and cost, often used as fallback models
- **Premium models** (Opus-class and equivalent): Highest quality output, best for content writing where tone and personalization matter, but significantly more expensive per token

For budget-conscious users, the biggest savings come from keeping scoring and classification on nano models and reserving premium models only for content writing (DMs, posts, replies).

## Checking Your AI Spending

You can review your actual AI usage and spending in the **AI Usage panel on the Dashboard**. This shows token consumption and costs broken down by category, so you can see exactly where your budget is going and identify opportunities to optimize.

## Reducing Costs

1. **Disable web enrichment**-  the most expensive per-lead operation; skip it for lead sources where you already have company context
2. **Use lower-cost models for scoring and classification**-  these high-volume categories process every lead, so even small per-token savings add up quickly
3. **Filter early**-  apply keyword filters and exclusions before enrichment to reduce the number of leads entering the pipeline
4. **Choose efficient fallback models**-  an expensive fallback model increases your effective rate
5. **Run smaller batches first**-  test with 20-50 leads before running large searches to validate your keywords and filters
6. **Review the cost estimate before running**-  the estimate updates in real time as you adjust search parameters, so use it to experiment before committing

## Next Steps

- **[AI Model Configuration](ai-models.md)**: Customize model selections to optimize cost
