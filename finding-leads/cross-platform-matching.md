# Cross-Platform Profile Matching

AutoReach can find the matching profile on the other platform for your leads. If you have a prospect on LinkedIn, it can locate their X profile. If you have them on X, it can locate their LinkedIn profile. This gives you multi-platform outreach capability from a single discovery source.

## How to Trigger It

Cross-platform matching is a **manual action**. You trigger it from the Leads page:

1. Select the leads you want to match
2. Click the **Enrich** button in the floating selection bar
3. In the Enrich modal, look under the **Profile Discovery** category
4. Toggle **Find LinkedIn** (for X leads) or **Find X Profile** (for LinkedIn leads)
5. Confirm to start the search

The options are platform-aware — "Find LinkedIn" only appears when you have X leads selected, and "Find X Profile" only appears when you have LinkedIn leads selected. When you select a profile finder, the corresponding profile enrichment option is automatically enabled so the found profile gets enriched immediately.

## How Matching Works

### Finding X Profiles for LinkedIn Leads

Since X blocks web crawlers, AutoReach uses a single optimized **OpenAI web search** call to search external sites (LinkedIn, Crunchbase, GitHub, personal websites, press releases) for mentions of the person's Twitter handle.

**Search queries constructed:**
- `"[name]" twitter profile`
- `"[name]" "@" twitter`
- `"@[linkedin_username]" "[name]"`
- `"[name]" "[company]" twitter`
- `"[name]" twitter site:linkedin.com` (and other sites)

**Match scoring** — candidates are evaluated across multiple factors including name similarity, source credibility, company match, corroboration from multiple independent sources, and geographic consistency. Each factor is weighted by its reliability, and the combined score determines whether a match is accepted.

### Finding LinkedIn Profiles for X Leads

Uses a single optimized OpenAI web search call combining all available context (name, Twitter handle, company, location, website domain, bio keywords) into one query.

**Search queries constructed:**
- `"[name]" site:linkedin.com/in`
- `"[name]" @[twitterUsername] linkedin`
- Company and location variant queries when available

The same scoring approach and confidence mapping is applied as the X finder.

## What Happens After a Match

- **If found:** the lead record is updated with the matched profile URL, and enrichment proceeds for both platforms
- **If not found:** enrichment continues with data from the source platform only

LinkedIn and X profile enrichment run **in parallel** for leads that have URLs on both platforms. Enrichment failure on one platform does not block the other.

**Skip logic:** If the lead already has a profile URL or a previous search timestamp for the other platform, AutoReach skips the search entirely.

## AI Provider and Cost

Both finders use **OpenAI web search**. This is the primary cost of cross-platform matching — one web search call per lead per missing platform.

Each search takes approximately 5-10 seconds per lead.

## Example Workflows

**LinkedIn-First Outreach with X Follow-up**

1. Run a LinkedIn search and discover prospects.
2. Select the LinkedIn leads and run **Find X Profile** from the Enrich modal.
3. Send LinkedIn messages to all prospects.
4. Follow up on X for leads where a profile was found, increasing your touchpoints without repeating the same channel.

**X-First Discovery with Full Professional Context**

1. Run a tweet search and discover prospects engaging with relevant topics.
2. Select the X leads and run **Find LinkedIn** from the Enrich modal.
3. Full professional data (company, role, tenure, education, skills) enriches your lead records.
4. Use the richer profile data to write more informed, personalized outreach.

**Account-Based Outreach**

1. Run a LinkedIn people search targeting specific companies.
2. Select the leads and run **Find X Profile** to locate their X accounts.
3. Run coordinated outreach across both platforms for higher visibility.

## Troubleshooting

**Not finding X profiles for some LinkedIn leads?**
This is expected. Not every professional maintains an active X account. Since X blocks direct crawling, the finder relies on mentions of handles on external sites — handles that only appear on X itself cannot be found. Leads with more distinctive names and clear company affiliations tend to match more reliably.

**A match looks incorrect?**
Low-confidence matches are filtered out automatically, but occasional false positives can occur with very common names. You can manually update the lead record to correct a bad match.

**Both profiles exist but no match was made?**
The system requires a minimum confidence score before linking profiles. If the available signals were not sufficient (e.g., common name, no company overlap, handle doesn't contain the name), it skips the link rather than risk a false positive. You can always add the profile manually.

## Next Steps

- **[Enrichment Pipeline](../enrichment/pipeline.md)** — See how matched profiles flow through enrichment and scoring
- **[How Leads Work](../core-concepts/leads.md)** — Understand unified lead profiles across platforms
