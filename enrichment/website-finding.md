# Website Finding

Website finding automatically discovers professional and company websites for your leads during enrichment. These websites provide valuable context that powers more personalized outreach.

## What Website Finding Does

As part of the enrichment process, AutoReach searches for and identifies websites associated with each lead. This runs automatically when new leads are added to your workspace, requiring no manual effort.

Discovered websites are stored on the lead profile and made available to AI message generation for deeper personalization.

## Types of Websites Discovered

Website finding looks for several categories of web presence:

- **Company Websites** - Official corporate domains and marketing sites
- **Personal Websites** - Consulting sites, bio pages, or personal branding sites
- **Portfolio Sites** - Showcases of past work, case studies, or client results
- **Project Websites** - Startup landing pages, side projects, or open-source work

## How Discovered Websites Are Used

### AI Personalization

AutoReach AI uses discovered websites to craft more relevant outreach. It analyzes website content to understand a lead's focus, expertise, and professional interests, then incorporates those insights into generated messages.

For example, if AutoReach discovers a personal website showcasing software engineering expertise with specific technologies, the AI might personalize an outreach message:

> "I noticed you've built some impressive projects using Go and Kubernetes. We're helping engineering teams scale their infrastructure like you have..."

Higher relevance leads to higher response rates.

### Competitor Insights

If a discovered website reveals that a lead works at a competing company or is building a competitive product, AutoReach's buyer scoring can factor that into lead quality assessments.

## Best Practices

### Combine With Other Enrichment

Website discovery works best alongside other enrichment sources:

- **LinkedIn Enrichment** - Professional context and career history
- **X Enrichment** - Real-time interests and activity
- **Web Enrichment** - Company-level context like funding, tech stack, and news

Together, these create a complete picture of your lead.

### Enable AI-Powered Messaging

{% hint style="success" %}
**Pro Tip:** Enable AI-powered DM generation in your sequences. The AI will automatically reference discovered websites to create more personalized, relevant messages.
{% endhint %}

### Review High-Value Leads

For your highest-priority leads, manually review discovered websites. You may find details you can use directly in subject lines or opening lines of your outreach.

## Troubleshooting

### No Websites Found

This is normal. Not every lead has a discoverable web presence:

- Some professionals do not maintain personal websites
- Company websites may not be well indexed
- The lead may be newer to their role

This does not affect outreach quality. AutoReach can still reference LinkedIn and X data for personalization.

### Irrelevant Websites Found

Occasionally, website finding may return results for a different person with the same name:

1. Review the discovered websites in the lead profile
2. Delete any that do not match by clicking the remove icon
3. The AI will use only the remaining websites for message generation

### Website Not Updating

Website discovery runs once per lead by default. To refresh:

1. Open the lead profile
2. Click **Refresh Enrichment**
3. Website finding will re-run with the latest data

You may want to refresh if the lead recently launched a new website or you suspect the discovered URL is outdated.

## Next Steps

- **[Email Finding](email-finding.md)** - Discover work email addresses using Findymail integration
- **[Web Enrichment](web-enrichment.md)** - Gather company-level context like funding, tech stack, and news
