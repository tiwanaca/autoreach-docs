# Web Enrichment

Web enrichment uses AI-powered web search to gather additional context about leads -- company details, social profiles, contact information, recent news, and professional achievements. It is a **separate, optional process** that is not part of the standard enrichment pipeline.

## How It Works

Web enrichment runs in **three sequential search phases**, each making a separate AI web search call. The AI model is resolved via the user's web search model configuration.

### Phase 1: Identity & Company

Searches for the lead's current company and role. Extracts company name, website, size, industry, funding details, tech stack, founding year, and headquarters.

### Phase 2: Social & Contact

Searches for additional social profiles (GitHub, YouTube, Medium, Substack, personal website) and contact information (phone, additional emails, Calendly link). Uses the company name discovered in Phase 1 to improve search accuracy.

### Phase 3: Activity & Insights

Searches for recent news mentions, speaking engagements, publications, podcast appearances, and achievements. **Filtered to the last 6 months only** -- news items without dates or older than 6 months are removed post-processing.

Each phase returns a confidence level (HIGH, MEDIUM, LOW, or NONE) and a list of sources.

### Rate Limit

Web enrichment processes up to **5 leads per minute**.

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
| Enrichment Confidence | Numeric score 0-0.95 indicating data reliability |
| Enrichment Sources | Deduplicated list of web sources used |
| Enrichment Summary | AI-generated overview of the lead |

## Enrichment Confidence

Confidence is a weighted average across the three search phases:

| Phase | Weight | Description |
|---|---|---|
| Phase 1 (Company) | 50% | Most critical -- identity and company data |
| Phase 2 (Social/Contact) | 25% | Supporting profiles and contact info |
| Phase 3 (Activity/Insights) | 25% | Recent news and achievements |

Each phase returns a confidence level mapped to a score: HIGH = 0.9, MEDIUM = 0.65, LOW = 0.4, NONE = 0. The weighted average is capped at 0.95.

Web enrichment data is only included in scoring context when confidence exceeds 0.3.

## How It's Triggered

Web enrichment is **not part of the standard pipeline** and does **not run automatically** when leads are added. It must be triggered explicitly.

| Trigger | Endpoint | Description |
|---|---|---|
| Manual enrichment | `POST /api/enrich` | Select leads and set `web_enrich: true` |
| Cost estimation | `POST /api/enrich/estimate` | Preview cost before enriching |
| Re-enrich skipped | `POST /api/enrich/re-enrich-skipped` | Retry failed or skipped leads |
| Status check | `GET /api/enrich/web-enrich/status` | Check progress of web enrichment jobs |

## Cost

Web enrichment costs approximately **$0.08 per lead** (3 web search calls). Cost estimation is available via the estimate endpoint before committing to enrichment.

## Error Handling

| Error | Behavior |
|---|---|
| Rate limit (429) | Retried with exponential backoff (30s base), up to 3 attempts |
| Other API/parsing errors | Marked as enriched with error recorded |
| Lead not found | Job completes silently |
| Already enriched | Job skips |
| No eligible data | Marked as enriched with error message |

## Next Steps

- **[Email Finding](email-finding.md)**: Discover work email addresses for your enriched leads
- **[Website Finding](website-finding.md)**: Find professional and company websites for deeper personalization
- **[Enrichment Pipeline](pipeline.md)**: See how the standard enrichment pipeline works
