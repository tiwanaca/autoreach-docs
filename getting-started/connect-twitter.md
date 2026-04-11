# Connecting Your X/Twitter Account

Connect your X (Twitter) account to AutoReach using cookie-based authentication. This method is faster and more reliable than traditional login flows.

## Authentication Methods

AutoReach supports two ways to authenticate X accounts:

### Method 1: Chrome Extension (Recommended)

The AutoReach Chrome Extension can automatically extract your X cookies.

1. Install the [AutoReach Chrome Extension](#) from the Chrome Web Store
2. Visit [x.com](https://x.com) and log in to your X account
3. In AutoReach, go to **Accounts** → **Add Account** → **X (Twitter)**
4. Click **Extract via Chrome Extension**
5. The extension will prompt you to authorize; click **Allow**
6. Your cookies are extracted automatically

### Method 2: Manual Cookie Extraction

If the extension isn't available, you can manually provide cookies from your browser:

1. Visit [x.com](https://x.com) and make sure you're logged in
2. Open your browser's Developer Tools (F12 or Cmd+Option+I)
3. Go to **Application** → **Cookies** → `x.com`
4. Copy the `auth_token` cookie value
5. In AutoReach, go to **Accounts** → **Add Account** → **X (Twitter)**
6. Paste the cookie value in the **Cookie** field
7. Click **Save**

{% hint style="warning" %}
**Important**: Keep your cookies private. They act like your login credentials. Do not share them with untrusted sources.
{% endhint %}

## Proxy Configuration

Using a proxy is **highly recommended** to avoid IP-based detection and rate limiting from X's anti-bot systems.

### Why Use a Proxy?

- **IP rotation**: X monitors for unusual activity from single IPs
- **Account safety**: Residential proxies reduce the risk of bot detection or account suspension
- **Multi-account**: If you're running multiple X accounts, each should route through a different IP

### Supported Proxy Types

- **HTTP Proxies** (standard web proxies)
- **SOCKS5 Proxies** (recommended for better performance)
- **Residential Proxies** (best for avoiding detection)

### Setting Up a Proxy

1. In your X account settings, go to **Proxy Configuration**
2. Select your proxy type (HTTP or SOCKS5)
3. Enter:
   - **Proxy Host**: The IP or domain of your proxy provider
   - **Proxy Port**: The port number (e.g., 8080)
   - **Username** (optional): If your proxy requires authentication
   - **Password** (optional): If your proxy requires authentication
4. Click **Test Proxy** to verify connection
5. Click **Save**

{% hint style="info" %}
**Tip**: We recommend residential proxy providers like Bright Data, Oxylabs, or Smartproxy. These rotate through real ISPs and are less likely to be detected by X's anti-bot measures.
{% endhint %}

### Proxy Providers We Recommend

- **Bright Data**: Residential proxies with 72M+ IPs
- **Oxylabs**: High-speed residential and datacenter proxies
- **Smartproxy**: Affordable rotating proxies
- **Rotating Proxies**: Use a different proxy for each account if possible

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
**Example**: If you set 9am–9pm EST, AutoReach will only like posts, follow users, and send DMs between those hours. This looks natural to X's systems and reduces detection risk.
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

- **New accounts** (< 3 months): 10–15 DMs/day
- **Established accounts** (3–12 months): 20–30 DMs/day
- **Mature accounts** (> 1 year): 40–50 DMs/day

Start conservative and increase slowly as your account builds reputation.

## Account Health Monitoring

AutoReach monitors your X account health and shows you warnings if something's wrong.

### Account Status Indicators

| Status | Meaning | Action |
|--------|---------|--------|
| **Healthy** | Account is running normally | Keep going! |
| **Warning** | Minor activity detected (likes, follows tracking) | Monitor closely |
| **Rate Limited** | Hit X's DM or action limit | Wait 24 hours for cooldown |
| **Bot Detected** | X flagged suspicious activity | Account may need rest (7–14 days) |
| **Suspended** | Account is temporarily or permanently blocked | Review activity; contact X support if needed |

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
2. Set realistic daily DM limits (start with 15–20)
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

Your X session has expired. Re-authenticate using the Chrome Extension or manual cookie extraction.

### "Proxy Connection Failed"

Check your proxy host, port, and credentials. Verify the proxy is running and accessible from your network.

### "Rate Limited"

You've hit X's DM limit for today. Wait 24 hours and try again. Consider lowering your daily DM limit.

### "Bot Detected"

X flagged suspicious activity. Wait 7 days for the cooldown to expire. In the meantime, reduce your daily action limits and use a different residential proxy.

## Next Steps

Once your X account is connected:

1. **Create an Offer** to define your target audience and message tone
2. **Build a Sequence** to automate outreach (like → follow → DM)
3. **Add Leads** manually or via Autopilot
4. **Launch your Sequence** and monitor results in your Inbox

See [Quickstart](quickstart.md) for the full setup flow, or read [Core Concepts](../core-concepts/sequences.md) to learn more about sequences and automation.
