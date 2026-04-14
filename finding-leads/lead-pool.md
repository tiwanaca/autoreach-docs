# Lead Pool (Instant Matching)

Discover qualified prospects by matching your offer's ICP against a global pool of pre-enriched lead profiles using vector similarity search. Lead Pool delivers results in seconds because the profiles are already enriched — only scoring needs to run.

## What Is the Lead Pool?

The Lead Pool is a **global, cross-user** database of enriched lead profiles stored as vector embeddings. Every lead enriched through AutoReach has their profile embedded and added to the pool. When you create or update an offer, AutoReach generates an embedding of your ICP and runs a cosine similarity search against the entire pool to find the best matches.

Unlike keyword-based filtering, semantic matching understands the meaning behind your offer description. A lead whose profile is conceptually aligned with your target audience will surface even if they do not share exact keywords with your search criteria.

## How It Works

### 1. Profile Embedding

When any lead completes the enrichment pipeline (completes enrichment), their profile is embedded and stored. The embedding captures the lead's professional identity as a vector representation.

**What gets embedded per lead:**
- Headline / role
- Bio
- Industry
- Company name and employee count
- Location
- Top 10 LinkedIn skills
- LinkedIn summary (truncated to 200 characters)

Each embedding also stores metadata including platform identifiers, industry, location, company size, and available platforms for filtering.

### 2. ICP Embedding

When matching triggers, your offer's ICP is embedded separately. The ICP embedding is built from:
- Target audience definition
- Industry names (resolved from LinkedIn industry IDs)
- Preferred locations

The ICP embedding focuses on who the buyer is, not what you're selling.

### 3. Similarity Matching

A cosine similarity search finds the closest matches:
- **Similarity threshold:** 0.25 (minimum match score)
- **Default limit:** 100 candidates per run
- **Deduplication:** Leads the user already has are automatically excluded. A unique constraint prevents duplicate cloning.

### 4. Lead Creation

Matched profiles are **cloned** as new leads with:
- Source marked as "Lead Pool"
- All scoring fields reset (fresh scoring needed)
- Pipeline status set to pending

A scoring-only pipeline job is queued — enrichment is skipped because the profile data is already available, but buyer intelligence scoring runs fresh against your specific offer.

## When Does It Trigger?

Lead Pool matching fires automatically in several scenarios:

| Trigger | When It Fires |
|---------|---------------|
| **New offer created** | When you create a new offer |
| **Search finishes** | When any search completes: X tweet search, LinkedIn content search, LinkedIn seed search, or link extraction |
| **Follower extraction starts** | When a follower extraction begins |

Note: Updating an existing offer re-embeds the ICP but does not automatically trigger a pool match job — only offer creation does.

## Cost

Lead Pool matching is **not zero-cost**. Two cost components:

1. **Embedding generation:** Each match run generates a vector embedding of your offer's ICP. Profile embeddings are created once during enrichment.
2. **AI scoring:** Every matched lead is queued for deep analysis scoring, which uses your configured AI models. This is the primary cost.

The platform API cost (Twitter/LinkedIn calls) is zero because leads are already enriched, but AI costs apply.

## Search Parameters

| Parameter | Default | Description |
|---|---|---|
| Max candidates | 100 | Maximum matches to return per run |
| Platforms | -- | Optional filter: X only, LinkedIn only, or both |
| Similarity threshold | 0.25 | Minimum cosine similarity score |

By default, all platforms are matched unless you explicitly filter to X-only or LinkedIn-only leads.

## Existing Lead Rescoring

In addition to cloning new leads from the pool, the matching process also checks your existing leads that may match a different offer. These are rescored against the new offer without cloning.

The total across cloned + rescored leads never exceeds the max candidates limit.

## Getting Started

### Prerequisites

You need an existing base of enriched leads in the global pool. Build one through any discovery method:

- [X Tweet Search](tweet-search.md)
- [LinkedIn Content Search](linkedin-content-search.md)
- [LinkedIn People Search](linkedin-people-search.md)
- [Lookalike Audiences](lookalike-audiences.md)

### Initial Setup

1. **Create your offer** with a clear target audience, industries, and preferred locations.
2. **Run your first discovery search** using any method above.
3. **Wait for enrichment to complete.** Embeddings are generated at the end of the enrichment pipeline.
4. **Lead Pool matching triggers automatically** on offer creation and after searches complete.

### Continuous Scaling

- Every new search triggers pool matching against the growing pool of enriched leads.
- Your pool grows with every user's enrichment, making future matching more powerful.

## Best Practices

1. **Build the database first.** Lead Pool is most effective with a large base of enriched leads. Start with discovery searches before relying on pool matching.

2. **Write detailed target audience definitions.** The ICP embedding is built from your target audience, industries, and locations — not your offer description. Be specific in those fields.

4. **Monitor match quality.** Track response rates from Lead Pool matches and compare them to other discovery methods.

5. **Refresh your offer periodically.** When your target market shifts, update your offer fields to change the ICP embedding. Creating a new offer triggers a fresh pool match automatically.

6. **Combine with other methods.** Use Lead Pool for rapid scaling while continuing X and LinkedIn searches for fresh intent signals.

## Troubleshooting

**Not getting any matches?**
- Confirm that enriched leads exist in the pool (from your own or other users' searches).
- Check that the enrichment pipeline has finished processing for recent searches.
- Try creating a new offer or running a search to trigger a pool match.
- Review your offer's target audience, industries, and locations — these drive the ICP embedding.

**Match quality seems low?**
- Review your target audience definition. Vague or overly broad descriptions produce weaker matches.
- Remember: the ICP embedding uses your target audience, industries, and locations — not your offer description or pain points.

**Getting too many irrelevant matches?**
- Tighten your target audience and preferred locations.
- Use platform filtering to focus on X-only or LinkedIn-only leads.
- Lower the max candidates limit.

## Next Steps

- [Create or refine your offer](../getting-started/create-offer.md) to improve match accuracy.
- [Run an X Tweet Search](tweet-search.md) to start building the enriched lead pool.
- [Set up a LinkedIn People Search](linkedin-people-search.md) for systematic lead generation.
- [Explore Lookalike Audiences](lookalike-audiences.md) to expand from your best-performing leads.
