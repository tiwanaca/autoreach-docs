# X Profile Data

X enrichment extracts profile information and recent activity from X (Twitter) profiles. This data powers buyer scoring, outreach personalization, and - most importantly - determines whether you can send DMs to a lead without following them first.

## How It Works

X profile enrichment fetches the full profile data using your connected X account. If no X account is available, enrichment skips and the pipeline advances.

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

- **Can-DM = True** - You can send direct messages without following the account first. Your initial message goes straight to their inbox.
- **Can-DM = False** - Your first message will appear in their "Message Requests" folder, which has much lower engagement.

### Recent Activity

After profile data is fetched, recent posts are collected:

| Field | Description |
|---|---|
| Recent Posts | Array of structured post objects |
| Posts Text | Concatenated text with date labels for AI consumption |
| Interaction Orbit | Who the lead interacts with on social media |
| Signal Date | Updated if a newer post is found |

Older posts are filtered out to keep activity data relevant. Activity data is not required for the pipeline to advance - if it can't be fetched, scoring continues without it.

## Error Handling

Transient errors (rate limits, network issues) are automatically retried. Permanent errors (profile not found, no account available) are logged and the pipeline continues-  X enrichment failure does not block LinkedIn enrichment, scoring, or other pipeline phases.

## Data Quality

- **Suspended accounts** - profile data cannot be retrieved (404)
- **Private/protected accounts** - limited data available; recent posts may not be accessible
- **New accounts** - may have minimal activity for personalization
- **Deleted accounts** - return 404 and enrichment skips

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
