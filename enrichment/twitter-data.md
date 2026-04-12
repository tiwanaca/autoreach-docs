# X Profile Data

X enrichment extracts profile information and activity data that are critical for direct outreach. Most importantly, it determines whether you can send DMs to a lead without following them first.

## What Gets Extracted

### Profile Information

AutoReach extracts the following from each X profile:

- **User ID** - Unique identifier needed for DM delivery
- **Display Name** - Public name shown on the profile
- **Username/Handle** - The @username used for mentions and DMs
- **Bio** - Profile biography (up to 160 characters)
- **Profile and Banner Images** - Avatar and header image URLs
- **Follower/Following Counts** - Network size indicators
- **Verification Status** - Whether the account holds a verified badge
- **Account Creation Date** - When the profile was first created

### The Can-DM Flag

The most important piece of X data is the **can-DM flag**. This boolean controls whether your outreach can land directly in someone's inbox.

{% hint style="success" %}
**Can-DM = True** - You can send direct messages WITHOUT following the account first. Your initial message goes straight to their inbox, which dramatically improves outreach conversion.

**Can-DM = False** - You must follow the account before sending DMs. Your first message will appear in their "Message Requests" folder, which has much lower engagement.
{% endhint %}

The can-DM status depends on the lead's account settings:
- Whether they accept DMs from non-followers
- Whether they restrict DMs to followers only
- Whether they have DMs disabled entirely

AutoReach detects this automatically and routes outreach accordingly.

### Recent Posts and Engagement Data

AutoReach collects recent activity from each profile:

- **Recent Posts** - The latest posts from the profile
- **Post Content** - Text, links, and media included in each post
- **Engagement Metrics** - Likes, reposts, and reply counts
- **Post Dates** - When each post was published
- **Hashtags and Keywords** - Topics and interests the lead posts about

This activity data powers several outreach functions:
- Identifying recent interests and active projects
- Finding natural conversation starters for personalized messages
- Scoring buyer intent based on whether the lead discusses problems you solve
- Timing outreach to coincide with relevant posts

## How X Data Complements LinkedIn

X and LinkedIn serve different purposes in your outreach strategy:

| Dimension | LinkedIn | X |
|-----------|----------|---|
| **Profile Type** | Professional credentials | Interest signals and personality |
| **Data Freshness** | Updated yearly or less | Updated daily or hourly |
| **What's Shown** | Formal work history | Real-time thoughts and interests |
| **Outreach Value** | Context and credibility | Conversation starters and intent |
| **Can-DM Status** | Not applicable | Critical for first contact |

**Best Practice:** Use LinkedIn for initial credibility checks (role, experience, company fit) and X for finding conversation hooks (what the lead is talking about right now) and determining DM reachability.

## Using X Data for Outreach Personalization

AI message generation leverages X data to craft relevant, natural outreach:

- **Reference Recent Activity** - "I saw your post about scaling sales engineering..."
- **Show Genuine Interest** - "Your thoughts on buyer enablement align with..."
- **Time the Outreach** - Messages sent shortly after relevant posts get higher response rates
- **Personalize the Approach** - Reference the lead's actual words and interests rather than assumptions

{% hint style="warning" %}
**DM Deliverability:** Always check the can-DM status before sending initial outreach. If can-DM is false, set your sequence to follow first, then wait 24 hours before sending DMs. This improves deliverability to the main inbox instead of message requests.
{% endhint %}

## Data Quality Considerations

- **Suspended Accounts** - Data cannot be retrieved for suspended profiles
- **Private Accounts** - Limited data is available; recent posts may not be accessible
- **New Accounts** - May have minimal activity data for personalization
- **High-Activity Accounts** - Popular profiles update frequently; activity data refreshes on each enrichment cycle

AutoReach handles fetch failures gracefully and retries enrichment periodically.

## Next Steps

- **[LinkedIn Profile Data](linkedin-data.md)**: See what professional data is extracted from LinkedIn
- **[Web Enrichment](web-enrichment.md)**: Learn how company-level context is gathered from the web
