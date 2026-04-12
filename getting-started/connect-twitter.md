# Connecting Your X/Twitter Account

Connect your X (Twitter) account to AutoReach through the Chrome Extension. This is the only supported method for linking your X account.

## Connecting via Chrome Extension

The AutoReach Chrome Extension handles authentication automatically by extracting your session cookies.

{% hint style="warning" %}
**Important**: You can ONLY connect your X account through the Chrome Extension. Make sure you've [installed the extension](chrome-extension.md) and activated your license key first.
{% endhint %}

### Steps

1. Visit [x.com](https://x.com) and make sure you're logged in
2. Click the **AutoReach extension icon** in your Chrome toolbar
3. Enter your **name**
4. Enter a **4-digit PIN** for X DM Chat
5. Click **Connect Account**

The extension will automatically extract your session cookies and link your X account to AutoReach. No manual cookie copying or DevTools required.

## Proxy Configuration

AutoReach automatically provisions a secure ISP residential static proxy for your account when you pick a location during onboarding. You don't need to configure or purchase a proxy separately.

### How It Works

1. During onboarding, you select your **location**
2. AutoReach provisions a dedicated ISP residential static proxy for that location
3. The proxy is automatically assigned to your account
4. All X API requests route through this proxy for safety

{% hint style="info" %}
**Why ISP proxies?** ISP residential static proxies use real internet service provider IPs, making your activity indistinguishable from a normal user. This is the safest proxy type for social media automation.
{% endhint %}

## Activity Window Setup

Set a time window during which AutoReach will run actions on your account. This makes automation look more natural.

1. In your X account settings, go to **Activity Window**
2. Set your preferred hours:
   - **Start Time**: e.g., 9:00 AM
   - **End Time**: e.g., 9:00 PM
   - **Timezone**: Select your local timezone
3. Click **Save**

During off-hours, AutoReach pauses all actions. They resume the next morning within your activity window.

{% hint style="info" %}
**Example**: If you set 9am to 9pm EST, AutoReach will only like posts, follow users, and send DMs between those hours. This looks natural to X's systems and reduces detection risk.
{% endhint %}

## Daily DM Limits

DM limits prevent your account from hitting X's rate limits, which trigger a 24-hour cooldown.

1. In your X account settings, go to **Daily Limits**
2. Set your **Daily DM Limit** (default: 20 DMs/day)
3. Click **Save**

AutoReach will never send more DMs than this limit, even if your sequence would generate more.

{% hint style="warning" %}
**Rate Limit Cooldown**: If you hit X's DM limit, your account enters a 24-hour cooldown. During this time, you cannot send new DMs. AutoReach will skip all DM actions and resume after 24 hours.
{% endhint %}

### Recommended Limits

| Account Age             | Recommended Limit |
| ----------------------- | ----------------- |
| New (< 3 months)        | 10-15 DMs/day     |
| Established (3-12 months) | 20-30 DMs/day   |
| Mature (> 1 year)       | 40-50 DMs/day     |

Start conservative and increase slowly as your account builds reputation.

## Account Health Monitoring

AutoReach monitors your X account health and shows you warnings if something's wrong.

### Account Status Indicators

| Status           | Meaning                                        | Action                                            |
| ---------------- | ---------------------------------------------- | ------------------------------------------------- |
| **Healthy**      | Account is running normally                    | Keep going!                                       |
| **Warning**      | Minor activity detected (likes, follows tracking) | Monitor closely                                |
| **Rate Limited** | Hit X's DM or action limit                     | Wait 24 hours for cooldown                        |
| **Bot Detected** | X flagged suspicious activity                  | Account may need rest (7-14 days)                 |
| **Suspended**    | Account is temporarily or permanently blocked  | Review activity; contact X support if needed      |

### What Causes Account Issues

- **Sending too many DMs too fast** (violates rate limits)
- **Following/unfollowing too many accounts** (flag for bot behavior)
- **Engaging with restricted content** (spam, hateful content, etc.)
- **Using outdated or leaked cookies** (may trigger security checks)
- **Proxies that X has blacklisted** (use reputable residential proxy providers)

### Rate Limit Cooldown

If you hit the DM rate limit:

- You'll see a **Rate Limited** status
- AutoReach will pause all DM actions
- You can still like posts and follow users
- After 24 hours, the cooldown expires and DMs resume

### Bot Detection Cooldown

If X detects bot-like behavior:

- You'll see a **Bot Detected** status
- AutoReach will pause **all actions** (likes, follows, DMs)
- This cooldown lasts **7 days**
- After 7 days, your account returns to **Healthy** status

{% hint style="warning" %}
**Prevention Tips**:
1. Use a residential proxy to avoid IP-based detection
2. Set realistic daily DM limits (start with 15-20)
3. Space out your sequences with wait periods (never run continuous actions)
4. Don't engage with spam, adult, or hateful content
5. Monitor your account health weekly
{% endhint %}

## Testing Your Connection

After connecting your account, test that everything works:

1. Go to **Accounts** and find your X account
2. Click **Test Connection**
3. AutoReach will:
   - Verify your cookies are valid
   - Check proxy connectivity
   - Confirm rate limit status
   - Test DM capability

If all checks pass, you're ready to use this account in sequences.

## Troubleshooting

### "Cookies Invalid"

Your X session has expired. Open the Chrome Extension, click the **three dots** next to the account, and click **Reconnect**.

### "Proxy Connection Failed"

Check your proxy host, port, and credentials. Verify the proxy is running and accessible from your network.

### "Rate Limited"

You've hit X's DM limit for today. Wait 24 hours and try again. Consider lowering your daily DM limit.

### "Bot Detected"

X flagged suspicious activity. Wait 7 days for the cooldown to expire. In the meantime, reduce your daily action limits and use a different residential proxy.

## Next Steps

Once your X account is connected:

1. **Create an Offer** to define your target audience and message tone
2. **Build a Sequence** to automate outreach (like, follow, DM)
3. **Add Leads** manually or via Autopilot
4. **Launch your Sequence** and monitor results in your Inbox

See [Quickstart](quickstart.md) for the full setup flow, or read [Core Concepts](../core-concepts/sequences.md) to learn more about sequences and automation.
