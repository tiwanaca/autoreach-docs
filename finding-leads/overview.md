# Finding Leads Overview

AutoReach provides multiple lead discovery methods across X and LinkedIn. Access them from the **Leads** page, which has four tabs:

- **All**-  Every lead discovered across all your sources
- **Signals**-  Leads found from intent signal searches, scored and ranked in real time
- **Sources**-  Extractions from lookalike accounts, link extractions, and CSV imports
- **Lookalikes**-  Manage your saved lookalike accounts

To add new leads, click **Add Lead** on the Leads page. You'll choose a platform (X or LinkedIn), select an account and offer, then pick a discovery method.

## X Discovery Methods

When you select X, four options appear:

### From a Lookalike

Extract followers or following from a specific X account. You provide a target username, choose followers or following, and set a max count. AutoReach paginates through the list and scores each person against your offer.

Enable **Buyer Expansion** to automatically re-extract from seed accounts daily to capture new followers.

**Best for:** Mining the audience of industry accounts, newsletters, or competitors on X.

### From Signals (Intent Stream)

Search X for people discussing problems your offer solves. AutoReach generates targeted search queries from your offer, or you can provide your own keywords. Both tweet authors and commenters are captured as leads.

Advanced settings let you configure max tweets, days back, whether to include replies, and max replies per tweet.

Enable **Buyer Expansion** to automatically re-run this search every 24 hours with fresh keywords.

**Best for:** Finding leads showing active buying signals on X.

[Learn more about X Tweet Search →](tweet-search.md)

### From a Link

Extract leads from a specific X post or search URL. Two modes:

- **Post Comments**-  Extract people who commented on a specific tweet
- **Search Profiles**-  Extract profiles from a search results URL

**Best for:** Capturing engaged audiences from specific high-signal posts or threads.

### Add Manually

Add a lead by their X username. The lead is queued for enrichment and scoring.

## LinkedIn Discovery Methods

When you select LinkedIn, six options appear:

### From a Lookalike

Search for people similar to a lookalike account on LinkedIn. This uses LinkedIn People Search filtered to followers of the target account.

**Best for:** Scaling outreach by tapping into relevant professional communities.

### By Role

Search LinkedIn for people by job title in your offer's target locations. Uses your offer's preferred locations and industries to filter results. Select a role from AI-generated role suggestions, and set a max result count.

Enable **Buyer Expansion** to automatically rotate through different roles daily and continuously find new leads.

**Best for:** Systematic targeting by role, location, and industry. To target specific companies, use **By Company** instead.

[Learn more about LinkedIn People Search →](linkedin-people-search.md)

### By Company

Search for companies matching descriptors like "B2B SaaS Sales Tooling" or "Lead Generation Agency", then add the top decision-maker from each as a lead. AI can generate descriptors from your offer, or you can enter your own.

Enable **Buyer Expansion** to re-run each descriptor daily and capture new companies as they appear.

**Best for:** When you know the *type* of company you want to reach but not the people yet. Returns one focused lead per company instead of many.

[Learn more about LinkedIn Company Search →](linkedin-company-search.md)

### From Signals (Intent Stream)

Search LinkedIn posts and comments for intent signals. AutoReach shows which buying signals are active for your offer and generates queries accordingly. Both post authors and commenters are captured by default.

Advanced settings include:

- **Posts per search query**-  How many posts to analyze per query
- **Search period**-  Past 24 hours, past week, past month, or any time
- **Max comments per post**-  How many commenters to extract per post
- **Include commenters**-  Toggle commenter extraction on/off
- **Feed search**-  Also search your LinkedIn feed for signals
- **Hiring signals**-  Configure Max Jobs per Role and Max Companies to find decision-makers at companies that are actively hiring

Enable **Buyer Expansion** to automatically re-run this search every 24 hours.

**Best for:** Finding engaged LinkedIn users with professional signal strength.

[Learn more about LinkedIn Content Search →](linkedin-content-search.md)

### From a Link

Extract leads from a specific LinkedIn post or search URL. Two modes:

- **Post Comments**-  Extract people who commented on a specific post
- **Search Profiles**-  Extract profiles from a search results URL

**Best for:** Capturing engaged audiences from specific high-signal LinkedIn posts.

### Add Manually

Add a lead by their LinkedIn profile URL or vanity name. The lead is queued for enrichment and scoring.

## Lookalike Account Discovery

From the **Lookalikes** tab, click **New Lookalike** to discover relevant accounts. Two search methods:

- **By Offer**-  AutoReach uses your offer's target audience to find influencers, thought leaders, and communities whose audiences match your ICP
- **By Profile URL**-  Provide a specific influencer or competitor profile URL

The search returns up to 10 candidate accounts with follower counts and audience categories. Select which to save, then use them as seed accounts for extraction via the "From a Lookalike" option.

Works on both X and LinkedIn.

[Learn more about Lookalike Audiences →](lookalike-audiences.md)

## Lead Pool (Instant Matching)

AutoReach maintains a shared pool of pre-enriched lead profiles with vector embeddings. When you create or update an offer, the system automatically matches existing pool entries against your ICP. Matching leads appear in your pipeline instantly-  no waiting for enrichment.

The Lead Pool is fully automatic. You can see pool-sourced leads by filtering the All tab by "Pool DB" source.

**Best for:** Getting scored leads instantly without waiting for enrichment.

[Learn more about Lead Pool →](lead-pool.md)

## CSV Import

Click **Import Leads** on the Leads page to bulk-import leads from a CSV file. Upload your file, preview the results (including duplicate detection), select accounts for enrichment, and confirm. AutoReach supports X handles, LinkedIn URLs, and email addresses. Imported leads are automatically queued for enrichment and scoring.

## CSV Export

Select leads from the All tab and export them as a CSV file. The export includes profile information, scores, contact details, source data, and enrichment results. Use filters to narrow down which leads to include before exporting.

## Cross-Platform Profile Matching

Cross-platform matching (finding X profiles for LinkedIn leads and vice versa) is a **manual action**, not an automatic pipeline step. Select leads, click Enrich, and enable "Find LinkedIn" or "Find X Profile" under Profile Discovery. See [Lead Pool](lead-pool.md) for details.

## Choosing the Right Method

| Method | Platform | Best For |
|--------|----------|----------|
| From a Lookalike | Both | Scaling via relevant community audiences |
| By Role | LinkedIn | Systematic targeting by role/location/industry |
| By Company | LinkedIn | One decision-maker per matching company |
| From Signals | Both | Intent signals from active discussions |
| From a Link | Both | Capturing engagement on specific posts |
| Add Manually | Both | Adding individual prospects |
| Lookalike Discovery | Both | Finding relevant accounts to extract from |
| Lead Pool | Both | Instant matches from pre-enriched profiles |
| CSV Import | Both | Bringing in external prospect lists |

## Quick Start

1. **Starting fresh?** Click **Add Lead**, choose a platform, and select **From Signals** to find intent-driven prospects.

2. **Have specific role/location targets?** Use **By Role** (LinkedIn) for precise filtering.

3. **Want to scale quickly?** Discover **Lookalike** accounts, then extract their followers.

4. **Need fast results?** Create an offer and let the **Lead Pool** instantly match pre-enriched leads.

5. **Want continuous growth?** Enable **Buyer Expansion** on your searches and extractions for daily autopilot discovery.

> **Note:** All lead discovery methods automatically score new prospects against your offer for fit, intent, and timing before they appear in your pipeline.

> **Warning:** Lead quality depends on accurate ICP definition. Spend time setting up your offer with clear pain points and target audience for best results.
