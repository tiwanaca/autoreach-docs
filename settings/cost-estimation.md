# Pipeline Cost Estimation

AutoReach provides real-time cost estimates for your lead discovery and enrichment pipeline. Costs are dynamically calculated based on your AI model configuration.

## Dynamic Pricing

Cost estimates reflect your **actual model selections**. When you change models in Settings, the estimate updates immediately.

### Blended Pricing

Each category's cost is blended between primary and fallback models:

- **85% primary model** pricing + **15% fallback model** pricing

This reflects the observed fallback activation rate in production. In plain terms, about 85% of the time your primary model handles the request successfully, and about 15% of the time the system falls back to the secondary model (due to rate limits, timeouts, or temporary API issues). Your cost estimate reflects this real-world mix rather than assuming the primary model handles everything.

The system reads your resolved model configuration and computes blended input/output token costs per category.

## Cost Components

The main cost drivers per lead:

### Extraction (Lead Discovery)

- Keyword generation tokens (classification category pricing)
- Sentiment analysis tokens

### Enrichment

- **LinkedIn profile finding** — web search to find LinkedIn profiles for X-sourced leads (applies to ~90% of X leads, 0% of LinkedIn leads, ~50% of lookalike leads)
- **Website finding** — web search for company websites
- **Web enrichment** — deep company analysis from websites (most expensive per-lead operation)
- **Email finding** — third-party API cost (your own Findymail key, no AutoReach markup)

### Buyer Scoring

- System prompt (~30 tokens) + template (~650 tokens) + profile data (~120 tokens)
- Up to 10 posts per lead
- JSON schema (~600 tokens) + output (~750 tokens)
- Optional company posts section (~4,100 tokens, 75% probability)
- Optional web enrichment context (~400 tokens, 30% probability)

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
- **Premium models** (Opus-class, GPT-5.4): Highest quality output, best for content writing where tone and personalization matter, but significantly more expensive per token

For budget-conscious users, the biggest savings come from keeping scoring and classification on nano models and reserving premium models only for content writing (DMs, posts, replies).

## Checking Your AI Spending

You can review your actual AI usage and spending in **Analytics > AI Usage**. This shows token consumption and costs broken down by category, so you can see exactly where your budget is going and identify opportunities to optimize.

## Reducing Costs

1. **Disable web enrichment** — the most expensive per-lead operation; skip it for lead sources where you already have company context
2. **Use lower-cost models for scoring and classification** — these high-volume categories process every lead, so even small per-token savings add up quickly
3. **Filter early** — apply keyword filters and exclusions before enrichment to reduce the number of leads entering the pipeline
4. **Choose efficient fallback models** — since fallbacks contribute 15% of blended cost, an expensive fallback model increases your effective rate
5. **Run smaller batches first** — test with 20-50 leads before running large searches to validate your keywords and filters
6. **Review the cost estimate before running** — the estimate updates in real time as you adjust search parameters, so use it to experiment before committing

## Next Steps

- **[AI Model Configuration](ai-models.md)**: Customize model selections to optimize cost
