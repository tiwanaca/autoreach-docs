# Finding Leads Overview

AutoReach provides multiple lead discovery methods to help you find prospects that match your ideal customer profile (ICP). Methods range from intent-driven social searches to follower extraction and instant pool matching.

## Search-Based Discovery

These methods find leads through keyword and filter-based searches.

### X Tweet Search
Find prospects from intent-signaling posts on X. AutoReach can analyze your offer and auto-generate targeted search queries organized by intent category (budget pressure, operational pain, competitor switching, hiring/scaling, etc.), or you can provide your own keywords. Both tweet authors and commenters are captured as leads.

Supports **daily recurring searches** — AutoReach regenerates fresh keywords and re-runs searches every 24 hours automatically.

**Best for:** Finding leads showing active buying signals on X.

[Learn more about X Tweet Search →](tweet-search.md)

### LinkedIn Content Search
Discover decision-makers through LinkedIn posts and comments. Both post authors and commenters are captured by default (`include_commenters` is on).

Supports **daily recurring searches** with auto-regenerated queries.

**Best for:** Finding engaged LinkedIn users with professional signal strength.

[Learn more about LinkedIn Content Search →](linkedin-content-search.md)

### LinkedIn People Search
Direct profile discovery using LinkedIn's search API. Available filters:

- **Location** (geo URNs)
- **Industry**
- **Current company**
- **Job title** (keyword)
- **Network** (1st/2nd/3rd+ connections)
- **Profile language**
- **Follower of** (specific profile URNs — used by lookalike-driven searches)

Note: company size is not a direct LinkedIn People Search filter. It is part of your offer's ICP definition and checked during scoring, not at search time.

Supports **buyer expansion** — a daily autopilot that re-runs people searches with role rotation to continuously find new leads.

**Best for:** Systematic targeting of specific roles at specific companies.

[Learn more about LinkedIn People Search →](linkedin-people-search.md)

### LinkedIn Job Search
Find decision-makers at companies that are actively hiring. The flow:

1. AI generates role targets based on your offer
2. Searches LinkedIn job postings for each role
3. Deduplicates by company
4. Fetches full company profiles (industry, size, headquarters, etc.)
5. Runs a people search within each company to find a decision-maker by seniority scoring (CEO/CTO/Founder score highest)

The system finds the most senior relevant decision-maker at the company, not necessarily the person who posted the job.

**Best for:** Targeting growth-stage companies and their decision-makers.

[Learn more about LinkedIn Job Search →](linkedin-job-search.md)

### Keyword Generation
AI generates targeted search queries tailored to your offer for both X and LinkedIn. For X, this includes both keywords and intent-organized query clusters. For LinkedIn, it generates content search queries.

Keyword generation is both a standalone preview tool and the engine behind daily recurring searches — each recurring run regenerates fresh keywords automatically.

**Best for:** Discovering relevant search terms you might not think of yourself.

[Learn more about Keyword Generation →](keyword-generation.md)

## Audience-Based Discovery

These methods find leads by extracting followers or audiences from relevant accounts.

### Lookalike Audience Discovery
AutoReach uses AI to find influencers, thought leaders, and communities whose audiences match your ICP. The lookalike search works on both X and LinkedIn. However, the downstream lead extraction differs by platform:

- **X:** Followers are extracted directly via the follower extraction pipeline
- **LinkedIn:** Leads are found via People Search filtered by `followerOf` the discovered account's profile URN

**Best for:** Scaling outreach by tapping into existing relevant communities.

[Learn more about Lookalike Audiences →](lookalike-audiences.md)

### Follower/Following Extraction
Extract followers or following lists from specific X accounts you choose as seed accounts. You specify a username, choose followers or following, and set a max count. AutoReach paginates through the list and scores each person against your offer.

Supports **buyer expansion** — a daily autopilot that re-extracts from seed accounts to capture new followers.

**Best for:** Mining the audience of specific industry accounts, newsletters, or competitors on X.

### Link Extraction
Extract leads from specific URLs — either profile links or comment sections. Supports four extraction types:

- X comments (from a tweet URL)
- X profiles (from a thread or list)
- LinkedIn comments (from a post URL)
- LinkedIn profiles (from a post or article)

**Best for:** Capturing engaged audiences from specific high-signal posts or threads.

