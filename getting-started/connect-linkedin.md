# Connecting Your LinkedIn Account

LinkedIn is one of the two core platforms AutoReach supports for outreach. Connecting your LinkedIn account lets AutoReach send connection requests, DMs, comments, likes, and profile views on your behalf.

> **Important:** You can ONLY connect your LinkedIn account through the Chrome Extension. Make sure you've [installed the extension](chrome-extension.md) and activated your license key first.

***

## Connecting via Chrome Extension

1. Visit [linkedin.com](https://linkedin.com) and make sure you're logged in
2. Click the **AutoReach extension icon** in your Chrome toolbar
3. Enter your **first name** and **last name**
4. Click **Connect Account**

The extension will automatically extract your session cookies and link your LinkedIn account to AutoReach. No manual cookie copying or DevTools required.

***

## Proxy Configuration

AutoReach automatically provisions a secure ISP residential static proxy for your account when you pick a location during onboarding. You don't need to configure or purchase a proxy separately.

> **Note:** Each LinkedIn account gets its own dedicated ISP residential static proxy. This ensures your activity appears to come from a real residential IP, which is critical for LinkedIn's stricter anti-automation detection.

***

## Weekly Connection Limits

LinkedIn enforces weekly limits on connection requests. AutoReach tracks these automatically:

| Account Type    | Weekly Limit             |
| --------------- | ------------------------ |
| Free            | 100 connections/week     |
| Premium         | 150 connections/week     |
| Sales Navigator | 200 connections/week     |

These limits reset weekly. AutoReach tracks your usage and pauses connection requests when you approach the limit. If a connection request gets rate-limited, it enters a **deferred state** and automatically resumes the following Monday.

***

## Rate Limiting

AutoReach uses multiple layers of rate limiting to protect your LinkedIn account, including per-request throttling, daily activity caps, and automatic emergency pausing when issues are detected.

***

## Inbound Engagement Detection

AutoReach monitors your LinkedIn notifications for inbound engagement:

* **Reactions** on your posts
* **Comments** on your content
* **Mentions** of your profile
* **Connection requests** received
* **Profile views**

These are processed as buying signals. Someone engaging with your content may be a potential buyer. AutoReach can automatically create leads from high-intent engagers (replies, comments, connections) and update signals on existing leads.

***

## Account Health

AutoReach continuously monitors your LinkedIn account health. If issues arise:

| Issue         | Cooldown | What Happens                             |
| ------------- | -------- | ---------------------------------------- |
| Rate limit    | 24 hours | Activity reduced by 50%                  |
| Bot detection | 7 days   | Activity reduced by 90% (near full stop) |
| Auth error    | 48 hours | Auto-recovery attempted                  |
| Proxy error   | 24 hours | Auto-recovery attempted                  |
| IP blocked    | 24 hours | Full activity stop                       |

> **Warning:** If you see a bot detection warning, do not try to bypass it. Wait the full 7-day cooldown and let AutoReach gradually resume activity.

***

## Best Practices

* **One proxy per account**: Never share proxies between LinkedIn accounts.
* **Start with the Engagement Engine**: Let it build activity history before launching sequences.
* **Keep connection requests conservative**: Stay well under the weekly limit, especially for new accounts.
* **Use realistic activity windows**: Match the hours you'd normally be active on LinkedIn.
* **Monitor the health dashboard**: Check your account status regularly in the Accounts page.

## Next Steps

- **[Creating Your First Offer](create-offer.md)**: Define your target audience and value proposition
- **[Building Sequences](../outreach/building-sequences.md)**: Set up LinkedIn outreach sequences for your leads
- **[Quickstart](quickstart.md)**: Follow the full setup guide from start to finish
