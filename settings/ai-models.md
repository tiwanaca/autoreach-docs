# AI Model Configuration

Configure which AI models AutoReach uses for different tasks. Each category has a primary model and a fallback model.

## API Keys

Connect your AI providers by adding API keys in **Settings > AI & Models**:

- **AI provider API keys** — required for all AI-powered features (Anthropic and/or OpenAI)
- **Email discovery API key** — required for email finding (Findymail)

## Model Categories

AutoReach uses AI across **11 categories**. Each has independent primary and fallback model settings:

| Category | Purpose |
|---|---|
| Content Writing | DMs, posts, replies, engagement comments, warmup content |
| Buyer Scoring | Evaluating leads against your ICP |
| Keyword Generation | Creating search queries for lead discovery |
| Classification | Classifying content by topic, sentiment, and tone |
| Web Search | General web search operations |
| Web Search (Finding) | Cross-platform profile discovery |
| Web Search (Enrichment) | Company data extraction from websites |
| Web Search (Lookalike) | Finding influencers similar to target profiles |
| Web Search (Research) | Deep analysis and exploration |
| Lead Relevance | Scoring leads with detailed reasoning |
| Call Briefs | Generating meeting preparation documents |

## Per-User Overrides

Each category can be customized with a primary and fallback model selection. The system validates your choices against available models and checks that the required API key is present. Invalid or missing configurations fall back to defaults.

## How Fallbacks Work

If the primary model fails (timeout, rate limit, API error), AutoReach automatically switches to the fallback model for that operation. This provides resilience without manual intervention.

## Settings UI

The AI Configuration section in Settings shows all 11 categories with primary and fallback dropdowns. Changes take effect immediately and are validated on save.

## Dynamic Cost Impact

Your model selections directly affect pipeline costs. The cost estimation system reads your actual model configuration and calculates costs using blended pricing (85% primary + 15% fallback). See **[Cost Estimation](cost-estimation.md)** for details.

## Next Steps

- **[Pipeline Cost Estimation](cost-estimation.md)**: How model choices affect per-lead costs
