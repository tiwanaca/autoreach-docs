# AI Model Configuration

Configure which AI providers and models AutoReach uses for different tasks. You can customize each category independently or stick with the recommended defaults.

## Accessing AI Model Settings

Navigate to **Settings > AI & Models** to configure your AI provider setup.

## API Keys

Connect your AI provider accounts by adding API keys:

- **AI provider API keys** - required to run any AI-powered features
- **Email discovery API key** - used for email discovery; if not provided, email finding is skipped

{% hint style="info" %}
You only need to add keys for the providers you plan to use. AutoReach supports multiple AI providers, and you can mix providers across categories.
{% endhint %}

## Model Configuration Categories

AutoReach uses AI for 9 distinct tasks. Each category has a **Primary Model** (used first) and a **Fallback Model** (used if the primary fails or is unavailable).

AutoReach supports multiple AI providers and models, with a recommended default configuration that balances quality and reliability.

### Content Writing
Generates direct messages, posts, replies, and engagement comments.

### Keyword Generation
Creates search queries to find your target buyers on X and LinkedIn.

### Classification
Classifies content by topic, sentiment, and tone to filter leads.

### Profile Finding
Discovers cross-platform profiles (finds X handles for LinkedIn users, etc.).

### Web Enrichment
Extracts company data, products, and funding info from websites.

### Lookalike Search
Finds influencers and thought leaders similar to your target profiles.

### Research & Copilot
Performs deep analysis for custom research and AI-powered exploration.

### Lead Relevance
Scores leads against your ICP with detailed reasoning.

### Call Briefs
Generates meeting preparation documents with background research.

## How Fallback Models Work

If your primary model fails (timeout, rate limit, API error), AutoReach automatically switches to the fallback model for that operation. Fallback activation is logged in your activity feed so you can see when it is happening.

## Dynamic Cost Estimation

AutoReach estimates your pipeline costs in real time based on your model choices. The cost display:

- Reflects your selected primary and fallback models
- Reflects measured token counts from production runs
- Updates instantly when you change models

{% hint style="tip" %}
The default model configuration works well for most users. You can customize individual categories if you have specific cost or quality preferences for particular tasks.
{% endhint %}

## Next Steps

- **[Pipeline Cost Estimation](cost-estimation.md)**: See how your model choices affect per-lead costs
- **[Creating Your First Offer](../getting-started/create-offer.md)**: Set up an offer to start using your configured models
