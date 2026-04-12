# How Leads Work

A **lead** in AutoReach is a unified profile of a potential buyer that combines data from both X and LinkedIn. Leads are automatically discovered, enriched, scored, and tracked throughout the entire outreach lifecycle.

## What Is a Lead?

A lead represents one person across one or both platforms. AutoReach automatically matches X profiles with LinkedIn profiles to create a unified view, giving you:

* **Social presence** across both platforms
* **Professional history** (education, experience, skills)
* **Company and role** information
* **Recent activity** and engagement patterns
* **Intent and fit signals** extracted from content
* **Buyer score** predicting purchase probability

## Where Do Leads Come From?

AutoReach discovers leads through several different sources:

### 1. Tweet Search

Search for keywords on X using natural language. AutoReach finds tweets matching your keywords and enrolls the authors as leads.

**Example:** Search for "looking for workflow automation tool" finds people actively discussing this problem.

### 2. LinkedIn Search

Powerful LinkedIn search across content, people, and job changes.

* **Content search:** Find people posting about keywords (hiring, switching to competitor, etc.)
* **People search (By Role):** Target by job title, company, location, industry, or custom fields
* **Job search:** Find people who recently started a new role

### 3. Lookalike Audiences

AutoReach uses AI to find influencers, thought leaders, publications, and communities whose followers match your ideal customer profile. It then extracts followers from those accounts and scores them against your ICP.

You do not upload a list. AutoReach discovers the right seed accounts automatically based on your offer definition.

**Example:** If you sell to B2B SaaS leaders, AutoReach might find an industry newsletter whose followers include VPs of Sales and Directors of Revenue Operations. It extracts those followers and scores them as leads.

### 4. Follower Extraction

Extract followers from specific X accounts or LinkedIn profiles you choose as seed accounts. AutoReach processes the followers and scores them against your offer.

### 5. Link Extraction

AutoReach extracts profile links found during searches and other discovery methods. These are processed and added as leads.

### 6. Lead Pool

AutoReach maintains a shared lead pool of pre-enriched profiles. When you create or update an offer, the system uses vector embeddings to match existing leads against your ICP. This is the fastest way to get scored leads because they skip enrichment entirely.

### 7. Chrome Extension

On LinkedIn, you can click the **Add to Leads** button on any profile page to add them directly to your CRM via the Chrome Extension.

### 8. Manual Add

Add individual leads manually by URL or username.

### 9. CSV Import

Bulk import leads from a spreadsheet with X handle, LinkedIn URL, or email.

{% hint style="info" %}
**Lead Sources and Speed:** Lead pool matches are instant because they are pre-enriched. Intent-based sources (Tweet Search, LinkedIn Content Search) are next fastest. CSV imports take longest because they need full enrichment from scratch.
{% endhint %}

## Lead Enrichment

When a lead enters AutoReach, it goes through automatic enrichment in the background:

1. **Profile discovery:** Find the lead's X and LinkedIn profiles (cross-platform matching)
2. **Profile enrichment:** Extract bio, headline, experience, education, skills, and company data
3. **Activity enrichment:** Fetch recent posts, engagement patterns, and social activity
4. **Location enrichment:** Resolve company HQ and lead location
5. **Scoring:** Run Buyer Intelligence to calculate fit, intent, and timing scores

As each stage completes, the lead's profile gets richer. You can view partial data during enrichment, but full Buyer Intelligence scores only generate after all enrichment stages finish.

{% hint style="warning" %}
**Enrichment Speed Varies:** X and LinkedIn rate limiting can affect enrichment speed. Large batches may take time to fully enrich.
{% endhint %}

## Lead States

Every lead has a buyer state that determines where it appears in the UI and whether it is eligible for outreach:

| State | Condition | Where It Appears |
| --- | --- | --- |
| **Active** | Buyer Score >= 60 | Buyers page |
| **Monitor** | Buyer Score 30-59 | All Leads page |
| **Poor Fit** | Buyer Score < 30 | All Leads page |
| **Disqualified** | Very low fit and intent | Removed from database |
| **Not Scored** | Enrichment not complete | All Leads page |
| **Manual Outreach** | User override | Treated as Active |

See [Buyer States](buyer-states.md) for full details on each state and how transitions work.

## Cross-Platform Profile Matching

When you add a lead from one platform, AutoReach automatically searches for their profile on the other. This cross-platform data makes enrichment and scoring far more accurate than single-platform data alone.

## Lead Profile Data

Each lead's profile includes:

### Basic Info

* Name, headline, bio
* X and LinkedIn URLs
* Email (if found via web enrichment)
* Location (city, state, country)
* Company and job title

### Professional Background

* Education (school, degree, field, dates)
* Work experience (company, role, tenure, description)
* Skills (extracted from profiles)

### Social Activity

* Recent posts and engagement
* LinkedIn post activity
* Follower/following counts

### Signals and Scoring

* All detected intent signals (with dates and strength)
* Company-level signals
* Buyer state (active/monitor/poor_fit/disqualified)
* Buyer score, fit score, intent score, timing score

## Lead Lifecycle in a Sequence

Once enrolled in a sequence, a lead progresses through these statuses:

| Status | Meaning |
| --- | --- |
| **Pending** | Enrolled but not yet started |
| **Active** | Currently progressing through sequence steps |
| **Paused** | Manually paused mid-sequence |
| **Replied** | Lead replied to a message |
| **Meeting Booked** | Meeting scheduled |
| **Completed** | Finished all sequence steps |
| **Failed** | Error during execution (invalid profile, rate limit) |
| **Removed** | Manually removed from the sequence |

## Best Practices

{% hint style="info" %}
**Quality Over Quantity:** 100 highly-scored leads from LinkedIn search will outperform 1,000 random CSV imports. Focus on signal-rich sources first.
{% endhint %}

{% hint style="info" %}
**Use the Lead Pool:** If you are just getting started, the lead pool gives you scored leads instantly without waiting for enrichment.
{% endhint %}

{% hint style="info" %}
**Monitor Lower Scores:** Do not ignore poor_fit leads entirely. Re-scoring happens when new signals are detected. A lead could jump from 25 to 65 based on a job change or new social activity.
{% endhint %}

## Next Steps

* [**Buyer Intelligence & Scoring**](buyer-scoring.md): Learn how AutoReach scores leads across fit, intent, and timing
* [**Finding Leads Overview**](../finding-leads/overview.md): Explore all the ways to discover new leads
