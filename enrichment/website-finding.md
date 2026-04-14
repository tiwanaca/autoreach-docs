# Website Finding

Website finding discovers company and personal websites for leads using AI-powered web search. It is a **separate, optional enrichment** that is not part of the standard pipeline -- you must trigger it explicitly. Found websites improve email finding accuracy (providing a domain to search against) and give AI more context for outreach personalization.

## How It Works

Website finding uses AI web search (based on your model configuration) to search for a lead's company or personal website. It implements **three search strategies** tried sequentially, returning the first high-confidence result or the best result across all strategies.

### Search Strategies

**Strategy 1: Bio/Headline Company Search** (tried first)
- Extracts company name from the lead's bio using common patterns (e.g., "@ Company", "at Company", "CEO of X")
- Searches for that company's official website
- If confidence is high, returns immediately without trying other strategies
- Confidence is reduced if the company name couldn't be verified

**Strategy 2: LinkedIn Company Search**
- Extracts company from the lead's LinkedIn profile data
- Searches for the company's official website
- If confidence is high, kept for comparison

**Strategy 3: Direct Person Search** (last resort)
- Searches for the person's personal website or portfolio using their name and social handle
- Generally returns lower confidence scores

The best result above a minimum confidence threshold is returned. If no candidate meets the threshold, no website is stored.

### Rate Limit

Website finding processes up to **10 leads per minute**.

### Preconditions

A lead must have **at least one** of:
- A LinkedIn profile URL
- A bio longer than 20 characters

Leads without either are skipped.

## What Gets Stored

| Field | Description |
|---|---|
| Website URL | The discovered website URL |
| Website Confidence | Confidence score (0.0-1.0) |
| Website Source | How it was found: LinkedIn company, bio company, direct search, or Twitter search |

### Confidence Scoring

Each strategy returns a confidence level (HIGH, MEDIUM, or LOW). LinkedIn company searches tend to produce the highest confidence, followed by bio company extraction, and then direct person searches. Results below a minimum confidence threshold are discarded to avoid false matches.

## Domain Filtering

Website finding filters out social media, link aggregators, URL shorteners, and other non-website domains. Any result matching or being a subdomain of these is discarded:

- **Social networks:** twitter.com, x.com, facebook.com, instagram.com, youtube.com, tiktok.com
- **Professional platforms:** linkedin.com, github.com
- **Link aggregators:** linktr.ee, linkin.bio, bio.link, beacons.ai
- **Scheduling:** calendly.com, cal.com
- **URL shorteners:** bit.ly, t.co, goo.gl
- **Creator platforms:** medium.com, substack.com, patreon.com, ko-fi.com, buymeacoffee.com, gumroad.com
- **Messaging:** discord.gg, discord.com, telegram.me, t.me, wa.me, whatsapp.com

URLs without a protocol are auto-prepended with `https://`.

## How It's Triggered

Website finding does **not run automatically** when leads are added. It must be triggered explicitly:

To run website finding, select leads from the Leads page and enable the website finding option when triggering enrichment. You can also retry failed or skipped leads from the same interface.

## Cost

Approximately **$0.02 per lead** -- one AI web search call per strategy attempted (up to 3 strategies). Cost varies by AI provider.

## Error Handling

| Error | Behavior |
|---|---|
| Rate limit (429) | Retried with exponential backoff, up to 3 attempts |
| Lead not found | Logged as warning, job completes |
| No website found | Marked as attempted (not an error) |
| Invalid lead data | Error recorded, job completes |
| Other errors | Error recorded, job completes without retry |

Only rate limit errors trigger retries. All other errors are logged and the job completes to avoid infinite retry loops.

## Integration with Email Finding

Website finding feeds into email finding. The email finder uses the lead's website URL to extract a company domain, which is the preferred input for Findymail API lookups. Running website finding before email finding improves email discovery rates by providing a verified domain.

This is not a strict pipeline dependency -- email finding can proceed without a website URL by falling back to LinkedIn company data or the lead's bio.

## Next Steps

- **[Email Finding](email-finding.md)**: Discover work email addresses using the domains found here
- **[Web Enrichment](web-enrichment.md)**: Gather additional company context from the web
- **[Enrichment Pipeline](pipeline.md)**: See how the standard enrichment pipeline works
