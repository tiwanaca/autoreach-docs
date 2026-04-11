# RAG Lead Pool (Instant Matching)

Instantly match new prospects against your database of previously enriched leads using vector search. Get qualified prospects without additional enrichment costs.

## How It Works

The Lead Pool uses semantic vector search to instantly identify prospects matching your ICP:

### 1. Offer Vector Embedding

When you create or update an offer, AutoReach:
- Builds a comprehensive profile from your offer description
- Includes pain points, target audience, and search signals
- Converts this profile into a 1536-dimensional vector using **OpenAI text-embedding-3-small**
- Stores the embedding for comparison against lead profiles

### 2. Vector Database Storage

All previously enriched leads have their profiles stored as vectors in **pgvector**:
- **Fast lookup:** Queries return matching leads instantly
- **Semantic matching:** Finds conceptually similar prospects, not just keyword matches
- **Scalable:** Works efficiently with millions of leads

### 3. Lead Profile Vectors

Each lead's profile vector is built from:

- **Headline:** Current job title and role
- **Bio:** Twitter/X bio or LinkedIn headline
- **Industry:** Company industry classification
- **Company:** Company name and type
- **Location:** Geographic location
- **Skills:** Professional skills and competencies
- **Summary:** Generated profile summary
- **Education:** Educational background and relevant degrees
- **Notable Roles:** Previous significant job titles

This rich profile ensures accurate semantic matching.

### 4. Vector Search and Similarity Matching

The matching process:
1. Embeds your offer description into vector space
2. Performs **cosine similarity** search against all lead vectors
3. Returns leads ranked by match similarity
4. Automatically clones top matches into your lead database
5. Queues matched prospects for buyer intent scoring

## Trigger Sources

Lead Pool matching is automatically triggered by:

| Trigger | When It Fires |
|---------|---------------|
| **offer_update** | You update your offer description or pain points |
| **search_complete** | After any lead search completes (Tweet, Content, People, Job) |
| **target_user_extraction** | When leads are extracted from a search result set |
| **manual** | You manually trigger pool matching |

## Cost Efficiency

Unlike other discovery methods that require API calls and enrichment:

- **No platform API calls** for profile scraping
- **No enrichment costs** (leads already enriched)
- **Instant results** (vector search is millisecond-fast)
- **Unlimited matching** (search as many times as you want)

This makes Lead Pool ideal for rapidly scaling once you have an enriched lead database.

## Vector Search Tuning

Our search parameters are tuned for B2B SaaS precision:

- **Embedding model:** OpenAI text-embedding-3-small (proven B2B accuracy)
- **Vector dimensions:** 1536 (balanced precision/performance)
- **Similarity metric:** Cosine similarity (standard for semantic search)
- **Minimum threshold:** Configurable similarity cutoff (default: top 500 matches)

## Getting Started with Lead Pool

### Prerequisites
You need an enriched lead database. Build this through:
- [Tweet Search](tweet-search.md)
- [LinkedIn Content Search](linkedin-content-search.md)
- [LinkedIn People Search](linkedin-people-search.md)
- [Lookalike Audiences](lookalike-audiences.md)

### Initial Setup
1. Create your offer with clear pain points and target audience
2. Run your first discovery search (any method above)
3. AutoReach automatically enqueues leads for enrichment
4. Lead Pool automatically starts matching once enrichment completes

### Continuous Scaling
After initial enrichment:
- Each new offer update triggers fresh Lead Pool matching
- Each new search automatically gets pool-matched
- You continuously discover matches without additional platform API costs

## Example Workflow

**Scenario:** You run an HR analytics platform and have enriched 50,000 HR professionals from your initial searches.

**Now you want to scale:**
1. A new VP of People Operations takes a job at TechCorp
2. They get added to the lead pool (from LinkedIn or Tweet Search)
3. Enrichment completes
4. Lead Pool matches them against your 50,000 existing leads
5. Semantic search identifies them as highly similar to other successful prospects
6. They're automatically added to your outreach queue with high ICP score

**Result:** You found a new prospect instantly, at zero API cost, without any new search work.

## Best Practices

1. **Build your initial lead database first:** Lead Pool is most powerful with an enriched database of 10,000+ leads.

2. **Refine your offer description:** More detailed pain points and target audience = better vector matches.

3. **Use search signals:** Natural language search signals improve semantic matching significantly.

4. **Monitor match quality:** Track response rates from Lead Pool matches. They should be competitive with other discovery methods.

5. **Update your offer periodically:** When your offer or target market evolves, update it to trigger fresh Lead Pool matching.

6. **Combine with other methods:** Use Lead Pool for scaling while continuing to do content/Twitter searches for fresh signal discovery.

7. **Review filtering:** Set similarity thresholds appropriately—higher thresholds get fewer but higher-quality matches.

## Lead Pool vs. Other Methods

| Method | Initial Setup | Cost Per Search | Speed | Best For |
|--------|---------------|-----------------|-------|----------|
| **Lead Pool** | Requires enriched leads | Zero API cost | Instant | Rapid scaling with existing DB |
| **Tweet Search** | None | Low API cost | Fast | Fresh intent signals |
| **Content Search** | None | Low API cost | Medium | Engaged professionals |
| **People Search** | None | Low API cost | Medium | Systematic targeting |
| **Lookalike** | None | Low API cost | Medium | Audience-based scaling |

## Troubleshooting

**Not getting Lead Pool matches?**
- Verify you have an enriched lead database with 1,000+ prospects
- Check that enrichment pipeline has completed
- Try updating your offer to trigger new matching

**Match quality seems low?**
- Review your offer description—it may be too generic
- Add more specific pain points and search signals
- Check if your target audience characteristics match your database

**Getting many irrelevant matches?**
- Tighten your ICP definition (pain points, audience, search signals)
- Lower the similarity threshold to only get high-confidence matches
- Combine with content search for fresh, high-intent signals

**How long until I can use Lead Pool?**
- Usually 30 minutes after your first lead discovery search
- Depends on enrichment pipeline speed
- Automatic triggers fire once enrichment completes

## Advanced Strategies

**Offer Variation Testing:**
- Create variation offers with different pain point emphasis
- Each triggers fresh Lead Pool matching
- Compare which offer variation finds highest-quality matches
- Optimize your messaging based on what matches best

**Lead Pool + Lookalike Hybrid:**
- Use Lookalike Audiences to find new seed accounts
- These prospects get enriched and added to your database
- Lead Pool then finds similar prospects across your full database
- Combines audience discovery with semantic matching for rapid scaling
