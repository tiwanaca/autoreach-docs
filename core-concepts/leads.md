# How Leads Work

A **lead** in AutoReach is a unified profile of a potential buyer that combines data from both X/Twitter and LinkedIn. Unlike manual lists, leads are intelligent entities that get automatically discovered, enriched, scored, and tracked throughout the entire outreach lifecycle.

## What Is a Lead?

A lead represents one person across one or both platforms. AutoReach automatically matches X profiles with LinkedIn profiles to create a unified view, giving you:

- **Social presence** across both platforms
- **Professional history** (education, experience, skills)
- **Company and role** information
- **Recent activity** and engagement patterns
- **Intent and fit signals** extracted from content
- **Buyer score** predicting purchase probability

Think of a lead as a 360-degree profile: not just a name and email, but a complete picture of who they are, what they do, and whether they're likely to buy.

## Where Do Leads Come From?

AutoReach discovers leads through seven different sources, each with different discovery speed and quality characteristics:

### 1. Tweet Search (Intent/Fast Track)

Search for keywords on X using natural language. AutoReach finds tweets matching your keywords and enrolls the authors as leads.

**Example:** Search for "looking for workflow automation tool" finds people actively discussing this problem.

### 2. LinkedIn Search (Intent/Fast Track)

Powerful LinkedIn search across content, people, and job changes.

- **Content search:** Find people posting about keywords (hiring, switching to competitor, etc.)
- **People search:** Target by job title, company, location, skills, or custom fields
- **Job search:** Find people who recently started a new role (first 6 months)

### 3. Lookalike Audiences

Upload a customer CSV and let AutoReach find similar profiles on LinkedIn.

### 4. Follower Extraction (Lower Priority)

Extract followers from X accounts you specify and enroll them as leads.

### 5. Manual Add

Add individual leads manually by URL or username.

### 6. CSV Import (Lowest Priority)

Bulk import leads from a spreadsheet with X handle, LinkedIn URL, or email.

### 7. Lead Pool and RAG Matching

AutoReach's internal matching system finds leads from expanded audiences using Retrieval-Augmented Generation (RAG) with your Offer definition.

{% hint style="info" %}
**Lead Sources and Speed:** Intent-based sources (Tweet Search, LinkedIn Content Search) move leads through enrichment fastest. CSV imports take longest because they skip the initial X/LinkedIn discovery step.
{% endhint %}

## Lead Enrichment Pipeline

When a lead enters AutoReach, it travels through a sophisticated enrichment pipeline:

```
1. x_find              → Discover X profile (if not provided)
2. x_enrichment        → Extract X profile data (bio, followers, posts)
3. linkedin_find       → Match LinkedIn profile to X profile
4. linkedin_enrichment → Extract LinkedIn profile data (experience, education, skills)
5. activity_fetch      → Get recent posts, activity, engagement patterns
6. location_enrichment → Enrich location data (company HQ, lead location)
7. scoring             → Run Buyer Intelligence (fit, intent, timing)
```

Lead enrichment happens asynchronously in the background. As each stage completes, the lead's profile gets richer. You can view partial data during enrichment, but full Buyer Intelligence scores only generate after all enrichment stages finish.

{% hint style="warning" %}
**Enrichment Speed Varies:** X and LinkedIn rate limiting can slow enrichment. Large batches of CSV imports may take 24-48 hours to fully enrich.
{% endhint %}

## Lead States

Every lead moves through a state machine that determines its buyer status and where it appears in the UI:

### not_scored

A newly added lead that hasn't completed enrichment or initial scoring yet. No Buyer Intelligence data is available.

### active

**Buyer Score >= 60.** This lead is ready to buy. Appears on the **Buyers** page and is eligible for immediate sequence enrollment.

### monitor

**Buyer Score 30-59.** This lead has moderate fit or intent but isn't ready yet. Appears on the **All Leads** page. AutoReach continuously monitors for new signals that might trigger promotion to **active**.

### poor_fit

**Buyer Score < 30.** This lead is a weak match for your offer. Tracked but deprioritized. Can still be enrolled in sequences manually if you want to experiment.

### disqualified

**Both fit_score < 15 AND intent_score < 15.** AutoReach automatically removes these leads from your database (they are permanently disqualified as a bad fit).

### manual_outreach

A lead you manually override for outreach regardless of their score. Useful for VIP leads, strategic accounts, or testing sequences on lower-scoring prospects.

## Cross-Platform Profile Matching

AutoReach's magic happens at the intersection of X and LinkedIn. When you add a lead from one platform, AutoReach automatically searches for their profile on the other.

**Example:** You search for "moving from Salesforce to HubSpot" on LinkedIn and find Alice. AutoReach automatically finds Alice's X profile (@alice_tweets), looks up her recent tweets, checks for mentions of Salesforce/HubSpot, and uses that social activity as an additional intent signal.

This cross-platform matching makes lead enrichment far more accurate than single-platform data alone.

## Lead Profile Data

Each lead's profile includes:

### Basic Info

- Name, headline, bio
- X and LinkedIn URLs
- Email (if found)
- Location (city, state, country)
- Company and job title

### Professional Background

- Education (school, degree, field, dates)
- Work experience (company, role, tenure, description)
- Skills (extracted from profiles)

### Social Activity

- Tweet frequency and engagement
- LinkedIn post activity
- Follower/following counts
- Recent interactions

### Signals and Scoring

- All detected intent signals
- Company-level signals
- Buyer state (active/monitor/poor_fit/disqualified)
- Buyer score, fit score, intent score, timing score
- Last activity date, last score date

## Lead Lifecycle in a Sequence

Once enrolled in a sequence, a lead's state evolves:

1. **Enrolled** - Added to sequence, awaiting first action
2. **Active** - Currently receiving sequence actions
3. **Replied** - Lead has responded to a message
4. **Meeting Booked** - Lead scheduled a call
5. **Completed** - Reached end of sequence
6. **Failed** - Action failed (invalid profile, rate limit, etc.)
7. **Removed** - You manually removed the lead from the sequence

## Best Practices

{% hint style="info" %}
**Quality Over Quantity:** 100 highly-scored leads from LinkedIn job search will outperform 1,000 random CSV imports. Focus on signal-rich sources first.
{% endhint %}

{% hint style="info" %}
**Monitor Lower Scores:** Don't ignore poor_fit leads entirely. Re-scoring happens when new signals are detected. A lead could jump from 25 to 65 based on new social activity.
{% endhint %}

{% hint style="warning" %}
**Respect Platform Limits:** AutoReach respects X and LinkedIn's rate limits. Bulk imports of 10,000+ leads will be throttled to avoid account restrictions.
{% endhint %}
