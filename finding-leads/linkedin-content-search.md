# LinkedIn Content Search

Discover high-intent decision-makers through LinkedIn posts and comments. AutoReach generates intent-organized search queries, searches LinkedIn's content feed, and extracts both post authors and commenters as leads.

## How It Works

### 1. Intent-Based Query Generation

AutoReach's AI generates 10-15 search queries and 15-20 keywords based on your offer. You select which intent categories to search from:

| Intent Category | What It Finds |
|-----------------|---------------|
| **Pain Points** | Professionals discussing operational challenges, inefficiencies, and frustrations |
| **Hiring Signals** | Recruiting efforts, team expansion, skill gaps |
| **Solution Seeking** | People evaluating tools, comparing options, asking for recommendations |
| **Buying Intent** | Budget allocation, purchase decisions, vendor selection |
| **Growth Signals** | Revenue growth, market expansion, new initiatives |

The AI may also generate queries for additional categories like competitor switching, cost pressure, compliance/regulatory, and tool evaluation, but only the categories you select are used.

AutoReach also generates search signals from your offer automatically. These are given the highest priority in query generation — the AI is instructed to build queries around them.

Queries are always generated server-side. Unlike X Tweet Search, you cannot provide your own queries directly.

### 2. Content Discovery

AutoReach searches LinkedIn's content feed to find posts matching your queries. For each query:

1. An initial search request goes to LinkedIn's content search endpoint
2. Pagination fetches 3 results per page
3. Post activity URNs are extracted from the response stream
4. Pagination continues until the configured posts per intent limit is reached, or a maximum of 15 pages per query

Delays are applied between requests to respect rate limits.

### 3. Post Detail Enrichment

For each discovered post URN, AutoReach fetches the full post details via LinkedIn's API, including the post text, author name, author profile, engagement metrics, and creation date.

### 4. Commenter Extraction

When commenter extraction is enabled (the default), AutoReach fetches comments on each discovered post via LinkedIn's API. For each commenter, the following data is extracted:

- Name, headline, profile URL, and profile image
- Comment text, comment URN, and creation date
- Parent post context (text, author, URL)

Maximum comments per post is controlled by the max comments setting (default: 100).

> **Note:** LinkedIn commenters are often decision-makers actively engaging with relevant content, which is a strong buying signal.

### 5. ICP Matching

Extracted prospects are matched against your offer's target audience. This annotates each prospect with an ICP match reason but does not filter them out — all discovered prospects are added as leads. Scoring happens downstream during the enrichment pipeline.

### 6. Recurring Daily Searches

You can enable any content search to run on a daily recurring schedule. The scheduler runs hourly and triggers searches that were last run more than 24 hours ago. Each recurring run **regenerates fresh queries** to avoid repeating previous searches and capture new content. Unconverted prospects from the previous run are cleaned up before rerunning.

## Search Parameters

| Parameter | Default | Description |
|---|---|---|
| Intent categories | *(required)* | Which intent categories to search |
| Posts per intent | 25 | Max posts to collect per intent category |
| Include commenters | enabled | Extract commenters from discovered posts |
| Max comments | 100 | Max comments to fetch per post |
| Days back | 30 | How far back to search |
| Daily recurring | disabled | Enable automatic daily re-runs |
| Enrichment options | -- | Whether to run enrichment and deep analysis on discovered leads |
| Max jobs per role | -- | For hiring signals: max job postings per role |
| Max companies | -- | For hiring signals: max companies to process |

## Cost Estimation

Before running a search, use the cost estimation feature to preview estimated costs. The estimate shows minimum and maximum costs with a detailed breakdown based on your selected intent categories, posts per intent, and commenter settings.

## Progress Tracking

While a content search runs, progress is tracked and updated in real time. You can monitor:

- **Posts found:** Total LinkedIn posts matching your queries
- **Comments fetched:** Total comments retrieved
- **People found:** Unique prospects identified
- **People after ICP match:** Prospects matching your ICP
- **Current operation:** What phase the search is in
- **Current query:** Which query is currently being searched

## Best Practices

1. **Be specific.** More specific search terms yield higher-quality prospects than broad keywords.

2. **Include pain points.** Search for the exact pain points your offer solves (from your offer description).

3. **Keep commenters on.** LinkedIn commenters are often highly engaged decision-makers. Leave commenter extraction enabled.

5. **Run recurring searches.** Set up daily LinkedIn content searches to capture new prospects continuously with fresh query rotation.

## Example Workflow

**Offer:** "People analytics and HR software platform"

**Selected intent categories:** Pain Points, Hiring Signals, Solution Seeking

**AI-generated queries might include:**
- "struggling with employee retention"
- "need visibility into team performance"
- "talent management challenges"
- "hiring pipeline needs improvement"

**Result:** Content search finds posts discussing HR challenges, hiring, and performance management. Post authors and commenters are extracted — CHROs, VPs of People, and Talent Acquisition leaders discussing your exact problem space. All are added as leads and queued for enrichment and scoring.

## Troubleshooting

**Seeing too many generic results?**
- Narrow your intent categories — fewer categories means more focused queries
- Review your offer description and pain points for clarity

**Not finding enough prospects?**
- Add more intent categories
- Increase posts per intent to collect more results
- Add more specific pain points to your offer
- Check if your target audience is active on LinkedIn

**Getting low ICP match rates?**
- Verify your offer's target audience and pain points are well-defined

**High duplicate rate across searches?**
- This is normal. The same prospect may comment on multiple relevant posts. Deduplication happens before leads are added to your database.

## Next Steps

- **[LinkedIn People Search](linkedin-people-search.md)**: Target prospects by job title, company, and location
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile data
