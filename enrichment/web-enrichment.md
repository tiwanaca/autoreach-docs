# Web Enrichment

Web enrichment uses AI-powered web search to gather additional context about leads - company details, social profiles, contact information, recent news, and professional achievements. It is a **separate, optional process** that is not part of the standard enrichment pipeline.

## How It Works

Web enrichment uses AI web search to gather three categories of data:

- **Identity & Company**-  current company, role, website, size, industry, funding, tech stack, headquarters
- **Social & Contact**-  additional social profiles (GitHub, YouTube, Medium, Substack, personal website) and contact information (phone, additional emails, scheduling links)
- **Activity & Insights**-  recent news mentions, speaking engagements, publications, podcast appearances, and achievements (last 6 months only)

### Preconditions

A lead must have **at least one** of:
- A LinkedIn profile URL
- A website URL
- A bio longer than 20 characters

Leads without any of these are skipped.

## What Gets Extracted

### Company Information

| Field | Description |
|---|---|
| Company Name | Company name |
| Company Website | Company domain URL |
| Company Size | Employee range ("1-10", "11-50", "51-200", "201-500", "500+") |
| Industry | Primary industry classification |
| Description | Brief company description |
| Founded Year | Founding year |
| Headquarters | Primary office location |
| Funding Stage | Funding stage (Seed, Series A, B, C, etc.) |
| Funding Amount | Total raised to date |
| Investors | Array of known investor names |
| Technologies | Array of tech stack tools and frameworks |

If the lead does not already have an employee count value, the company size is promoted for filtering.

### Social Profiles

| Field | Description |
|---|---|
| Twitter | X/Twitter profile URL |
| GitHub | GitHub profile |
| YouTube | YouTube channel |
| Medium | Medium blog |
| Substack | Substack newsletter |
| Personal Website | Portfolio, consulting site, or blog |
| Other | Array of other platform profiles |

### Contact Information

| Field | Description |
|---|---|
| Phone | Phone number |
| Additional Emails | Array of work or personal emails beyond primary |
| Calendly | Scheduling page URL |

### News Mentions

Array of recent news items (last 6 months only):

| Field | Description |
|---|---|
| Title | Headline |
| Source | Publication name |
| URL | Link to the article |
| Date | Publication date (YYYY-MM-DD, required) |
| Summary | Brief description |

### Insights

| Field | Description |
|---|---|
| Notable Achievements | Array of professional accomplishments |
| Speaking Engagements | Conferences and events |
| Publications | Articles, whitepapers, or research authored |
| Podcast Appearances | Interviews and podcast guest slots |

### Confidence & Sources

| Field | Description |
|---|---|
| Enrichment Confidence | Overall data reliability indicator |
| Enrichment Sources | List of web sources used |
| Enrichment Summary | AI-generated overview of the lead |

Web enrichment data is only included in scoring context when overall confidence is sufficient.

## How It's Triggered

Web enrichment is **not part of the standard pipeline** and does **not run automatically** when leads are added. It must be triggered explicitly.

You can trigger web enrichment manually from the Leads page by selecting leads and enabling the web enrichment option. You can also preview costs before enriching, retry failed or skipped leads, and check enrichment progress - all from the same interface.

## Cost

Cost estimation is available before starting enrichment. Cost varies by AI model configuration.

## Error Handling

Transient errors (rate limits) are automatically retried. Other errors are recorded and the job completes-  web enrichment failure does not block other enrichment steps.

## Next Steps

- **[Email and Website Finding](optional-enrichment.md)**: Discover work email addresses and company websites
- **[Enrichment Pipeline](pipeline.md)**: See how the standard enrichment pipeline works
