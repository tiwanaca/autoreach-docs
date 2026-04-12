# Installing the Chrome Extension

The AutoReach Chrome Extension is the gateway to powerful CRM and automation features. It lets you manage your sales pipeline from your browser, extract account credentials, and track prospect engagement.

## Installation

### From Chrome Web Store (Recommended)

1. Visit the [AutoReach Chrome Extension](https://chromewebstore.google.com/detail/autoreach) page
2. Click **Add to Chrome**
3. In the popup, click **Add extension**
4. The AutoReach icon will appear in your Chrome toolbar

### Manual Installation

If the extension isn't on the Web Store yet:

1. Download the extension file from your [AutoReach Settings](https://autoreach.tech/settings/integrations)
2. Go to **chrome://extensions**
3. Toggle on **Developer mode** (top right)
4. Click **Load unpacked**
5. Select the downloaded extension folder
6. The AutoReach extension is now installed

## License Key Activation

After installation, activate your license key:

1. Click the **AutoReach icon** in your Chrome toolbar
2. Go to **Settings** (gear icon)
3. Paste your **License Key** (found at [autoreach.tech/settings/integrations](https://autoreach.tech/settings/integrations))
4. Click **Activate**

{% hint style="warning" %}
**Important**: Keep your license key private. Never share it with others or post it online.
{% endhint %}

If you don't have a license key yet:

1. Log into your AutoReach account
2. Go to **Settings** > **Integrations**
3. Copy your license key
4. Return to the extension and paste it

## What the Extension Does

The AutoReach Chrome Extension adds three core features to your browser:

### 1. CRM Pipeline Management

Manage your sales pipeline directly from the browser. As you browse LinkedIn and Twitter, you can:

- **Create leads**: See a prospect's profile? Click the extension icon and add them to your CRM.
- **Track pipeline stage**: Move leads through your sales funnel (new > requested > accepted > contacted > replied > meeting > won/lost).
- **Add notes**: Track your interactions with each prospect.
- **View lead history**: See all messages and interactions with a prospect.

### Pipeline Stages

| Stage         | Description                                          |
| ------------- | ---------------------------------------------------- |
| **New**       | Prospect added to your CRM                           |
| **Requested** | You sent a connection request or message              |
| **Accepted**  | Prospect accepted your connection or replied positively |
| **Contacted** | You've reached out directly                          |
| **Replied**   | Prospect has engaged in conversation                 |
| **Meeting**   | Call or meeting scheduled                            |
| **Won/Lost**  | Deal closed (won) or opportunity over (lost)         |

### 2. Social Account Connection

The extension is the **only way** to connect your X and LinkedIn accounts to AutoReach:

- **LinkedIn**: Visit linkedin.com, click the extension, enter your first and last name, and click Connect Account.
- **X/Twitter**: Visit x.com, click the extension, enter your name and a 4-digit PIN for DM Chat, and click Connect Account.
- **Automatic cookie extraction**: The extension handles all authentication automatically. No manual DevTools or cookie copying needed.

See [Connecting X](connect-twitter.md) and [Connecting LinkedIn](connect-linkedin.md) for details.

### 3. Profile Data Scraping

Automatically extract and store prospect information:

- **Name, title, company, location**: Extracted from LinkedIn and Twitter profiles
- **Bio and headline**: Captured for context
- **Recent posts/activity**: Tracked to identify interests and pain points
- **Profile URL and handle**: Saved for quick reference

This data powers AutoReach's lead scoring and personalization.

## LinkedIn Connection Acceptance Detection

AutoReach's extension monitors your LinkedIn notifications and detects when someone accepts your connection request.

### How It Works

1. You send a connection request to "Alice Chen, VP Marketing at Acme"
2. Alice accepts your connection request
3. The extension detects the new connection and fuzzy-matches it to your sent requests
4. AutoReach alerts you in the **Inbox** and marks the lead as **Accepted**

### Fuzzy Name Matching

The extension uses fuzzy matching to recognize accepted connections even if the name doesn't match exactly:

- "Robert J. Chen" matches "Rob Chen" or "R. Chen"
- "Sarah Johnson" matches "Sarah" if that's a pending request
- "Jose Garcia-Lopez" matches "Jose Garcia Lopez" (accent handling)
- "Michael O'Brien" matches "Mike O Brien"

You don't have to worry about name variations. AutoReach will catch them.

{% hint style="info" %}
**Tip**: The more exact your original connection message, the more reliable the matching. Use their full name in your message for best results.
{% endhint %}

### Notifications

When a match is detected:

1. You get a notification in your AutoReach **Inbox**
2. Lead status changes to **Accepted**
3. A suggested reply is generated (if AI is enabled)
4. You can respond immediately or review first

## Platform Detection

The extension automatically detects which platform you're on:

- **LinkedIn.com**: LinkedIn interface and features active
- **X.com / Twitter.com**: X interface and features active
- **Other sites**: Extension shows limited features (CRM access only)

This uses the `navigator.platform` API to detect your operating system and adjust the interface accordingly.

## Cyrillic Character Detection

The extension includes anti-phishing protection by detecting Cyrillic characters in URLs and messages.

### What It Does

If the extension detects Cyrillic characters in:

- URLs (e.g., a domain using Cyrillic lookalikes of Latin characters)
- Message content
- Profile bios

It will **warn you** with a security alert. This helps prevent:

- **Phishing attacks**: Fake domains using Cyrillic lookalikes (Cyrillic 'a' looks like Latin 'a')
- **Fraudulent messages**: Spam or scam messages written in Cyrillic
- **Compromised profiles**: Accounts taken over by bad actors

{% hint style="warning" %}
**Example**: A fake domain might use Cyrillic 'a' (U+0430) instead of Latin 'a' to mimic a legitimate domain. The extension will flag this.
{% endhint %}

If you see a Cyrillic warning, be cautious before clicking links or providing information.

## Chrome Extension Permissions

When you install the extension, you'll be asked to grant permissions. Here's what we need and why:

| Permission                                    | Purpose                                                      |
| --------------------------------------------- | ------------------------------------------------------------ |
| **Read and change data on linkedin.com**      | Extract cookies, detect connections, scrape profile data      |
| **Read and change data on x.com**             | Extract cookies, detect follows, scrape profile data          |
| **Read and change data on twitter.com**       | Support legacy Twitter URLs                                  |
| **Read your browsing history**                | Detect when you visit LinkedIn/X (local only, not stored)    |
| **Access tabs and windows**                   | Switch between open tabs to extract data                     |
| **Storage**                                   | Save your license key and settings locally                   |

All data is stored locally in your browser. We do not log your browsing activity.

## Using the Extension

### Opening the Extension

1. Click the **AutoReach icon** in your Chrome toolbar
2. The extension popup opens with options:
   - **CRM**: Manage your sales pipeline
   - **Extract Cookies**: Get authentication credentials
   - **Settings**: License key, preferences
   - **Analytics**: View dashboard of your activity

### Adding a Prospect to Your CRM

1. Visit a prospect's LinkedIn or X profile
2. Click the **AutoReach icon**
3. Click **Add to CRM**
4. Fill in their pipeline stage (New, Requested, etc.)
5. Add any notes
6. Click **Save**

The prospect is now in your CRM and synced to your AutoReach account.

### Connecting a Social Account

1. Visit [linkedin.com](https://linkedin.com) or [x.com](https://x.com) while logged in
2. Click the **AutoReach icon**
3. For **LinkedIn**: Enter your first name and last name, then click **Connect Account**
4. For **X/Twitter**: Enter your name and a 4-digit PIN for DM Chat, then click **Connect Account**

The extension handles all cookie extraction and authentication automatically. See [Connecting X](connect-twitter.md) and [Connecting LinkedIn](connect-linkedin.md) for details.

### Viewing Your Analytics

1. Click the **AutoReach icon**
2. Go to **Analytics**
3. See your activity this week:
   - Profiles viewed
   - Connections sent
   - Messages sent
   - Replies received
   - Acceptance rate

## Troubleshooting

### "License Key Invalid"

Your license key has expired or is incorrect.

1. Go to [autoreach.tech/settings/integrations](https://autoreach.tech/settings/integrations)
2. Copy your current license key
3. Paste it into the extension's Settings
4. Click **Activate**

### "Extension Can't Access This Page"

The extension only works on:

- linkedin.com
- x.com / twitter.com
- autoreach.tech

If you're on a different site, the extension will show limited features.

### "Cookie Extraction Failed" / Session Expired

Your session may have expired. To reconnect:

1. Open the **AutoReach Chrome Extension**
2. Click the **three dots** next to the account
3. Click **Reconnect**

Make sure you're logged into the social account in your browser before reconnecting.

### "Cyrillic Character Warning"

You've encountered text with Cyrillic characters. Be cautious:

1. Don't click suspicious links
2. Don't provide credentials or sensitive info
3. If it's a phishing attempt, report it to the platform
4. You can dismiss the warning if you trust the source

### "Connection Not Detected"

LinkedIn connection acceptance detection requires:

1. The extension to be running
2. Your LinkedIn tab to stay open
3. LinkedIn notifications to be enabled
4. The pending connection to still be in your pending requests

If detection isn't working:

- Refresh your LinkedIn page
- Check that you have pending requests in the right stage
- Re-authenticate your license key

## Privacy & Security

### Data Storage

- All CRM data is stored in your AutoReach account (encrypted)
- License key is stored locally in your browser (not shared)
- Extracted cookies are transmitted only to AutoReach servers (HTTPS encrypted)
- We never log your browsing history or profile views

### Cookies & Credentials

- Keep your extracted cookies private
- Don't share your license key
- Cookies expire over time (2-4 weeks). Reconnect via the extension (three dots > Reconnect).
- If you log out of your social accounts, reconnect via the extension

### Reporting Issues

Found a security issue? Email security@autoreach.tech with details. We take security seriously and will respond within 24 hours.

## Next Steps

1. **Extract your X credentials**: [Connecting X](connect-twitter.md)
2. **Extract your LinkedIn credentials**: [Connecting LinkedIn](connect-linkedin.md)
3. **Create an Offer**: [Creating Your First Offer](create-offer.md)
4. **Follow the Quickstart**: [Quickstart](quickstart.md)

Need help? Email support@autoreach.tech.
