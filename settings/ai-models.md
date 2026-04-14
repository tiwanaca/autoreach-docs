# AI Model Configuration

Configure which AI models AutoReach uses for different tasks. Each category has a primary model and a fallback model.

## API Keys

Connect your AI providers by adding API keys in **Settings > AI & Models**:

- **AI provider API keys**-  required for all AI-powered features (Anthropic and/or OpenAI)
- **Email discovery API key**-  required for email finding (Findymail)

## Model Categories

AutoReach uses AI across multiple categories. Each has independent primary and fallback model settings:

| Category | Purpose |
|---|---|
| Content Writing | DMs, replies, first messages, templates, warmup, copilot |
| Buyer Scoring | Evaluating leads against your ICP |
| Keyword Generation | Creating search queries for lead discovery |
| Classification | Classifying content by topic, sentiment, and tone |
| Profile Finding | Email, LinkedIn, X profile, and website discovery |
| Web Enrichment | Company data extraction from websites |
| Lookalike Search | Finding influencers similar to target profiles |
| Research & Copilot | Follow-up research, copilot web search, topic research |
| Lead Relevance | Scoring leads with detailed reasoning |
| Call Briefs | Generating meeting preparation documents |

## Per-User Overrides

Each category can be customized with a primary and fallback model selection. The system validates your choices against available models and checks that the required API key is present. Invalid or missing configurations fall back to defaults.

## How Fallbacks Work

If the primary model fails (timeout, rate limit, API error), AutoReach automatically switches to the fallback model for that operation. This provides resilience without manual intervention.

You do not need to do anything when a fallback occurs-  the system handles it automatically and the output is still delivered. The only visible effect is that your cost reflects the blended rate of both models rather than just the primary.

If both the primary and fallback models fail (rare, but possible during provider outages), the operation is retried later.

## When to Change Model Settings

**Good reasons to change models:**
- You want to reduce costs by using a cheaper model for high-volume categories like scoring or classification
- You want higher quality DMs or posts and are willing to pay more for a premium content writing model
- You have API keys for only one provider and need all categories to use that provider's models

**When to leave defaults alone:**
- If you are just getting started, the defaults are a solid starting point
- If your current output quality and costs are acceptable, there is no need to experiment
- Web search categories are constrained to specific providers and generally should not be changed

## Cost Implications

Model pricing varies significantly. As a rough guide:

- **Nano-class models** are the cheapest option - ideal for scoring, classification, and keyword generation where volume is high
- **Mid-tier models** (Sonnet-class) offer a good balance and work well as fallback models
- **Premium models** (Opus-class) deliver the highest quality but cost considerably more per token - reserve these for content writing if budget is a concern

Since scoring and classification run on every lead while content writing only runs when sending messages, moving scoring to a cheaper model produces larger savings than optimizing content writing.

## Recommended Configurations

**Budget-conscious setup:** Use nano models for scoring, classification, and keyword generation. Use a mid-tier model for content writing. This minimizes per-lead costs while keeping message quality reasonable.

**Quality-focused setup:** Use a premium model for content writing (DMs, posts, replies). Keep scoring and classification on nano or mid-tier models - these tasks do not benefit as much from premium models. This gives you the best message quality without overspending on scoring.

## Settings UI

The AI Configuration section in Settings shows all categories with primary and fallback dropdowns. Changes take effect immediately and are validated on save.

## Dynamic Cost Impact

Your model selections directly affect pipeline costs. The cost estimation system reads your actual model configuration and calculates blended pricing based on observed fallback rates. See **[Cost Estimation](cost-estimation.md)** for details.

## Next Steps

- **[Pipeline Cost Estimation](cost-estimation.md)**: How model choices affect per-lead costs
