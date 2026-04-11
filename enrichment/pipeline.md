# The Enrichment Pipeline

The enrichment pipeline is the backbone of AutoReach's lead intelligence system. It takes raw lead data and progressively enriches it with profile information, activity signals, and scoring intelligence.

## Pipeline Architecture

The enrichment process flows through 7 sequential steps:

```
x_find → x_enrichment → linkedin_find → linkedin_enrichment 
  → activity_fetch → location_enrichment → scoring
```

Each step builds on the previous one, creating a comprehensive profile of every lead.

### Step-by-Step Breakdown

**1. X Find** - Locates X/Twitter profiles for the lead
**2. X Enrichment** - Extracts profile data and DM eligibility from X
**3. LinkedIn Find** - Locates LinkedIn profiles for the lead
**4. LinkedIn Enrichment** - Extracts work history, skills, network stats
**5. Activity Fetch** - Retrieves recent tweets, posts, and engagement signals
**6. Location Enrichment** - Geocodes and validates location data
**7. Scoring** - Calculates buyer intent, fit, and engagement scores

## Source Priority & Processing Order

AutoReach applies a "fast lane" system based on lead source. Leads from intent sources get processed faster and are prioritized for deep analysis.

{% hint style="info" %}
**Source Priority Multipliers:**
- **Intent Search (1.4x)** - Fastest lane. Leads actively posting about your solution
- **Manual Import (1.0x)** - Standard processing speed
- **CSV Import (0.6x)** - Slower lane. Lower priority, batched with other CSV leads
{% endhint %}

This means if an intent lead takes 10 minutes to fully enrich, a CSV lead might take ~17 minutes. Intent leads get proportionally more computational resources for deep analysis.

## Processing Configuration

The pipeline is configured for optimal speed and accuracy:

| Setting | Value | Purpose |
|---------|-------|---------|
| Batch Size | 25 leads | Process leads in groups for efficiency |
| Parallel Deep Analyses | 5 | Maximum concurrent AI analysis jobs |
| Timeout | 60 seconds | Max time per enrichment step |
| Retries | 3 | Automatic retry on failure |
| Backoff Strategy | Exponential | Wait 2s → 4s → 8s between retries |

### What These Settings Mean

- **Batch Size**: Leads are processed in groups of 25. Smaller batches are faster but less efficient.
- **Parallel Analyses**: AutoReach can run up to 5 deep analyses (like buyer signal extraction) at the same time.
- **Timeout**: If a single enrichment step takes longer than 60 seconds, it times out and triggers a retry.
- **Exponential Backoff**: If a step fails, AutoReach waits 2 seconds before retry 1, 4 seconds before retry 2, and 8 seconds before retry 3.

## Pipeline Recovery

The enrichment pipeline is designed to be resilient. If processing stalls:

{% hint style="success" %}
**Automatic Recovery:** The system automatically resumes stalled enrichment jobs. You don't need to manually restart anything. Check the **Activity Log** to monitor enrichment progress.
{% endhint %}

Failed steps are automatically retried up to 3 times with exponential backoff. If all retries fail, the lead moves to the next available step or is marked for manual review.

## From Enrichment to Scoring to Outreach

Once enrichment completes, the collected data flows into two key systems:

**1. Buyer Scoring** - The enrichment data powers the buyer intelligence engine:
- Does the lead match your ICP?
- Are they showing intent signals?
- What's their buyer readiness score (0-100)?

**2. DM Generation** - AI uses enriched profile data to personalize outreach:
- Recent tweets and activities
- Work history and expertise
- Company context
- Shared interests or connections

The better the enrichment, the better the scoring and the more relevant your outreach.

{% hint style="warning" %}
**Enrichment Quality Matters:** Leads with incomplete enrichment (missing LinkedIn profile, no recent activity) will receive lower scoring and less personalized outreach. Encourage leads to have complete profiles on X/LinkedIn for best results.
{% endhint %}
