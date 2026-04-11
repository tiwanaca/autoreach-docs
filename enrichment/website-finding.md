# Website Finding

Website finding uses AI-powered web search to discover professional and company websites. This enrichment adds crucial context to lead profiles and enables more personalized outreach.

## What Website Finding Does

Website finding automatically searches for and discovers:

- **Company Websites** - Official .com or corporate domains
- **Personal Websites** - Consulting sites, portfolios, or landing pages
- **Professional Profiles** - Personal branding sites or bio pages
- **Product/Project Websites** - Startup sites, side projects, or open-source portfolios

These discovered websites are stored on the lead profile for reference and used by AI message generation for deeper personalization.

## How It Works

### OpenAI Web Search

Website finding leverages OpenAI's web search capabilities to find websites:

1. **Query Generation** - AutoReach generates targeted web searches using the lead's name, company, and available profile data
2. **Web Search** - Sends queries to OpenAI's search index
3. **Result Parsing** - Analyzes search results to identify legitimate professional websites
4. **Link Extraction** - Extracts and validates discovered URLs
5. **Storage** - Saves discovered websites to the lead profile

The process is intelligent—it filters out irrelevant results and focuses on discovering real professional presence.

## Requirements

Website finding requires at least one of:

- **Complete LinkedIn Profile** - A working LinkedIn profile URL
- **Meaningful Bio** - A bio or description longer than 20 characters

Leads without either will skip website finding to save credits and processing time.

{% hint style="info" %}
**Why These Requirements?** These data points provide context for web search. A bio alone might be too generic, and a name alone could match thousands of people. LinkedIn profile + minimal bio = sufficient context for targeted search.
{% endhint %}

## Cost

Website finding costs approximately **$0.02 per lead**.

{% hint style="info" %}
**Credit Usage:** Website discovery costs are deducted from your AutoReach subscription's monthly credit allowance.
{% endhint %}

This makes it one of the most cost-efficient enrichment tools relative to the value it adds.

## What Happens With Discovered Websites

### Storage

Found websites are stored on the lead profile under the **Websites** section. You can view them in:
- The lead profile card
- The lead details page
- Export files (if you export lead data)

### AI Usage

AutoReach AI uses discovered websites to:

- **Content Analysis** - Reads website content to understand the lead's focus and expertise
- **Message Personalization** - References the lead's personal brand in outreach
- **Context Generation** - Incorporates website insights into DM generation
- **Portfolio Understanding** - Gathers context if the website showcases past work

For example, if AutoReach discovers a personal website showing software engineering expertise with specific technologies, the AI might personalize an outreach message:

> "I noticed you've built some impressive projects using Go and Kubernetes. We're helping engineering teams scale their infrastructure like you have..."

### Competitor Insights

If the discovered website reveals the lead is at a competing company or building a competitive product, AutoReach's buyer scoring algorithm can adjust lead quality accordingly.

## Enabling & Disabling Website Finding

Website finding is enabled by default. To disable it:

1. Go to **Settings > Enrichment**
2. Toggle off **Enable Website Finding**
3. Save

This prevents new leads from having websites discovered and preserves credits if you don't need this data.

## When Website Finding Runs

Website finding automatically triggers when:

- A new lead is added to AutoReach
- The lead meets requirements (LinkedIn profile OR meaningful bio)
- Your workspace has available credits
- Website finding is enabled

It does NOT automatically re-run on already-enriched leads. You can manually refresh website discovery from the lead profile.

## Best Practices

### Combine With Other Enrichment

Website discovery is most powerful when combined with:

- **LinkedIn Enrichment** - Provides professional context and credibility
- **X/Twitter Enrichment** - Shows real-time interests and activity
- **Web Enrichment** - Gathers company-level context

Together, these create a 360-degree view of your lead.

### Use for Personalization

{% hint style="success" %}
**Pro Tip:** Enable AI-powered DM generation in your sequences. The AI will automatically reference discovered websites to create more personalized, relevant messages. Higher relevance = higher response rates.
{% endhint %}

### Review High-Value Leads

For your highest-priority leads, manually review discovered websites. Sometimes the AI will find nuances you can leverage directly in subject lines or opening lines of your outreach.

## Troubleshooting

### No Websites Found

This is normal. Not every lead has discoverable web presence:

- Some professionals don't maintain personal websites
- Company websites might not be indexed well
- The lead might be newer to the role

This doesn't affect outreach quality—you can still reference LinkedIn and X data.

### Irrelevant Websites Found

Occasionally, website finding returns false positives (websites for different people with the same name):

1. Review the discovered websites in the lead profile
2. Delete any that don't match (just click the X icon)
3. The AI will use only the relevant websites for message generation

### Website Not Updating

Website discovery runs once per lead by default. To refresh:

1. Open the lead profile
2. Click **Refresh Enrichment** or similar button
3. Website finding will re-run

You might want to refresh if:
- The lead recently launched a new website
- You suspect the discovered URL is outdated
- You want to confirm current professional presence
