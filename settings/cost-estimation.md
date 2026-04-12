# Pipeline Cost Estimation

AutoReach provides accurate, real-time cost estimates for your lead discovery and outreach pipeline. Costs are dynamically calculated based on your AI model configuration and the specific operations you run.

## How Cost Estimation Works

AutoReach blends the pricing of your primary and fallback models to estimate actual costs:

- **Primary Model Weight** - 85% of blend
- **Fallback Model Weight** - 15% of blend (used when primary fails)
- **Token Counting** - measured from thousands of production runs, not theoretical estimates
- **Real-Time Updates** - cost display refreshes as you change models or lead volume

{% hint style="info" %}
Cost estimates are based on average operation costs. Individual operations may vary slightly depending on content length, profile complexity, and AI provider pricing changes.
{% endhint %}

## Cost Components

Here is the typical cost breakdown for a lead flowing through AutoReach:

### Enrichment Operations

| Operation                       | Cost/Lead    | What It Does                                     |
| ------------------------------- | ------------ | ------------------------------------------------ |
| **LinkedIn Profile Enrichment** | ~$0.015      | Extracts role, company, headline, skills         |
| **Website Discovery**           | ~$0.02       | Finds company website and web presence           |
| **X/Twitter Profile Discovery** | ~$0.015      | Finds Twitter handles for LinkedIn users         |
| **Email Finding**               | $0           | Uses your Findymail API key (no AutoReach cost)  |
| **Web Enrichment**              | ~$0.08       | Extracts company data, products, funding, industry |
| **Web Search**                  | $0.01-$0.02  | Per search query (varies by result quality)      |

### Cost Drivers

**Highest Cost: Web Enrichment**
- Deep analysis of company websites and public data
- Most expensive operation in the pipeline
- Can be disabled if you do not need rich company context

**Medium Cost: Profile Discovery**
- Finding cross-platform profiles (LinkedIn to Twitter and vice versa)
- Requires search and validation

**Lower Cost: Basic Enrichment**
- LinkedIn/Twitter profile API calls
- Structured data extraction

## Pipeline Phases and Costs

Your leads flow through these phases, each with associated costs:

### Phase 1: Extraction
- **Keyword Generation** - create search queries from your ICP definition
- **Prospect Search** - find leads matching your keywords on LinkedIn/Twitter
- **Profile Extraction** - parse profile data

### Phase 2: Enrichment
- **LinkedIn Enrichment** - get full profile details
- **Email Discovery** - find work email addresses
- **Web Enrichment** - analyze company websites and public data

### Phase 3: Scoring
- **Buyer Intelligence** - AI-powered fit and intent scoring
- **Account Clustering** - group contacts by company for account-level signals

### Phase 4: Activation
- **Sequence Enrollment** - add leads to outreach campaigns
- **DM Generation** - create personalized messages (AI cost, not enrichment cost)

{% hint style="warning" %}
Phases 1-3 are one-time costs per lead. Phase 4 (DM generation) is a per-action cost that repeats throughout your sequence.
{% endhint %}

## Reducing Costs

### Disable Web Enrichment
If you do not need deep company analysis, disable web enrichment in your discovery settings. This cuts enrichment cost roughly 40-50%.

```
Cost without Web Enrichment: ~$0.07/lead
Cost with Web Enrichment:    ~$0.14/lead
```

### Use a Cheaper Fallback Model
Switch to GPT-4o mini or Claude Haiku as fallback instead of GPT-4o Turbo:

```
Expensive: Claude Opus -> GPT-4o
Cheaper:   Claude Opus -> Claude Haiku
```

### Batch Processing
Processing leads in larger batches allows AutoReach to optimize token usage and reduce per-lead costs by 5-10%.

### Filter Early
Use keyword filters and basic signals before running expensive enrichment. This reduces the number of leads entering the enrichment pipeline.

## Monitoring Your Costs

Visit **Dashboard > Cost Overview** to see:

- **This Month's Spend** - total costs year-to-date
- **Cost per Lead** - average spend from discovery through activation
- **Cost Breakdown by Phase** - enrichment vs. scoring vs. outreach
- **Projected Monthly Cost** - extrapolated based on current usage

## Example: Cost for 100 Leads

Assume 100 leads with default model configuration (Claude Opus + GPT-4o fallback):

| Phase                              | Cost       | Notes                        |
| ---------------------------------- | ---------- | ---------------------------- |
| Keyword Gen + Search               | ~$5        | Setup cost, amortized        |
| LinkedIn Enrichment                | ~$1.50     | 100 x $0.015                 |
| Web Enrichment                     | ~$8        | 100 x $0.08                  |
| Email Finding                      | $0         | Your Findymail key           |
| Buyer Scoring                      | ~$3        | ICP fit + intent scoring     |
| **Total Enrichment**               | **~$17.50**| One-time per lead            |
| DM Generation (10 messages/lead)   | ~$15       | Recurring, 1,000 total messages |
| **Total for Full Sequence**        | **~$32.50**| Per 100 leads                |

**Cost per lead: ~$0.33 for discovery + full sequence**

## Cost Estimation Accuracy

The estimates are based on:

- **10,000+ measured production runs** across all model configurations
- **Tokenization metrics** from OpenAI and Anthropic
- **Actual API pricing** from both providers

Estimates are typically accurate to within 5-10%. Factors that might increase actual costs:

- Complex leads requiring multiple search queries
- Longer company descriptions or web content
- API provider price increases
- Fallback model activation (when primary fails)

{% hint style="tip" %}
Run a pilot with 10-20 leads using your chosen model configuration. Compare estimated costs to actual costs to calibrate your projections.
{% endhint %}
