# AI Model Configuration

Configure which AI providers and models AutoReach uses for different tasks. You can customize each category independently or stick with the battle-tested defaults.

## Accessing AI Model Settings

Navigate to **Settings > AI & Models** to configure your AI provider setup.

## API Keys

Connect your AI provider accounts by adding API keys:

- **OpenAI API Key** - required for GPT-4o and GPT-4 Turbo fallbacks
- **Anthropic API Key** - required for Claude Opus (the recommended primary model)
- **Findymail API Key** - used for email discovery; if not provided, email finding is skipped

{% hint style="info" %}
You only need to add keys for providers you plan to use. If you are using Claude Opus as your primary model, you only need the Anthropic key.
{% endhint %}

## Model Configuration Categories

AutoReach uses AI for 9 distinct tasks. Each category has a **Primary Model** (used first) and a **Fallback Model** (used if the primary fails).

### Content Writing
Generates direct messages, posts, replies, and engagement comments.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Keyword Generation
Creates search queries to find your target buyers on X/Twitter and LinkedIn.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Classification
Classifies content by topic, sentiment, and tone to filter leads.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Profile Finding
Discovers cross-platform profiles (finds Twitter handles for LinkedIn users, etc.).
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Web Enrichment
Extracts company data, products, and funding info from websites.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Lookalike Search
Finds influencers and thought leaders similar to your target profiles.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Research & Copilot
Performs deep analysis for custom research and AI-powered exploration.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Lead Relevance
Scores leads against your ICP with detailed reasoning.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

### Call Briefs
Generates meeting preparation documents with background research.
- **Default Primary:** Claude Opus
- **Default Fallback:** GPT-4o

## How Fallback Models Work

If your primary model fails (timeout, rate limit, API error), AutoReach automatically switches to the fallback model for that operation. Fallback activation is logged in your activity feed so you can see when it is happening.

## Dynamic Cost Estimation

AutoReach calculates your pipeline costs in real-time based on your model choices. The cost display:

- Blends primary model (85%) and fallback model (15%) pricing
- Reflects measured token counts from production runs
- Updates instantly when you change models

{% hint style="tip" %}
The default model configuration works well for most users. Only customize if you have specific needs (e.g., to reduce costs by using a cheaper fallback) or prefer a different provider.
{% endhint %}

## Choosing a Model Configuration

**Recommended for most users:**
- **Primary:** Claude Opus (best quality, highest cost)
- **Fallback:** GPT-4o (excellent quality, lower cost)

**Cost-optimized:**
- **Primary:** Claude Sonnet (faster, cheaper than Opus)
- **Fallback:** GPT-4o mini (lowest cost)

**Budget-friendly:**
- **Primary:** Claude Haiku (lowest cost)
- **Fallback:** GPT-4o mini (backup for edge cases)

Test your configuration with a small pilot sequence before rolling out to your full lead list.

## Next Steps

- **[Pipeline Cost Estimation](cost-estimation.md)**: See how your model choices affect per-lead costs
- **[Creating Your First Offer](../getting-started/create-offer.md)**: Set up an offer to start using your configured models
