# X Tweet Search

Find high-intent prospects by searching X for tweets that match your offer. AutoReach uses AI to generate targeted search queries organized by intent category, then extracts both tweet authors and commenters as leads.

## How It Works

### 1. Query Generation

When you start a search, you can either:

- **Let AI generate queries:** Provide your offer and AutoReach generates 15-25 targeted keywords (short 2-4 word phrases in first-person conversational style) plus structured **intent clusters** — groups of queries organized by intent type. The AI selects 3-6 intent categories most relevant to your offer, with 2-6 queries per cluster. Competitor-specific keywords are generated and merged separately.
- **Provide your own keywords:** Enter your own keywords and search query directly to skip AI generation entirely.

#### Intent Categories

The AI organizes queries across these intent types (selecting the most relevant for your offer):

- **Operational Pain** — day-to-day frustrations and inefficiencies
- **Budget Pressure** — cost concerns and budget constraints
- **Hiring & Scaling** — growth challenges and team scaling
- **Buying Evaluation** — actively comparing or evaluating solutions
- **Competitor Switch** — switching away from or frustrated with competitors
- **Growth Signals** — expansion, new markets, scaling needs
- **Security & Compliance** — regulatory, security, or compliance concerns
- **Professional Identity** — role-based challenges and aspirations
- **Vertical Specific** — industry-specific pain points

A separate AI step generates insider terminology queries specific to your industry to catch leads using specialized language.

### 2. Search Execution

AutoReach searches X via X's API. For each query group:

1. **Combined OR query** — up to 7 keywords combined with OR operators, searched in both `Top` and `Latest` modes
2. **Individual term searches** — each keyword is also searched individually in `Latest` mode to catch results missed by the combined query
3. **Search operators applied** — exact phrase matching for 2-word terms, minus exclusions, minimum engagement filter

Search results are deduplicated at two levels: per-search (in-memory Set) and globally across all user searches (database check). Link-only tweets are filtered out.

#### Search Parameters

| Parameter | Default | Description |
|---|---|---|
| Max tweets | 100 | Total tweets to collect across all query groups |
| Days back | 60 | How far back to search |
| Include replies | enabled | Extract commenters from matching tweets |
| Max replies | 100 | Max replies to check per tweet |
| Exclusions | giveaway, retweet, airdrop | Terms to exclude from results |
| Daily recurring | disabled | Enable automatic daily re-runs |
| Enrichment options | -- | Whether to run enrichment and deep analysis on discovered leads |

### 3. Lead Extraction

AutoReach pulls leads from two sources within each matching tweet:

- **Tweet authors:** People posting directly about relevant topics, challenges, or needs
- **Commenters:** Professionals engaging in the conversation (when reply extraction is enabled). Replies are fetched for tweets with replies, up to the configured max replies per tweet.

All extracted prospects are converted to leads and queued for enrichment. An ICP matching step runs if your offer has a target audience defined -- ICP matches get a higher priority score, but all prospects are added regardless. Scoring happens downstream during the enrichment pipeline.

### 4. Recurring Daily Searches

You can enable any search to run automatically on a recurring schedule. The recurring search scheduler runs every hour and triggers searches that were last run more than 24 hours ago.

Each recurring run **regenerates fresh keywords** based on your offer, using the previous keywords as a reference to force variation. If keyword regeneration fails, the existing keywords are used as a fallback. Searches stuck in `running` for 2+ hours or `analyzing` for 3+ hours are automatically recovered.

### 5. Cost Estimation

Before running a search, you can use the cost estimation feature to preview the estimated AI and API costs based on your selected offer and maximum tweet count.

## Best Practices for Keyword Selection

The quality of your search results depends heavily on the keywords and phrases in your queries:

- **Be specific.** Multi-word phrases like "API rate limiting frustration" or "AWS cost optimization" produce far better results than single generic words like "API" or "cloud."
- **Use your audience's language.** Include industry jargon, product names, and terminology your target buyers actually use when discussing their problems.
- **Start broad, then refine.** Run an initial search with a range of terms, review the results, and narrow your queries based on what performs well.
- **Experiment with variations.** Different keyword combinations surface different prospect segments. Test multiple approaches to find the best fit for your offer.
- **Customize exclusion terms.** The default exclusions are minimal (`giveaway`, `retweet`, `airdrop`). Add terms relevant to your space to filter out noise, or clear the list entirely if defaults are too aggressive.

## Example Workflow

**Offer:** B2B SaaS sales automation platform

**AI-generated queries might include:**

Keywords:
- "manual sales process too slow"
- "need sales pipeline visibility"
- "CRM data quality issues"

Intent clusters:
- **Operational Pain:** "my team spends hours on data entry", "sales admin is killing productivity"
- **Buying Evaluation:** "evaluating sales tools", "comparing CRM platforms"
- **Competitor Switch:** "moving away from Salesforce", "HubSpot isn't scaling"

**Result:** Each query surfaces relevant tweets from CTOs, VPs of Sales, and Operations Managers. Both tweet authors and commenters are extracted, converted to leads, and queued for enrichment and scoring.

## Troubleshooting

**Getting too many irrelevant results?**
- Review your offer description for clarity and specificity
- Add more exclusion terms to filter out common false positives
- Use more niche, multi-word search phrases

**Not finding enough prospects?**
- Broaden your search terms or include common synonyms
- Increase the max tweets setting to collect more results
- Increase the days back setting to search further into the past
- Check whether your target audience actively discusses these topics on X

**Seeing duplicate prospects across searches?**
- This is expected. AutoReach deduplicates prospects at both the per-search and global level, so the same person appearing in multiple searches will not create duplicate leads.

## Next Steps

- **[Enrichment Pipeline](../enrichment/pipeline.md)**: Learn how discovered leads get enriched with profile and company data
- **[Building Sequences](../outreach/building-sequences.md)**: Set up outreach sequences for your newly discovered leads
