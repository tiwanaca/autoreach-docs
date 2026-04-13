# Pipeline Cost Estimation

AutoReach provides real-time cost estimates for your lead discovery and enrichment pipeline. Costs are dynamically calculated based on your AI model configuration.

## Dynamic Pricing

Cost estimates reflect your **actual model selections**. When you change models in Settings, the estimate updates immediately.

### Blended Pricing

Each category's cost is blended between primary and fallback models:

- **85% primary model** pricing + **15% fallback model** pricing

This reflects the observed fallback activation rate in production.

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

## Reducing Costs

1. **Disable web enrichment** — the most expensive per-lead operation
2. **Use lower-cost models** — especially for high-volume categories like classification and keyword generation
3. **Filter early** — apply keyword filters before enrichment to reduce the number of leads entering the pipeline
4. **Choose efficient fallback models** — since fallbacks contribute 15% of blended cost

## Next Steps

- **[AI Model Configuration](ai-models.md)**: Customize model selections to optimize cost
