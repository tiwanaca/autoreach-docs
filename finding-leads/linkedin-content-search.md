# LinkedIn Content Search

Discover high-intent decision-makers through LinkedIn posts and comments. AutoReach generates intent-organized search queries, searches LinkedIn's content feed, and extracts both post authors and commenters as leads.

## How It Works

### 1. Intent-Based Query Generation

AutoReach's AI generates search queries based on your offer, organized by intent category:

| Intent Category | What It Finds |
|-----------------|---------------|
| **Pain Points** | Professionals discussing operational challenges, inefficiencies, and frustrations |
| **Hiring Signals** | Recruiting efforts, team expansion, skill gaps |
| **Solution Seeking** | People evaluating tools, comparing options, asking for recommendations |
| **Buying Intent** | Budget allocation, purchase decisions, vendor selection |
| **Growth Signals** | Revenue growth, market expansion, new initiatives |

All intent categories are searched automatically to maximize coverage.

Queries are always generated server-side. Unlike X Tweet Search, you cannot provide your own queries directly.

### 2. Content Discovery

AutoReach searches LinkedIn's content feed to find posts matching your queries. Posts are discovered and their full details fetched-  including post text, author profile, engagement metrics, and creation date.

### 3. Commenter Extraction

When commenter extraction is enabled (the default), AutoReach extracts commenters from each discovered post, capturing their name, headline, profile URL, comment text, and the parent post context.

> **Note:** LinkedIn commenters are often decision-makers actively engaging with relevant content, which is a strong buying signal.

### 4. ICP Matching

Extracted prospects are matched against your offer's target audience. All discovered prospects are added as leads-  scoring happens during the enrichment pipeline.

### 5. Recurring Daily Searches (Buyer Expansion)

Enable **Buyer Expansion** to run the search automatically every 24 hours. Each recurring run **regenerates fresh queries** to avoid repeating previous searches and capture new content.

## Search Parameters

| Parameter | Default | Description |
|---|---|---|
| Posts per search query | 25 | Max posts to collect per query |
| Search period | Past month | How far back to search (Past 24 hours, Past week, Past month, Any time) |
| Include commenters | enabled | Extract commenters from discovered posts |
| Max comments per post | 50 | Max comments to fetch per post |
| Feed search | disabled | Also search your LinkedIn feed for signals |
| Buyer Expansion | disabled | Enable automatic daily re-runs |
| Enrichment options | - | Whether to run enrichment and deep analysis on discovered leads |

### Hiring Signals

Additional settings for hiring signal detection:

| Parameter | Default | Description |
|---|---|---|
| Max Jobs per Role | 100 | Max job postings to collect per role target (slider: 25–200) |
| Max Companies | 30 | Max companies to process (slider: 10–50) |

See [LinkedIn Job Search](linkedin-job-search.md) for details on how hiring signals work.

## Cost Estimation

Before running a search, use the cost estimation feature to preview estimated costs based on your settings.

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

**Intent categories searched:** Pain Points, Hiring Signals, Solution Seeking, Buying Intent, Growth Signals

**AI-generated queries might include:**
- "struggling with employee retention"
- "need visibility into team performance"
- "talent management challenges"
- "hiring pipeline needs improvement"

**Result:** Content search finds posts discussing HR challenges, hiring, and performance management. Post authors and commenters are extracted-  CHROs, VPs of People, and Talent Acquisition leaders discussing your exact problem space. All are added as leads and queued for enrichment and scoring.

## Troubleshooting

**Seeing too many generic results?**
- Review your offer description and pain points for clarity

**Not finding enough prospects?**
- Increase posts per search query to collect more results
- Add more specific pain points to your offer
- Check if your target audience is active on LinkedIn

**Getting low ICP match rates?**
- Verify your offer's target audience and pain points are well-defined

**High duplicate rate across searches?**
- This is normal. The same prospect may comment on multiple relevant posts. Deduplication happens before leads are added to your database.

## Next Steps

- **[LinkedIn People Search](linkedin-people-search.md)**: Target prospects by job title, company, and location
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile data
