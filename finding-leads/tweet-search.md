# X/Twitter Tweet Search

Discover prospects from intent-signaling tweets. AutoReach's AI analyzes your offer description and generates targeted search queries to find decision-makers actively discussing problems you solve.

## How It Works

### 1. AI-Powered Query Generation

When you create a search, our system:
- Analyzes your offer description, pain points, and target audience
- Generates 10-20 focused search queries using Twitter search operators
- Identifies relevant intent signals matching your offer domain

{% hint style="info" %}
Tweet search queries use Twitter's native operators: AND, OR, and exclusion terms (-) to narrow results and find highly relevant prospects.
{% endhint %}

### 2. Intent Types

Our AI identifies eight key intent categories:

| Intent Type | What We're Looking For |
|-------------|------------------------|
| **budget_pressure** | Cost reduction, financial constraints, budget cycles |
| **operational_pain** | Inefficient processes, manual work, bottlenecks |
| **security_compliance** | Security concerns, regulatory requirements, certifications |
| **hiring_scaling** | Hiring challenges, team growth, headcount decisions |
| **buying_evaluation** | Tool comparisons, vendor evaluation, RFP processes |
| **growth_signals** | Revenue growth, expansion plans, new market entry |
| **competitor_switch** | Switching from competitor platforms, tool migration |
| **vertical_specific** | Industry-specific problems, niche challenges |

### 3. Prospect Extraction

We extract prospects from two sources:

**Tweet Authors:** Decision-makers posting directly about relevant topics

**Tweet Commenters:** Professionals engaging in discussions (often purchasing stakeholders)

### 4. ICP Matching in Batches

Prospects are processed in batches of 20:
- Each tweet extracted prospect is scored against your ICP
- Buyer intent signals are identified
- Profiles are enriched with company and role data
- Only qualified matches are added to your lead database

## Default Exclusions

To prevent wasting API calls on non-commercial content, we automatically exclude:

- crypto, bitcoin, NFT, blockchain, web3
- casino, gambling, adult, NSFW content
- spam, phishing, malware signals

You can customize exclusion terms in your search settings.

## Keyword Selection Strategy

AutoReach uses **specificity scoring** to select the best keywords:

- **Multi-word phrases** score higher than single keywords
- Longer, more specific queries reduce noise and improve match quality
- Generic terms like "marketing" or "software" are deprioritized
- Your offer's unique terminology is weighted heavily

**Example:**
- ✓ "API rate limiting frustration" (specific, multi-word)
- ✗ "API" (too generic, single word)
- ✓ "AWS cost optimization" (domain-specific, multi-word)
- ✗ "cloud" (too broad, single word)

## Recurring Searches with Auto Re-Execution

Set up recurring daily searches that automatically:
- Run each day at consistent times
- Re-query the same search terms
- Extract new prospects who have posted since yesterday
- Score and enrich new matches

This ensures you capture fresh intent signals from decision-makers entering your awareness window.

## Rate Limiting

To respect Twitter's API limits and avoid detection:
- 2.5 second delay between page requests
- Gradual scaling of concurrent searches
- Automatic backoff on rate limit detection

{% hint style="warning" %}
Aggressive scraping patterns can trigger Twitter's anti-bot detection. AutoReach's rate limiting is tuned for safety and compliance. Don't manually override these delays.
{% endhint %}

## Best Practices

1. **Start broad, then narrow:** Generate initial searches with broad intent terms, then refine based on early results.

2. **Use vertical-specific language:** Include industry jargon from your target market for higher-quality matches.

3. **Run recurring searches:** Set up daily automation to catch new prospects continuously.

4. **Monitor exclusion terms:** Regularly review your exclusion list to avoid blocking legitimate prospects.

5. **Test keyword combinations:** Different keyword combinations surface different prospect segments.

## Example Workflow

**Offer:** "B2B SaaS sales automation platform"

**Generated queries might include:**
- "manual sales process too slow"
- "need sales pipeline visibility"
- "sales team needs automation"
- "CRM data quality issues"
- "struggling with sales forecasting"
- "team spends too much time on admin"

**Result:** Each query finds 20-100 relevant tweets from CTOs, VPs of Sales, and Ops Managers, precisely matching your target audience.

## Troubleshooting

**Getting too many irrelevant results?**
- Review your offer description for clarity
- Add more exclusion terms for common false positives
- Use more specific, niche-focused search terms

**Not finding enough prospects?**
- Broaden your intent categories
- Include common synonym variations
- Check if your target audience actually discusses this on Twitter

**Seeing duplicate prospects across searches?**
- This is normal. ICP matching deduplicates before adding to your database
- The same prospect may appear in multiple relevant searches
