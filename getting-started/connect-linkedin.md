# Connecting Your LinkedIn Account

LinkedIn is one of the two core platforms AutoReach supports for outreach. Connecting your LinkedIn account lets AutoReach send connection requests, DMs, comments, likes, and profile views on your behalf.

{% hint style="warning" %}
**Important**: You can ONLY connect your LinkedIn account through the Chrome Extension. Make sure you've [installed the extension](chrome-extension.md) and activated your license key first.
{% endhint %}

---

## Connecting via Chrome Extension

1. Visit [linkedin.com](https://linkedin.com) and make sure you're logged in
2. Click the **AutoReach extension icon** in your Chrome toolbar
3. Enter your **first name** and **last name**
4. Click **Connect Account**

The extension will automatically extract your session cookies and li_at token, and link your LinkedIn account to AutoReach. No manual cookie copying or DevTools required.

---

## Proxy Configuration

AutoReach automatically provisions a secure ISP residential static proxy for your account when you pick a location during onboarding. You don't need to configure or purchase a proxy separately.

{% hint style="info" %}
Each LinkedIn account gets its own dedicated ISP residential static proxy. This ensures your activity appears to come from a real residential IP, which is critical for LinkedIn's stricter anti-automation detection.
{% endhint %}

---

## Weekly Connection Limits

LinkedIn enforces weekly limits on connection requests. AutoReach tracks these automatically:

| Account Type | Weekly Limit |
|---|---|
| Free / Premium | 100 connections/week |
| Sales Navigator | 200 connections/week |

These limits reset weekly. AutoReach tracks your usage and pauses connection requests when you approach the limit. If a connection request gets rate-limited, it enters a **deferred state** and automatically resumes the following Monday.

---

## Three-Layer Rate Limiting

AutoReach protects your LinkedIn account with three layers of rate limiting:

1. **Concurrency semaphore** — Maximum 1 concurrent request per account. No parallel API calls that could look suspicious.
2. **Token bucket** — 15 requests per minute. Spreads activity naturally across time.
3. **Daily budget** — 25,000 requests per day. A hard ceiling that prevents excessive activity.

If LinkedIn returns automation-detection signals (429 after retries, 999 status, or 403 with automation keywords), AutoReach triggers an **emergency pause** that instantly stops all activity on that account.

---

## Activity Window

Set the hours during which AutoReach can perform actions on your LinkedIn account:

- **Timezone** — Your local timezone (e.g., UTC, America/New\_York)
- **Start time** — When outreach can begin (e.g., 09:00)
- **End time** — When outreach stops (e.g., 21:00)

Outside this window, no actions are taken. This makes your activity pattern look natural — real people don't send LinkedIn messages at 3am.

{% hint style="info" %}
Enable the **24/7 Pipeline** toggle if you want enrichment and scoring to run around the clock. Outreach actions still respect your activity window.
{% endhint %}

---

## Warmup Phase

New LinkedIn accounts (or accounts that haven't been active) go through a warmup phase. During warmup, AutoReach gradually increases activity levels to build a natural engagement history before starting outreach. The Engagement Engine dashboard shows your warmup progress and daily activity.

---

## Inbound Engagement Detection

AutoReach monitors your LinkedIn notifications for inbound engagement:

- **Reactions** on your posts
- **Comments** on your content
- **Mentions** of your profile
- **Connection requests** received
- **Profile views**

These are processed as buying signals — someone engaging with your content may be a potential buyer. AutoReach can automatically create leads from high-intent engagers (replies, comments, connections) and update signals on existing leads.

---

## Account Health

AutoReach continuously monitors your LinkedIn account health. If issues arise:

| Issue | Cooldown | What Happens |
|---|---|---|
| Rate limit | 24 hours | Activity reduced by 50% |
| Bot detection | 7 days | Activity reduced by 90% (near full stop) |
| Auth error | 48 hours | Auto-recovery attempted |
| Proxy error | 24 hours | Auto-recovery attempted |
| IP blocked | 24 hours | Full activity stop |

{% hint style="warning" %}
If you see a bot detection warning, do not try to bypass it. Wait the full 7-day cooldown and let AutoReach gradually resume activity.
{% endhint %}

---

## Best Practices

- **One proxy per account** — Never share proxies between LinkedIn accounts
- **Start with warmup** — Let the Engagement Engine build activity history before launching sequences
- **Keep connection requests conservative** — Stay well under the weekly limit, especially for new accounts
- **Use realistic activity windows** — Match the hours you'd normally be active on LinkedIn
- **Monitor the health dashboard** — Check your account status regularly in the Accounts page
