# LinkedIn People Search

Find decision-makers using LinkedIn's powerful search filters. Systematically target specific roles, companies, locations, and industries to build highly filtered prospect lists.

## How It Works

LinkedIn People Search lets you directly query LinkedIn's search API with precise targeting criteria. Rather than inferring prospects from content, you explicitly define who you're looking for.

### Available Filters

**Network Distance**
- **1st degree:** Immediate connections (requires connection first)
- **2nd degree:** Connections of your connections (broader reach)
- **3rd degree:** Extended network (widest reach)

**Geographic Location**
- Filter by country, region, or city
- Respects your offer's location settings
- Enables location-specific targeting

**Industry**
- Target by primary industry classification
- Find roles across specific verticals
- Combined with other filters for precision

**Company**
- Search by specific company names or domains
- Find decision-makers at target accounts
- Great for account-based outreach

**Title/Role**
- Filter by job title or role keywords
- Find CTOs, CFOs, VPs, Managers, etc.
- Multiple titles can be combined with OR logic

**Followers**
- Filter by follower count ranges
- Find influencers or thought leaders
- Optional secondary filter

## Progressive Search with Background Processing

Our system handles large search queries efficiently:

- **Initial Query:** Submits your filter criteria to LinkedIn
- **Pagination:** Automatically fetches multiple pages of results
- **Background Processing:** Continues searching while you work
- **Real-time Updates:** See prospect count as results stream in

{% hint style="info" %}
LinkedIn People Search can return up to 2,000 results. For larger searches, consider running multiple searches with refined filters.
{% endhint %}

## Account Safety

AutoReach includes built-in safety measures to protect your LinkedIn account during searches. Requests are spaced out naturally and rate limits are respected automatically. You do not need to configure anything.

## Search Limits

Each search can return up to 2,000 results. Use filters to narrow scope for more relevant results. Searches run in the background while you work, and if a search is interrupted, it automatically resumes where it left off.

## Building Effective Filter Combinations

### Example 1: CTOs at Funded Startups
- **Title:** Chief Technology Officer, CTO, VP Engineering
- **Company:** (leave empty to find startups broadly)
- **Location:** San Francisco Bay Area
- **Result:** Find all CTOs in your metro area

### Example 2: Financial Services Decision-Makers
- **Industry:** Financial Services, Banking
- **Title:** VP Finance, CFO, Treasurer
- **Location:** Major US financial hubs
- **Result:** Target finance leaders across banking sector

### Example 3: SaaS Company Operators
- **Company:** Target list of 50 SaaS companies
- **Title:** Head of Operations, VP Ops, Director Operations
- **Location:** (leave empty for fully distributed teams)
- **Result:** Ops leaders at companies that match your TAM

### Example 4: Growth/Scale-Stage Growth Leaders
- **Title:** VP Growth, Growth Manager, Director Growth
- **Location:** US (or your preferred region)
- **Industry:** SaaS, Technology
- **Result:** Growth leaders actively scaling B2B companies

## Progressive Targeting Strategy

**Start broad, then refine:**

1. **First search:** Use just one filter (e.g., location)
2. **Review results:** See what you're getting
3. **Add filters:** Add title, industry, company to narrow results
4. **Iterate:** Refine until you have 500-2,000 highly relevant prospects

## Best Practices

1. **Use multiple searches for different personas:** Don't try to find everyone in one search. Create separate searches for CMO, CTO, VP Sales.

2. **Combine filters strategically:** Location + Title + Industry yields higher-quality results than any single filter.

3. **Start with 1,000-2,000 person list:** This gives you enough volume while maintaining quality.

4. **Test and iterate:** Run a small search first, review results, then scale.

5. **Monitor quality:** As you add prospects to sequences, track response rates. Adjust filters if response is low.

6. **Save filter combinations:** Reuse filter combinations for recurring searches to capture newly promoted decision-makers.

## Troubleshooting

**Getting too many results?**
- Add more filter criteria (industry, company, title)
- Use more specific title searches
- Narrow geographic location further

**Not getting enough results?**
- Broaden your filters (e.g., widen geography)
- Try related titles or roles
- Check if your target audience exists on LinkedIn in that volume

**Seeing a lot of irrelevant profiles?**
- Be more specific with title filters
- Add company domain or industry filter
- Review profile relevance manually before adding to sequences

**Search seems slow?**
- This is normal for large result sets
- LinkedIn enforces rate limits for safety
- Large searches (1,500+ results) naturally take longer
- Searches run in background while you work

## Integration with Other Methods

LinkedIn People Search works best when combined with:

- **[Cross-Platform Matching](cross-platform-matching.md):** Find X profiles for your LinkedIn search results
- **[Lookalike Audiences](lookalike-audiences.md):** Identify relevant influencers in your target market, then find similar people
- **[Content Search](linkedin-content-search.md):** Start with content searches to identify roles, then use People Search to scale that profile type
