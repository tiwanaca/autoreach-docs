# Chrome Extension CRM Pipeline

The AutoReach Chrome Extension brings your entire CRM pipeline directly into your browser. Manage leads, track progress, and run outreach without leaving your daily workflow on LinkedIn and X.

## The Pipeline

Your leads move through a clean, visual pipeline right in the extension:

**new > requested > accepted > contacted > replied > meeting > won/lost**

Each stage represents a moment in the lead journey:
- **new** - freshly added to AutoReach
- **requested** - connection request or first message sent
- **accepted** - connection accepted or first reply received
- **contacted** - ongoing conversation started
- **replied** - they have engaged with your outreach
- **meeting** - meeting booked
- **won** - closed deal
- **lost** - disqualified or no longer pursuing

## Moving Leads Through the Pipeline

**Drag and drop:** Manually move leads between stages by dragging their card within the pipeline view.

**Auto-progression:** Leads automatically advance through stages as sequence activity progresses. A lead moves from "new" to "requested" when a DM is sent, and from "contacted" to "replied" when they respond.

{% hint style="info" %}
You can always override auto-progression by manually dragging a lead to a different stage if needed.
{% endhint %}

## Pipeline Analytics

The extension includes a built-in analytics dashboard showing:
- **Lead count per stage** - how many leads are in each pipeline stage
- **Conversion rates** - percentage of leads moving from one stage to the next
- **Stage velocity** - average time spent in each stage
- **Total pipeline value** - based on average deal size for your offer

Use these metrics to identify bottlenecks and optimize your outreach.

{% hint style="tip" %}
Check your analytics weekly to spot trends. If leads are stuck in "contacted," you may need to adjust your follow-up messaging.
{% endhint %}

## LinkedIn Connection Acceptance Detection

The extension monitors your LinkedIn account in real-time for connection acceptances.

**How it works:**
- When someone accepts your connection request, the extension detects it automatically
- The system uses fuzzy name matching to link the connection to the corresponding lead in AutoReach
- The lead's status updates to **"accepted"** in your pipeline

This means you do not have to manually track who has accepted. It is all automatic.

{% hint style="success" %}
Fuzzy matching is smart enough to handle common name variations, misspellings, and nickname differences, so connections are linked accurately even if the name is not exact.
{% endhint %}

## Security: Cyrillic Character Detection

The extension includes built-in phishing protection that detects lookalike profiles using Cyrillic characters.

**Why this matters:** Bad actors often use Cyrillic characters that visually resemble Latin letters to create fake profiles that look legitimate. The extension flags these suspicious profiles to protect you.

If a profile is flagged as potentially dangerous, the extension will warn you before you interact with it.

{% hint style="warning" %}
Be cautious with flagged profiles. Do not accept connection requests or share sensitive information with accounts that trigger security warnings.
{% endhint %}

## Lead Linking to AutoReach

When you visit a LinkedIn or X profile, the extension automatically extracts the profile data and links it to leads in AutoReach.

**This means:**
- You see at a glance which AutoReach leads match the profiles you are viewing
- You can start conversations knowing the lead is already in your system
- Lead context from AutoReach (buyer score, signals, conversation history) is just a click away

## Active Sequence Tracking

Each lead shows which sequences they are enrolled in, visible in the extension sidebar.

You will see:
- Sequence name
- Current step
- Next scheduled action
- Days in sequence

This keeps you aware of where each lead is in your outreach without switching apps.

{% hint style="tip" %}
Use active sequence tracking to avoid duplicate outreach. If a lead is in multiple sequences, you will see it in the extension.
{% endhint %}

## Real-Time Messaging Overlay

When you are chatting with someone on LinkedIn or X, a lightweight messaging overlay appears showing:
- Lead profile and buyer intelligence
- Conversation history from AutoReach
- Recommended next messages (if AI suggestions are enabled)
- Quick action buttons (link to AutoReach, add to sequence, etc.)

This keeps relevant context visible while you are actually in the conversation.

{% hint style="info" %}
The messaging overlay is lightweight and does not interfere with normal LinkedIn/X messaging. You can minimize or close it anytime.
{% endhint %}

## Account Authentication & Cookie Extraction

To connect your LinkedIn and X accounts to AutoReach, the extension securely extracts authentication cookies from your browser.

**How this works:**
- You authorize the extension to access your account cookies
- The extension extracts the authentication tokens needed to send messages on your behalf
- AutoReach stores these tokens securely and uses them to authenticate API calls
- Your actual password is never shared or stored

{% hint style="success" %}
Cookie-based authentication is more secure than password authentication because it avoids storing passwords in the cloud. You can revoke access anytime in the extension settings.
{% endhint %}

**To connect an account:**
1. Click the **Connect Account** button in the extension
2. Select LinkedIn or X
3. Review the permissions and click **Authorize**
4. The extension extracts your authentication cookies securely
5. You are connected. The extension can now send messages and track activity

## Bridging Browser and Outreach

The Chrome Extension is the bridge between your daily browsing and your outreach strategy. You can:

- Find prospects on LinkedIn and X, then instantly add them to AutoReach
- See lead context and conversation history while messaging
- Track pipeline stages without leaving your browser
- Monitor sequence activity in real-time
- Generate call briefs before meetings
- Take next steps all in one place

{% hint style="success" %}
Install the extension and pin it to your toolbar for quick access. It is designed to fit seamlessly into your workflow without slowing you down.
{% endhint %}

## Next Steps

- **[Installing the Chrome Extension](../getting-started/chrome-extension.md)**: Get started with installation and license activation
- **[Call Brief Generation](call-briefs.md)**: Prepare for meetings with AI-generated briefs from your pipeline
