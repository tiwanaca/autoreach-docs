# X/Twitter Profile Data

X/Twitter enrichment extracts profile information and activity data critical for direct outreach. Most importantly, it determines whether you can send DMs without following the lead first.

## What Gets Extracted

### Profile Information from GraphQL API

AutoReach uses X's GraphQL API to fetch:

- **User ID** - Unique identifier needed for DM delivery
- **Display Name** - Public name on the profile
- **Username/Handle** - @username used for mentions and DMs
- **Bio** - Profile biography (up to 160 characters)
- **Profile Image** - Avatar URL
- **Banner Image** - Header image URL
- **Follower/Following Counts** - Network size
- **Verification Status** - Whether the account is verified
- **Account Creation Date** - When the profile was created

### The Critical DM Flag

The most important piece of X data is the **can-DM flag**. This boolean determines whether:

{% hint style="success" %}
**Can-DM = True** - You can send direct messages WITHOUT following the account first. This dramatically improves outreach conversion, since your initial message goes straight to their inbox.

**Can-DM = False** - You must follow the account before sending DMs. Your first DM will appear in their "Message Requests" folder, which has much lower engagement.
{% endhint %}

The can-DM status depends on:
- Whether their account accepts DMs from non-followers
- Whether they have DMs restricted to followers only
- Whether they have DMs disabled entirely

AutoReach automatically detects this and routes outreach accordingly.

### Recent Activity & Tweets

AutoReach fetches:

- **Recent Tweets** - Latest posts from the profile (usually last 50-200)
- **Tweet Content** - The text, links, and media in those tweets
- **Engagement Metrics** - Likes, retweets, reply counts
- **Tweet Dates** - When each tweet was posted
- **Hashtags & Keywords** - Topics and interests they post about

This activity data is used for:
- Identifying recent interests and projects
- Finding conversation starters for personalized outreach
- Scoring buyer intent (are they talking about problems you solve?)
- Timing outreach (better to reach someone after they've posted about a relevant topic)

## Authentication

{% hint style="info" %}
**Cookie-Based Access:** X data is accessed using cookie-based authentication. Your X/Twitter account cookies are stored securely in AutoReach settings under **Settings > Accounts > X/Twitter**.
{% endhint %}

The authentication uses your own X account session, so you maintain full control. Cookies are refreshed periodically to keep the session valid.

## How X Data Complements LinkedIn

X and LinkedIn serve different purposes in your outreach:

| Dimension | LinkedIn | X/Twitter |
|-----------|----------|-----------|
| **Profile Type** | Professional credentials | Interest signals & personality |
| **Data Freshness** | Updated yearly or less | Updated daily or hourly |
| **What's Shown** | Formal work history | Real-time thoughts & interests |
| **Outreach Value** | Context & credibility | Conversation starters & intent |
| **Can-DM Status** | Not applicable | Critical for first contact |

**Best Practice:** Use LinkedIn for initial credibility checks (is this person's role/experience relevant?) and X for finding conversation hooks (what are they talking about right now?) and determining DM reachability.

## Using X Data for Outreach

AI message generation leverages X data to:

- **Reference Recent Activity** - "I saw your tweet about scaling sales engineering..."
- **Show Genuine Interest** - "Your thoughts on buyer enablement align with..."
- **Time the Outreach** - Messages sent shortly after relevant tweets get higher response rates
- **Personalize the Approach** - Reference their actual words and interests, not assumptions

{% hint style="warning" %}
**DM Deliverability:** Always check the can-DM status before sending initial outreach. If can-DM is false, set your sequence to follow first, then wait 24 hours before sending DMs. This improves deliverability to the inbox instead of message requests.
{% endhint %}

## X Data Quality Considerations

- **Suspended Accounts** - Data fetch will fail for suspended accounts
- **Private Accounts** - Limited data available for private profiles; may not have recent tweets
- **New Accounts** - Might have minimal activity data
- **High-Activity Accounts** - Popular accounts update frequently; activity data refreshes on each enrichment

AutoReach handles data fetch failures gracefully and will retry enrichment periodically.
