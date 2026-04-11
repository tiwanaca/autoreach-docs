# Inbox & Real-Time Messaging

The Inbox is your unified command center for all conversations across X/Twitter and LinkedIn. Every DM, reply, and engagement flows through here in real time, so you never miss a prospect.

## Unified Conversation View

Your Inbox displays all conversations from both X and LinkedIn in a single, chronologically sorted list. Each conversation shows:

- **Lead name** and profile picture
- **Platform badge** (X or LinkedIn)
- **Last message** preview
- **Timestamp** of most recent activity
- **AI status** indicator (see below)
- **Message count** for context

Search and filter by lead name, platform, or conversation status to quickly find what you need.

## Real-Time Message Detection

AutoReach detects new messages as they arrive using platform-optimized methods:

### X/Twitter
Uses **WebSocket connections** (the same real-time protocol X's web UI uses) for instant message detection. Your conversations appear in the Inbox within milliseconds of arrival.

### LinkedIn
Uses **adaptive polling** with intervals between 1-15 minutes. Message detection depends on your account activity and LinkedIn's rate limits.

{% hint style="info" %}
**Encrypted DM Support**: AutoReach supports encrypted DMs on X/Twitter via identity seed encryption. Your most sensitive conversations stay secure end-to-end.
{% endhint %}

## Message Deduplication

AutoReach prevents duplicate messages from being processed twice:

- **X messages** are tracked via `twitter_message_id`
- **LinkedIn messages** are tracked via `linkedin_message_urn`

Each message is logged exactly once, even if you're running multiple sequences or devices.

## AI Status Indicators

Look for these visual cues in your conversation list:

- **Green bubbles** = AI-generated responses (either pending or already sent)
- **Regular text** = Your manual messages or incoming lead messages
- **AI ON toggle** (top of conversation) = AI is enabled for that conversation and can reply automatically

## AI Control Per Conversation

At the top of any conversation thread, you'll see an **AI ON/OFF toggle**. Toggle it to:

- **Enable AI** - AutoReach will generate and send responses using your configured prompts and tone examples
- **Disable AI** - Only your manual messages will be sent; AI responses are blocked for this conversation

This gives you fine-grained control even within an active sequence.

## Pre-Call Preparation

Before an important conversation, click the **Call Brief button** to generate a context summary. AutoReach extracts:

- Prospect's pain points (from conversation history)
- Their company and role signals
- Key topics they've mentioned
- Recommended talking points
- Recent objections and how you addressed them

Use this 2-minute brief to walk into calls fully prepared.

{% hint style="tip" %}
**Conversation Count**: You'll see your total message count at the top of your Inbox (e.g., "567 conversations"). This includes all X and LinkedIn DMs tracked by AutoReach.
{% endhint %}

## Next Steps

- Learn how AI generates responses in the [AI Response Engine](ai-response-engine.md)
- Customize AI behavior with [Tone Examples](tone-examples.md)
- Build your [Knowledge Base](knowledge-base.md) for smarter responses
