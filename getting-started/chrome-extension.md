# Chrome Extension

The AutoReach Chrome Extension is the central tool for connecting your social accounts, managing your sales pipeline, and using AI-powered messaging directly from your browser.

## Installation

1. Visit the [AutoReach Chrome Extension](https://chromewebstore.google.com/detail/autoreach) page on the Chrome Web Store
2. Click **Add to Chrome**
3. In the popup, click **Add extension**
4. The AutoReach icon will appear in your Chrome toolbar

## License Key Activation

After installation, activate your license key:

1. Click the **AutoReach icon** in your Chrome toolbar
2. Paste your **License Key** (generated during onboarding or found at [autoreach.tech/settings](https://autoreach.tech/settings))
3. Click **Activate**

> **Important:** Keep your license key private. Never share it with others or post it online.

## Platform Modes

The extension automatically detects which platform you are on and adjusts its interface:

- **LinkedIn**: Full CRM pipeline, AI messaging assistant, connection tracking, profile scraping, account management, and proxy detection
- **X/Twitter**: Account connection, reconnection, PIN management, and proxy detection
- **Other sites**: Extension popup is not active

On X/Twitter, the CRM and Settings tabs are hidden. Only the Accounts tab is shown.

---

## Features on X/Twitter

On X, the extension provides:

### Account Connection

- Connect your X account by entering your name and a 4-digit PIN for DM Chat
- The extension automatically extracts session cookies from your browser
- See [Connecting Accounts](connecting-accounts.md) for details

### Account Management

- **Reconnect**: When cookies expire, click the three dots next to your account and click Reconnect
- **Enable/Disable**: Toggle accounts on or off
- **Edit PIN**: Update your 4-digit DM encryption PIN
- **Status display**: See account health (Healthy, Inactive, Expired, Paused, Rate Limited)

### Proxy Detection

- The extension detects and displays your current proxy configuration
- Supports AutoReach provisioned proxies and external proxy managers (GoLogin, Multilogin)

---

## Features on LinkedIn

On LinkedIn, the extension provides the full AutoReach experience.

### Account Connection

- Connect your LinkedIn account by entering your first and last name
- The extension automatically extracts session cookies
- See [Connecting Accounts](connecting-accounts.md) for details

### Account Management

Same as X: reconnect, enable/disable, status display, and proxy detection.

---

### CRM Pipeline (Kanban Board)

A full sales pipeline built into the extension popup. View and manage all your leads in a Kanban-style board.

#### Pipeline Stages

| Stage         | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| **New**       | Lead added to your CRM                                       |
| **On Hold**   | Lead temporarily paused (cooldown period after withdrawal)   |
| **Requested** | Connection request sent (auto-detected)                      |
| **Accepted**  | Connection request accepted (auto-detected or manual check)  |
| **Contacted** | You sent a DM (auto-detected)                                |
| **Replied**   | Lead replied to your message (auto-detected)                 |
| **Meeting**   | Meeting booked (AI-suggested, confirm to move)               |
| **Won**       | Deal closed successfully (AI-suggested, confirm to move)     |
| **Lost**      | Opportunity over (AI-suggested, confirm to move)             |

You can also create **custom stages** that appear between Replied and Meeting. Custom stages can be renamed, reordered, and deleted.

#### Pipeline Features

- **Search**: Filter leads by name, headline, or company
- **Stage changes**: Move leads between stages via dropdown
- **Delete leads**: Remove leads with confirmation
- **Infinite scroll**: Loads more leads as you scroll within each column
- **Pipeline stats**: Total leads, reply rate, and follow-up count displayed at the top
- **Per-account view**: Switch between LinkedIn accounts to see each account's pipeline
- **Active sequence badges**: See which sequence a lead is currently in

---

### Automatic Stage Detection

The CRM automatically detects and moves leads through stages based on your activity on LinkedIn. You do not need to update stages manually.

#### Connection Request Sent

When you send a connection request manually on LinkedIn, the extension intercepts it and:
- If the person is already a lead: moves them to **Requested**
- If they are not a lead: creates a new lead and sets them to **Requested**
- Captures the invitation URN for later withdrawal tracking

#### DM Sent

When you send a DM on LinkedIn, the extension detects the recipient and:
- Leads in New/Requested/Accepted are moved to **Contacted**
- Leads already in Contacted are checked for replies
- Leads in later stages get an activity timestamp update

#### Reply Detection

The extension continuously monitors open conversations. When a lead replies:
- The lead is automatically moved from **Contacted** to **Replied**
- A toast notification confirms the detection
- Uses fuzzy name matching to handle name variations, abbreviations, accents, and Cyrillic characters

#### Deal Signal Detection (Meeting, Won, Lost)

When a conversation is open, the extension uses AI to analyze the lead's messages for deal progression signals:
- If a meeting signal is detected: a popup suggests moving the lead to **Meeting**
- If a won or lost signal is detected: a popup suggests moving to **Won** or **Lost**
- You confirm or dismiss the suggestion. The popup auto-dismisses after 10 seconds.

---

### Add to Leads

On any LinkedIn profile page, the extension injects an **Add to Leads** button directly into the profile actions row (next to Connect, Message, and More).

- Click **Add to Leads** to create a new lead from the profile
- The extension automatically scrapes: name, headline, company, location, bio, and profile image
- If the person is already in your CRM, the button shows **In CRM**

---

### Check Connection Acceptances

Click **Check Acceptances** in the CRM to manually check which connection requests have been accepted.

- Fetches your recent LinkedIn connections via the API
- Cross-references them with leads in the **Requested** stage
- Accepted leads are automatically moved to the **Accepted** stage
- Uses fuzzy name matching to handle variations

---

### Follow-Up Management

The extension tracks which leads need follow-up:

- Leads in Contacted or Replied stages that exceed your configured follow-up threshold are flagged
- A **follow-up filter** toggle lets you see only leads that need follow-up
- Set a per-lead follow-up date: Tomorrow, In 3 days, In 1 week, In 1 month, or a custom date
- Generate an AI follow-up message with one click
- Configure the default follow-up days (1-30) in Settings

---

### Connection Withdrawal

Manage pending connection requests that have not been accepted:

- Configure a withdrawal threshold (number of days before a pending request should be withdrawn)
- The extension checks for leads past the threshold and shows a withdrawal modal
- Withdraw connections in batch (executed with delays for safety)
- Withdrawn leads are moved to the **On Hold** stage (cooldown period before they can be re-contacted)

---

### AI Messaging Assistant

On LinkedIn, the extension injects an AutoReach button into the message composer. Click it to open the assistant menu with six options:

#### 1. First Message

Generate a personalized opening message for a new contact.

- **Template mode**: Uses your saved first message template with basic personalization
- **Enhanced mode**: AI strategically crafts the message using all available context
- If the lead is in your CRM: shows their matched post/comment, buyer score, recent posts, and lets you generate from that context
- If the lead is not in your CRM: generates from their headline
- Displays lead intelligence: buyer probability, fit/intent/timing scores, suggested play, signal date

#### 2. Reply Suggestion

Get an AI-powered reply for an ongoing conversation.

- Parses the full conversation history from the page
- Sends conversation context plus lead data (CRM stage, matched post, buyer intelligence) to AI
- Detects objections in the lead's messages and surfaces an objection badge

#### 3. Follow Up

Generate a follow-up message when the lead has not replied.

- Uses full lead context: matched post, ICP match reason, buyer intelligence, recent posts
- Includes your currently selected offer for context

#### 4. Proofread

Improve a message you have already drafted.

- **Shorten**: Make your draft more concise and punchy
- **Enhance**: Make your draft more compelling and persuasive
- The result popup also offers Shorten and Regenerate options

#### 5. Analyse Lead

Opens the SDR Co-pilot with the prompt "Tell me everything you know about this person." Gives you a complete breakdown of the lead based on all available data.

#### 6. SDR Co-pilot

A persistent chat interface for freeform AI conversation about the current lead.

- Ask anything about the lead: strategy questions, objection handling, next steps
- Context includes: conversation history, CRM stage, buyer intelligence, matched post, ICP match reason, recent posts, company, bio, notes
- Chat history persists per lead across sessions
- Responses rendered with markdown formatting

#### Suggestion Popup

All AI-generated messages appear in a shared suggestion popup with these actions:

- **Insert**: Types the message into LinkedIn's input with a typewriter effect
- **Copy**: Copies to clipboard
- **Regenerate**: Get a new variant
- **Shorten**: Make it more concise
- **Custom Edit**: Type a free-form instruction (e.g., "make it more casual") and AI will adjust

---

### Post and Comment Reply Suggestions

The extension injects AI assist buttons into LinkedIn feed comment areas.

- Click the AutoReach button next to any comment input on a post
- The extension extracts the post text and author
- If the post has highlighted comments, a picker lets you choose whether to reply to the post or a specific comment
- AI generates a contextual comment based on the post content and your offer

---

### Analytics

Click the analytics icon in the CRM to see a pipeline overview:

- Counts per stage
- Conversion funnel (Lead > Contacted > Replied > Meeting > Won rates)
- Follow-up alerts with clickable links to filter your pipeline

---

### Settings

The Settings tab (LinkedIn only) includes:

- **Reply prompt**: Configure the AI reply prompt
- **First message template**: Set your default outreach template
- **Objection handling**: Add trigger/response pairs for common objections
- **Follow-up days**: Set the default follow-up threshold (1-30 days)
- **Withdrawal days**: Set how long before pending connections are flagged (1-30 days)
- **Custom stages**: Add, rename, reorder, and delete custom pipeline stages
- **Offers**: Select which offer to use for AI-generated messaging

All settings are saved with a unified save bar that detects unsaved changes.

---

## Troubleshooting

### "License Key Invalid"

Your license key has expired or is incorrect.

1. Go to [autoreach.tech/settings](https://autoreach.tech/settings)
2. Copy your current license key
3. Paste it into the extension
4. Click **Activate**

### "Extension Can't Access This Page"

The extension only works on linkedin.com and x.com/twitter.com.

### Session Expired

1. Open the **AutoReach Chrome Extension**
2. Click the **three dots** next to the account
3. Click **Reconnect**

Make sure you are logged into the social account in your browser before reconnecting.

### "Connection Not Detected"

LinkedIn connection acceptance detection requires:

1. The extension to be running
2. Your LinkedIn tab to stay open
3. The pending connection to still be in your CRM in the Requested stage

If detection is not working, use the **Check Acceptances** button in the CRM to manually trigger a check.

## Privacy and Security

- All CRM data is stored in your AutoReach account (encrypted)
- License key is stored locally in your browser (not shared)
- Extracted cookies are transmitted only to AutoReach servers (HTTPS encrypted)
- We never log your browsing history or profile views
- Keep your extracted cookies private
- Cookies expire over time (2-4 weeks). Reconnect via the extension (three dots > Reconnect).

Found a security issue? Email hello@autoreach.tech.

## Next Steps

- **[Connecting Accounts](connecting-accounts.md)**: Set up your X/Twitter and LinkedIn accounts
- **[Creating Your First Offer](create-offer.md)**: Define your target audience and outreach goals
- **[Quickstart](quickstart.md)**: Follow the complete setup guide
