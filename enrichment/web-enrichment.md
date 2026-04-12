# Web Enrichment

Web enrichment searches the public web to gather additional company context, contact information, and professional intelligence about your leads.

## What Web Enrichment Gathers

### Company Information

Enrichment searches for and extracts company details:

- **Company Size** - Number of employees
- **Industry** - Primary industry classification
- **Funding Stage** - Seed, Series A, B, C, etc.
- **Funding Amount** - Total raised to date
- **Investors** - Known VCs and angel investors
- **Technologies** - Tech stack and tools used
- **Founded Year** - When the company was established
- **Headquarters Location** - Primary office location
- **Official Website** - Company domain

This context is valuable for understanding the lead's company scale and maturity.

### Social Profiles & Web Presence

AutoReach searches for professional social profiles:

- **Twitter/X Account** - Company X handle
- **GitHub Account** - Engineering team code repository
- **YouTube Channel** - Video content and company branding
- **Medium Publication** - Company blog
- **Substack Newsletter** - Content newsletter
- **Personal Websites** - Portfolios, consulting sites, or blogs
- **Company LinkedIn Page** - Official company presence

### Contact Information

Additional ways to reach the lead:

- **Phone Number** - Verified phone contact
- **Additional Email Addresses** - Work or personal emails beyond primary
- **Calendly Link** - Scheduling page for easy meeting booking
- **Newsletter Subscription** - Email list signup pages

### News & Press

Recent news about the lead or their company:

- **News Title** - Headline of the article
- **Publication Source** - Where it was published (TechCrunch, Forbes, company blog)
- **URL** - Link to the full article
- **Publication Date** - When the news was published
- **Summary** - Brief description of the news content

News signals are powerful for outreach timing. Someone who just got funded or hired is especially receptive.

### Insights & Achievements

Professional achievements and speaking/publishing activity:

- **Speaking Engagements** - Conferences and events they've spoken at
- **Publications** - Articles, whitepapers, or research they've authored
- **Podcast Appearances** - Interviews and podcast guest slots
- **Awards** - Professional recognition and accolades
- **Patents** - Issued patents in their field

These signals indicate expertise and influence in their space.

## Confidence Scoring

All web-enriched data includes a **confidence score** (0.0 to 1.0):

- **0.9-1.0** - High confidence, multiple sources confirm
- **0.7-0.9** - Medium-high confidence, primary source found
- **0.5-0.7** - Medium confidence, inferred or single source
- **Below 0.5** - Low confidence, data may be inaccurate

AutoReach uses confidence scores to filter and prioritize data. Only high-confidence data is used for scoring and outreach personalization.

## Cost & Requirements

### Pricing

Web enrichment costs approximately **$0.08 per lead** from AutoReach's credit pool.

{% hint style="info" %}
**Credit Usage:** Web enrichment costs are deducted from your AutoReach subscription's monthly credit allowance. See your billing dashboard for credit balance.
{% endhint %}

### Lead Requirements

Web enrichment requires at least one of:

- **Complete LinkedIn Profile** - URL-accessible LinkedIn profile page
- **Meaningful Bio** - A bio or description longer than 20 characters

Leads without either will skip web enrichment to save credits.

### What Triggers Web Enrichment

Web enrichment automatically runs on newly added leads if:
- Your workspace has available credits
- The lead meets the requirements above
- Web enrichment is enabled in your workspace settings

You can also manually trigger web enrichment from a lead's profile card.

## Using Web Enrichment in Outreach

Web-enriched data powers more specific outreach:

- **Recent News Reference** - "Congrats on the Series B funding!"
- **Speaking Expertise** - "I loved your keynote at SaaStr..."
- **Technology Alignment** - "I see you're building on AWS and React..."
- **Investor Context** - "With Sequoia backing you, you're obviously scaling fast..."

More data leads to stronger personalization and higher response rates.

{% hint style="warning" %}
**API Rate Limits:** Web enrichment uses external APIs to search and scrape company data. If you have very large workspaces (1000+ leads), enrichment may be slower due to API rate limits. AutoReach queues requests fairly across all customers.
{% endhint %}

## Enabling & Disabling Web Enrichment

Web enrichment is enabled by default. To disable it (to preserve credits):

1. Go to **Settings > Enrichment**
2. Toggle off **Enable Web Enrichment**
3. Save

You can re-enable it anytime. Leads already enriched won't be re-processed unless manually refreshed.

## Next Steps

- **[Email Finding](email-finding.md)**: Discover work email addresses for your enriched leads
- **[Website Finding](website-finding.md)**: Find professional and company websites for deeper personalization
