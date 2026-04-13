# Engagement Engine Overview

The Engagement Engine builds a credible social presence on your accounts before you start outreach. It automatically posts content, engages with relevant posts, and grows your visibility so that when leads receive your messages, they see an active account with genuine engagement history.

## What the Engagement Engine Does

The Engagement Engine automatically:

- **Posts content** aligned with your offer and content pillars (X tweets and LinkedIn posts)
- **Engages with relevant posts** in your niche (likes, replies/comments, follows/connections)
- **Views LinkedIn profiles** to generate passive visibility
- **Maintains human-like patterns** with randomized timing, skip days, and natural variation

## How It Works

The warmup scheduler runs every **10 minutes**. Each cycle it:

1. Expires stale approvals and engagements (48-hour timeout)
2. Increments warmup day counters
3. Resets error counts
4. Processes tweets, engagement, auto-responses, and LinkedIn actions in parallel

All actions are distributed into sessions within your activity window with randomized delays between actions.

## Available Platforms

| Platform | Action Types |
|---|---|
| **X** | Tweets, likes, follows, replies |
| **LinkedIn** | Posts, likes, connection requests, comments, profile views |

You can run the Engagement Engine on multiple accounts simultaneously.

## Daily Activity

The Engagement Engine generates a randomized mix of actions each day. There are no ramp-up phases — activity starts at full range from day 1. Each day's action counts vary to mimic natural human behavior, with a **15% chance** of a full skip day (minimal activity only).

See **[Daily Action Allocation](daily-actions.md)** for the complete breakdown of action ranges per platform.

## Content Approval

All generated content enters an approval queue by default. You can:

- **Approve**: post as-is at the scheduled time
- **Reject**: discard and regenerate a replacement
- **Edit**: modify the text before approving

Enable **auto-approval** to skip manual review and post content automatically. Pending approvals expire after **48 hours** if not reviewed.

## Next Steps

- **[Content Strategy & Pillars](content-strategy.md)**: How content themes are organized
- **[Daily Action Allocation](daily-actions.md)**: Detailed breakdown of daily activity patterns
- **[Content Generation](content-generation.md)**: How tweets and posts are created
- **[Engagement Automation](engagement.md)**: How the engine interacts with relevant content
- **[Approvals](approvals.md)**: Managing the content approval queue
