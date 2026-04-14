# LinkedIn People Search

Find decision-makers using LinkedIn's search. Systematically target specific roles, companies, locations, and industries to build highly filtered prospect lists.

## How It Works

LinkedIn People Search lets you directly query LinkedIn's search with precise targeting criteria. Rather than inferring prospects from content, you explicitly define who you're looking for.

There are three ways to start a search:

1. **By role + filters:** Provide a job title/role keyword along with location, industry, and other filters. This is the most common approach for systematic prospecting.
2. **By seed account:** Provide a LinkedIn profile URL to find people similar to or following that person.
3. **By lookalike seed:** Select a seed from a lookalike account discovery to extract followers of that influencer.

### Available Filters

| Filter | Description |
|---|---|
| **Title/Role** | Job title keyword (e.g., "CTO", "VP Sales"). Not used in follower-of searches. |
| **Location** | Resolved from your offer's preferred locations. Supports countries, regions, cities, and abstract concepts like "Worldwide." |
| **Industry** | Resolved from your offer or overridden directly. |
| **Follower Of** | Find followers of a specific LinkedIn profile. Used by lookalike-seeded searches. |

Note: **Company size** and **network distance** are not search filters - they are part of your offer's ICP definition and checked during scoring, not at search time.

### Search Parameters

| Parameter | Default | Description |
|---|---|---|
| **LinkedIn Account** | *(required)* | LinkedIn account to search from |
| **Role** |-  | Job title keyword (required for direct role searches) |
| **Offer** |-  | Resolves location + industry filters from the offer |
| **Industries** | from offer | Override offer's industry IDs |
| **Max Results** | 500 | Max results to collect (slider: 50–5,000) |
| **Enrichment Options** |-  | Whether to run enrichment and deep analysis on discovered leads |
| **Buyer Expansion** | disabled | Enable daily autopilot with role rotation |

## Progressive Background Search

Searches run in the background-  results are saved progressively as they arrive, rather than waiting for the entire search to complete. The UI shows progress as results come in.

If a search is interrupted, it automatically resumes from where it left off. Non-retryable errors (expired session, automation detected) stop the search.

## Buyer Expansion (Daily Autopilot)

When buyer expansion is enabled, AutoReach automatically re-runs the search daily with role rotation to continuously discover new leads.

**How it works:**
1. Each day, the system rotates to the next role in the expansion queue
2. Runs a new search for that role
3. If a role returns no results, it rotates to the next
4. When all roles are exhausted, buyer expansion is automatically disabled

You can select a role from AI-generated suggestions based on your offer, or provide custom roles.

## Account Safety

AutoReach automatically manages LinkedIn account safety with rate limiting, request throttling, and concurrency controls. You do not need to configure any of this-  it is fully automatic.

## Result Data

Each search result includes:
- Name and headline
- LinkedIn profile URL
- Location
- Profile image URL

Results are queued for enrichment based on your enrichment settings.

## Building Effective Filter Combinations

### Example 1: CTOs in a Specific Region
- **Role:** CTO, VP Engineering
- **Location:** San Francisco Bay Area (resolved from offer)
- **Industry:** Software, Technology
- **Result:** Technical decision-makers in your target metro

### Example 2: Financial Services Decision-Makers
- **Role:** VP Finance, CFO, Treasurer
- **Location:** New York, London, Singapore
- **Industry:** Financial Services, Banking
- **Result:** Finance leaders across major financial hubs

### Example 3: Continuous Prospecting with Buyer Expansion
- **Role:** VP Sales (initial)
- **Buyer expansion:** Enabled with default roles
- **Result:** Daily automated discovery cycling through CEO, CTO, VP, Director, Manager roles at matching companies

## Best Practices

1. **Use multiple searches for different personas.** Don't try to find everyone in one search. Create separate searches for different roles.

2. **Combine filters strategically.** Location + Title + Industry yields higher-quality results than any single filter.

3. **Enable buyer expansion for ongoing discovery.** Set up a search with buyer expansion enabled to continuously find new decision-makers without manual effort.

4. **Start with a focused search, then scale.** Run a search with tight filters first, review results, then broaden if needed.

5. **Monitor quality downstream.** As leads are scored and enrolled in sequences, track response rates. Adjust filters if quality is low.

## Troubleshooting

**Getting too many results?**
- Add more filter criteria (industry, company, location)
- Use more specific title keywords
- Narrow geographic scope

**Not getting enough results?**
- Broaden your filters (wider geography, related titles)
- Try alternative job title variations
- Remove industry filter to cast a wider net

**Seeing irrelevant profiles?**
- Be more specific with title keywords
- Add industry filter if not set
- Results are scored by buyer intelligence after enrichment-  irrelevant profiles will score low automatically

**Search seems slow?**
- This is normal for large result sets. Searches are paced conservatively to protect your account.
- Searches run in the background - you can continue using the app.
- Large searches (1,500+ results) may take a while to complete.

**Search stuck or failed?**
- Auto-recovery retries stuck searches automatically on server restart
- If the LinkedIn session expired, reconnect your account and the search will resume
- Temporary pauses due to rate limiting clear automatically

## Next Steps

- **[Lookalike Audiences](lookalike-audiences.md)**: Discover relevant seed accounts, then use People Search to extract their followers
- **[LinkedIn Content Search](linkedin-content-search.md)**: Find leads via content engagement instead of profile filters
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile and company data