### Comment Extraction
When a search finds a high-signal post, AutoReach can also extract the commenters as leads. This happens automatically during X Tweet Search and LinkedIn Content Search when commenters are included, and can also be triggered via Link Extraction on specific post URLs.

## Instant & Manual Methods

### Lead Pool (Instant Matching)
AutoReach maintains a shared pool of pre-enriched lead profiles with vector embeddings. When you create or update an offer, the system uses cosine similarity search to match existing pool entries against your ICP. Pool entries are platform-agnostic — they can originate from X, LinkedIn, or both.

The pool is triggered automatically at search start and on offer updates, as well as manually.

**Best for:** Getting scored leads instantly without waiting for enrichment.

[Learn more about Lead Pool →](lead-pool.md)

### CSV Import
Bulk import leads from a spreadsheet with X handle, LinkedIn URL, or email. Includes duplicate detection and queues imported leads for full enrichment.

**Best for:** Bringing in existing prospect lists from other tools or sources.

### Manual Add
Add individual leads by URL or username. Queued for enrichment and scoring.

### Chrome Extension
On LinkedIn, click the **Add to Leads** button on any profile page to add them directly via the AutoReach Chrome Extension.

## Automated Discovery (Buyer Expansion)

The **buyer expansion scheduler** is a background autopilot that runs daily to continuously grow your lead pipeline. When enabled on a search or seed account, it:

- Re-runs X follower extractions on seed accounts to capture new followers
- Re-runs LinkedIn people searches with role rotation to find new matches
- Triggers automatically — no manual intervention needed after initial setup

## Cross-Platform Profile Matching

Cross-platform matching (finding X profiles for LinkedIn leads and vice versa) is **not a standalone discovery method**. It runs automatically during the enrichment pipeline when a lead enters from any source. See [Cross-Platform Matching](cross-platform-matching.md) for details on how it works.

## Managing Your Leads

Once leads are in your pipeline, AutoReach provides tools to organize, export, import, and clean up your lead data.

### CSV Export

Select leads from your pipeline and export them as a CSV file. You can export up to 50,000 leads at once. The export includes profile information, scores, contact details, source data, and enrichment results. Use filters to narrow down which leads to include before exporting.

### CSV Import

Upload a CSV file containing X handles, LinkedIn URLs, or email addresses to bulk-import leads. AutoReach previews the import before processing, showing you how many leads will be added and flagging any duplicates already in your pipeline. You can choose to skip duplicates or import them anyway. Imported leads are automatically queued for enrichment and scoring.

### Lead Pool Matching

The Lead Pool contains pre-enriched profiles that are shared across the platform. When you create a new offer or run a search, AutoReach automatically checks the pool for leads that match your ICP using vector similarity. Matching leads are imported into your pipeline instantly with scores already calculated — no waiting for enrichment.

## Choosing the Right Method

| Method | Platform | Best For |
|--------|----------|----------|
| X Tweet Search | X | Intent signals from active discussions |
| LinkedIn Content Search | LinkedIn | Professionals discussing relevant topics |
| LinkedIn People Search | LinkedIn | Systematic targeting by role/location/industry |
| LinkedIn Job Search | LinkedIn | Growth-stage companies and decision-makers |
| Lookalike Audiences | Both | Scaling via relevant community audiences |
| Follower Extraction | X | Mining specific account audiences |
| Link/Comment Extraction | Both | Capturing engagement on specific posts |
| Lead Pool | Both | Instant matches from pre-enriched profiles |
| CSV Import | Both | Bringing in external prospect lists |

## Quick Start

1. **Starting with a new offer?** Begin with [X Tweet Search](tweet-search.md) or [LinkedIn Content Search](linkedin-content-search.md) to find intent-driven prospects.

2. **Have specific role/location targets?** Use [LinkedIn People Search](linkedin-people-search.md) for precise filtering.

3. **Want to scale quickly?** Try [Lookalike Audiences](lookalike-audiences.md) to find entire communities of relevant prospects.

4. **Need fast results?** Use [Lead Pool](lead-pool.md) to instantly match against existing enriched leads.

5. **Want continuous growth?** Enable **buyer expansion** on your searches and seed accounts for daily autopilot discovery.

> **Note:** All lead discovery methods automatically score new prospects against your offer for fit, intent, and timing before they appear in your pipeline.

> **Warning:** Lead quality depends on accurate ICP definition. Spend time setting up your offer with clear pain points, target audience, and search signals for best results.
