# Connecting Your Social Accounts

Connect your X (Twitter) and LinkedIn accounts to AutoReach through the Chrome Extension. This is the only supported method for linking social accounts.

> **Important:** Make sure you have [installed the Chrome Extension](chrome-extension.md) and activated your license key first.

> **Email accounts:** Gmail and Outlook are connected separately, not through the Chrome Extension. See [Connecting Email](connecting-email.md) for setup.

---

## Connecting X (Twitter)

1. Visit [x.com](https://x.com) and make sure you are logged in
2. Click the **AutoReach extension icon** in your Chrome toolbar
3. Enter your **name**
4. Enter your **4-digit PIN** for X DM Chat
5. Click **Connect Account**

The extension links your active browser session to AutoReach automatically.

> **Warning:** Do not use automated engagement on X aggressively. Aggressive automated activity is the number one reason accounts get suspended. Start conservatively and increase gradually.

## Connecting LinkedIn

1. Visit [linkedin.com](https://linkedin.com) and make sure you are logged in
2. Click the **AutoReach extension icon** in your Chrome toolbar
3. Enter your **first name** and **last name**
4. Click **Connect Account**

The extension links your active browser session to AutoReach automatically.

---

## Proxy Configuration

AutoReach automatically provisions a secure ISP residential static proxy for each account when you pick a location during onboarding. You do not need to configure or purchase a proxy separately.

ISP residential static proxies use real internet service provider IPs, making your activity indistinguishable from a normal user. Each account gets its own dedicated proxy.

---

## LinkedIn Daily Connection Limits

LinkedIn enforces daily limits on connection requests. AutoReach tracks these automatically:

AutoReach lets you set a daily connection request limit per account. Any whole number from 1 to 100 is allowed (default 15, which is the recommended starting point). Choose a limit that matches your account type and risk tolerance - lower limits are safer for new or free accounts.

These limits reset daily. AutoReach tracks your usage and pauses connection requests when you approach the limit. If a connection request gets rate-limited, it enters a **deferred state** and automatically resumes the next day.

---

## Inbound Engagement Detection

AutoReach monitors your accounts for inbound engagement and processes it as buying signals.

**X (Twitter):** Retweets, likes on your posts, and new followers.

**LinkedIn:** Reactions on your posts, comments on your content, mentions of you, and new connections.

Someone engaging with your content may be a potential buyer. AutoReach can automatically create leads from high-intent engagers and update signals on existing leads.

---

## Account Health

AutoReach continuously monitors your account health and warns you when something is wrong. See **[Account Safety](../settings/account-safety.md)** for details on error handling, cooldowns, and emergency pausing.

### Prevention Tips

1. Use a dedicated residential proxy per account
2. Set realistic daily action limits (start conservatively on new accounts)
3. Space out your sequences with wait periods
4. Do not engage with spam, adult, or hateful content
5. Start with the Engagement Engine to build activity history before launching sequences
6. Monitor your account health regularly in the Accounts page

---

## Troubleshooting

**"Cookies Invalid"** - Your session has expired. Open the Chrome Extension, click the three dots next to the account, and click **Reconnect**.

**"Proxy Connection Failed"** - Your proxy was provisioned automatically during onboarding. If you see persistent proxy errors, contact support at hello@autoreach.tech.

**"Rate Limited"** - You have hit the platform's action limit. Wait for the cooldown to expire. Consider lowering your daily limits.

---

## Next Steps

Once your accounts are connected:

1. **[Connect Email](connecting-email.md)** to add Gmail and/or Outlook as a third channel (optional but recommended)
2. **[Create an Offer](create-offer.md)** to define your target audience and message tone
3. **[Build a Sequence](../outreach/building-sequences.md)** to automate outreach
4. **[Launch Autopilot](../autopilot/overview.md)** for fully automated pipeline management
