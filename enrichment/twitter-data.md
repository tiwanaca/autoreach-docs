# X Profile Data

X enrichment extracts profile information and recent activity from X (Twitter) profiles. This data powers buyer scoring, outreach personalization, and -- most importantly -- determines whether you can send DMs to a lead without following them first.

## How It Works

X profile enrichment fetches the full profile object in a single API request.

### Rate Limit

X enrichment processes approximately **3 profiles per minute**, with an 18-second delay between jobs. Twitter's API enforces approximately 50 requests per 15-minute window.

Rate limit (429) responses trigger exponential backoff starting at 5 minutes.

### Account Selection

Each enrichment job selects a Twitter account in priority order:

1. **Explicit:** Account specified in the job
2. **Lead's target user:** If the lead has a target user, that user's Twitter account is used
3. **Any active account:** First active Twitter account found for the user

If no account is available, enrichment skips and the pipeline advances.

## What Gets Extracted

### Profile Information

| Field | Description |
|---|---|
| Twitter User ID | Unique account identifier |
| Name | Display name |
| Username | Handle (derived from profile URL) |
| Bio | Profile description |
| Follower Count | Number of followers |
| Following Count | Number of accounts followed |
| Verified | Blue checkmark or verification status |
| Profile Image | Profile picture URL |
| Can DM | Whether you can send direct messages (see below) |

### The Can-DM Flag

The most important piece of X data is the **can-DM flag**. This boolean controls whether your outreach can land directly in someone's inbox.

- **Can-DM = True** -- You can send direct messages without following the account first. Your initial message goes straight to their inbox.
- **Can-DM = False** -- Your first message will appear in their "Message Requests" folder, which has much lower engagement.

### Recent Activity

After profile data is fetched, recent posts are collected with a 90-second timeout.

| Field | Description |
|---|---|
| Recent Posts | Array of structured post objects |
| Posts Text | Concatenated text with date labels for AI consumption |
| Fetch Timestamp | When posts were fetched |
| Empty Flag | True if fetch succeeded but no posts found |
| Rate Limited | True if tweet fetch hit rate limits |
| Interaction Orbit | Who the lead interacts with on social media |
| Signal Date | Updated if a newer post is found |

Posts older than 6 months are filtered out. If the tweet fetch is rate-limited, the pipeline continues to scoring -- activity data is not required for the pipeline to advance.

## Error Handling

### Transient Errors (Retried)

| Error | Behavior |
|---|---|
| Rate limit (429) | Exponential backoff starting at 5 minutes (5m, 10m, 20m, 40m...) |
| Network errors (ECONNRESET, ETIMEDOUT, TLS) | Up to 3 retries with exponential backoff (5s, 10s, 20s) |
| Transient HTTP (502, 503, 504, 522) | Exponential backoff |
| Proxy authentication (407) | Up to 2 retries |
| Validation error (422) | Up to 2 retries |

### Non-Transient Errors (Pipeline Advances)

- 404 Not Found (profile deleted or doesn't exist)
- Lead not found
- No active Twitter account available
- No X profile URL and no username
- Proxy connection failure (marked in account health)

Non-transient errors are logged and the pipeline continues -- X enrichment failure does not block LinkedIn enrichment, scoring, or other pipeline phases.

### Deferral

- **Outside outreach window:** Job is deferred until the account's outreach window opens

## Data Quality

- **Suspended accounts** -- profile data cannot be retrieved (404)
- **Private/protected accounts** -- limited data available; recent posts may not be accessible
- **New accounts** -- may have minimal activity for personalization
- **Deleted accounts** -- return 404 and enrichment skips

## How X Data Complements LinkedIn

| Dimension | LinkedIn | X |
|---|---|---|
| **Profile Type** | Professional credentials | Interest signals and personality |
| **Data Freshness** | Updated infrequently | Updated daily or hourly |
| **What's Shown** | Formal work history | Real-time thoughts and interests |
| **Outreach Value** | Context and credibility | Conversation starters and intent |
| **DM Reachability** | Not applicable | Can-DM flag critical for first contact |

## Next Steps

- **[LinkedIn Profile Data](linkedin-data.md)**: See what professional data is extracted from LinkedIn
- **[Web Enrichment](web-enrichment.md)**: Learn how company-level context is gathered from the web
- **[Enrichment Pipeline](pipeline.md)**: See how X enrichment fits into the full pipeline
