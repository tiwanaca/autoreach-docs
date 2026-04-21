# Lead Pool and Cross-Platform Matching

## Lead Pool (Instant Matching)

Discover qualified prospects by matching your offer's ICP against a shared pool of pre-enriched lead profiles. Lead Pool delivers results in seconds because the profiles are already enriched - only scoring needs to run.

### What Is the Lead Pool?

The Lead Pool is a shared database of enriched lead profiles. Every lead enriched through AutoReach is added to the pool. When you create an offer, AutoReach automatically matches existing pool entries against your ICP to find the best matches.

Unlike keyword-based filtering, the matching understands the meaning behind your offer description. A lead whose profile is conceptually aligned with your target audience will surface even if they do not share exact keywords with your search criteria.

### How It Works

**Profile Storage** - When any lead completes the enrichment pipeline, their professional profile is stored in the pool, including role, bio, industry, company, location, and skills.

**ICP Matching** - When matching triggers, your offer's ICP is compared against stored profiles. The matching is based on your target audience definition, industries, and preferred locations - focusing on who the buyer is, not what you are selling.

**Lead Creation** - Matched profiles are added as new leads with source marked as "Lead Pool," fresh scoring against your specific offer, and enrichment skipped since profile data is already available. Existing leads are excluded to prevent duplicates.

### When Does It Trigger?

| Trigger | When It Fires |
|---|---|
| **New offer created** | When you create a new offer |
| **Search finishes** | When any search completes |
| **Follower extraction starts** | When a follower extraction begins |

Updating an existing offer does not automatically trigger a pool match - only offer creation does.

### Cost

Lead Pool matching is **not zero-cost**. While platform API costs are zero (leads are already enriched), AI scoring costs apply since every matched lead is queued for scoring using your configured AI models.

### Viewing Pool Leads

See pool-sourced leads by filtering the **All** tab on the Leads page by "Pool DB" source.

### Progress During LinkedIn Searches

When a LinkedIn search runs, pool matches triggered by that search are counted alongside the profiles fetched during the search. The processing banner shows the combined count so you can see the full result set as it is built.

### Best Practices

1. **Build the database first.** Lead Pool is most effective with a large base of enriched leads. Start with discovery searches before relying on pool matching.
2. **Write detailed target audience definitions.** The matching is built from your target audience, industries, and locations. Be specific in those fields.
3. **Monitor match quality.** Track response rates from Lead Pool matches and compare them to other discovery methods.
4. **Combine with other methods.** Use Lead Pool for rapid scaling while continuing X and LinkedIn searches for fresh intent signals.

---

## Cross-Platform Profile Matching

AutoReach can find the matching profile on the other platform for your leads. If you have a prospect on LinkedIn, it can locate their X profile. If you have them on X, it can locate their LinkedIn profile.

### How to Trigger It

Cross-platform matching is a **manual action**:

1. Select the leads you want to match on the Leads page
2. Click the **Enrich** button in the floating selection bar
3. In the Enrich modal, look under **Profile Discovery**
4. Toggle **Find LinkedIn** (for X leads) or **Find X Profile** (for LinkedIn leads)
5. Confirm to start the search

The options are platform-aware. "Find LinkedIn" only appears for X leads, and "Find X Profile" only appears for LinkedIn leads. When you select a profile finder, the corresponding profile enrichment is automatically enabled so the found profile gets enriched immediately.

### How Matching Works

AutoReach uses AI-powered web search to find matching profiles across platforms. Candidates are evaluated on name similarity, company match, source credibility, and corroboration from multiple sources.

### What Happens After a Match

- **If found:** the lead record is updated with the matched profile URL, and enrichment proceeds for both platforms
- **If not found:** enrichment continues with data from the source platform only

LinkedIn and X profile enrichment run in parallel for leads that have URLs on both platforms. Failure on one platform does not block the other.

### Example Workflows

**LinkedIn-First with X Follow-up** - Run a LinkedIn search, then use Find X Profile to locate their X accounts. Send LinkedIn messages first, then follow up on X for multi-channel outreach.

**X-First with Full Professional Context** - Run a tweet search, then use Find LinkedIn to get full professional data (company, role, tenure, education, skills) for richer personalization.

**Account-Based Outreach** - Run a LinkedIn people search targeting specific companies, then use Find X Profile for coordinated outreach across both platforms.

### Troubleshooting

**Not finding X profiles for some LinkedIn leads?** This is expected. Not every professional maintains an active X account.

**A match looks incorrect?** Low-confidence matches are filtered out automatically, but occasional false positives can occur with common names. You can manually update the lead record.

## Next Steps

- **[Enrichment Pipeline](../enrichment/pipeline.md)**: How matched profiles flow through enrichment and scoring
- **[How Leads Work](../core-concepts/leads.md)**: Unified lead profiles across platforms
