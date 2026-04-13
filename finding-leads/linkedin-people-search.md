# LinkedIn People Search

Find decision-makers using LinkedIn's search API. Systematically target specific roles, companies, locations, and industries to build highly filtered prospect lists of up to 2,000 results per search.

## How It Works

LinkedIn People Search lets you directly query LinkedIn's search with precise targeting criteria. Rather than inferring prospects from content, you explicitly define who you're looking for.

There are three ways to start a search:

1. **By role + filters:** Provide a job title/role keyword along with location, industry, and other filters. This is the most common approach for systematic prospecting.
2. **By seed account:** Provide a LinkedIn profile URL or member URN to find people similar to or following that person.
3. **By lookalike seed:** Provide a `seed_id` from a lookalike account discovery to extract followers of that influencer.

### Available Filters

| Filter | Parameter | Description |
|---|---|---|
| **Title/Role** | `role` | Job title keyword (e.g., "CTO", "VP Sales"). Not used in follower-of searches. |
| **Location** | via `offer_id` | Resolved from your offer's `preferred_locations` using LinkedIn's geo typeahead API. Supports countries, regions, cities, and abstract concepts like "Worldwide." |
| **Industry** | `industry_ids` | LinkedIn industry IDs. Can be provided directly or resolved from your offer's `industry_ids`. |
| **Current Company** | via LinkedIn API | Company URNs for account-based targeting. |
| **Network Distance** | `network` | 1st degree (F), 2nd degree (S), or 3rd+ degree (O). |
| **Profile Language** | `profile_languages` | Defaults to `['en']` if not specified. |
| **Follower Of** | `follower_of_urn` | Find followers of a specific LinkedIn member URN. Used by lookalike-seeded searches. |

Note: **company size** is not a LinkedIn People Search filter. It is part of your offer's ICP definition and checked during scoring, not at search time. **Follower count** is also not a filter — `followerOf` filters by followers of a specific person, not by a count range.

### Search Parameters

| Parameter | Default | Description |
|---|---|---|
| `linkedin_account_id` | *(required)* | LinkedIn account to search from |
| `role` | — | Job title keyword (required for direct role searches) |
| `offer_id` | — | Resolves geo + industry filters from the offer |
| `industry_ids` | from offer | Override offer's industry IDs |
| `profile_languages` | `['en']` | Languages to filter by |
| `count` | 500 | Max results to collect. Set to 0 for unlimited (caps at 10,000). |
| `pipeline_actions` | — | Options for `enrich` and `deepAnalysis` |
| `buyer_expansion` | false | Enable daily autopilot with role rotation |
| `expansion_roles` | default list | Custom roles for buyer expansion rotation |

## Progressive Background Search

Searches run in the background — results are saved to the database page by page as they arrive, rather than waiting for the entire search to complete. The frontend polls for progress, showing `total_found` and `current_page` as they update.

**Pagination details:**
- 10 results per page via LinkedIn's API
- Up to 200 pages per search (2,000 results max)
- Configurable delays between pages (8-12s base + random jitter) to respect rate limits
- Search stops when the result count target is met, total results are exhausted, or max pages is reached

### Auto-Resume on Interruption

If a search is interrupted (server restart, timeout), it automatically resumes from the last completed page. The recovery service finds stuck searches (status `running`/`pending`) and resumes them with up to 3 retry attempts and a 15-minute timeout per attempt. Non-retryable errors (expired session, automation detected) are not retried.

## Buyer Expansion (Daily Autopilot)

When `buyer_expansion` is enabled, the **buyer expansion scheduler** automatically re-runs the search daily with role rotation to continuously discover new leads.

**How it works:**
1. The scheduler runs every hour and picks up searches where the last run was 24+ hours ago
2. It rotates to the next role in the expansion queue (with a random 0-6 hour delay for safety)
3. Runs a new search for that role with a daily cap of 100 leads per run
4. If a role returns 0 results, immediately rotates to the next
5. When all roles are exhausted, buyer expansion is automatically disabled

**Default expansion roles:** CEO, CTO, CFO, COO, Founder, VP, Director, Head, Manager, Lead, Partner, Owner. You can provide custom roles via `expansion_roles`.

## Account Safety

All LinkedIn requests route through the account gateway with multiple protection layers:

- **Concurrency:** Max 1 concurrent request per account
- **Rate limiting:** Max 15 requests/minute per account
- **Daily budget:** 25,000 requests/account/day hard cap
- **Emergency pause:** 30-minute block triggered by automation detection (429, 999, 403 responses)
- **Heavy operation lock:** Only one heavy operation (search, buyer expansion) runs at a time per account
- **Inter-page delays:** 8-12s between pages plus random jitter

You do not need to configure any of this — it is automatic.

## Result Data

Each search result includes:
- Name and headline
- LinkedIn vanity URL and full profile URL
- Member ID (base64 entity URN)
- Location
- Profile image URL

Results are saved progressively and queued for enrichment based on your `pipeline_actions` setting.

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

### Example 3: Account-Based Targeting
- **Role:** Head of Operations, Director Operations
- **Company:** Specific target company URNs
- **Result:** Operations leaders at your target accounts

### Example 4: Continuous Prospecting with Buyer Expansion
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
- Results are scored by buyer intelligence after enrichment — irrelevant profiles will score low automatically

**Search seems slow?**
- This is normal for large result sets. Delays of 8-12s between pages are intentional for account safety.
- Searches run in the background — you can continue using the app.
- Large searches (1,500+ results) may take 30+ minutes to complete.

**Search stuck or failed?**
- Auto-recovery retries stuck searches up to 3 times on server restart
- If the LinkedIn session expired, reconnect your account and the search will resume
- Automation-detected pauses clear after 30 minutes

## Next Steps

- **[Lookalike Audiences](lookalike-audiences.md)**: Discover relevant seed accounts, then use People Search to extract their followers
- **[LinkedIn Content Search](linkedin-content-search.md)**: Find leads via content engagement instead of profile filters
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile and company data
