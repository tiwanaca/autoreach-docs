# Inbox

The Inbox is your unified view of all conversations across X and LinkedIn. Every DM and reply flows through here, with real-time message detection and AI status indicators.

## Conversation List

Your Inbox displays all conversations in a single, paginated list. Each conversation shows:

- Lead name and profile
- Platform (X or LinkedIn)
- Last message preview
- Timestamp of most recent activity
- AI status indicator
- Message count

### Starring Conversations

You can star important conversations to keep them easy to find. Click the star icon on any conversation to toggle it. Starred conversations can be used as a personal shortlist for high-priority leads or deals in progress.

### Unread Indicators

New inbound messages are tracked automatically. The Inbox shows an unread count so you can see at a glance how many conversations have new messages since you last checked. This count updates in real time as new messages arrive.

### Filtering

Filter conversations by:
- **Status** (Active, Replied, Meeting Booked, etc.)
- **Sequence** (specific sequence)
- **Platform** (X or LinkedIn)
- **Search query** (lead name)

Combine filters to narrow your view -- for example, show only LinkedIn conversations with a "Replied" status to focus on warm leads on that platform.

## Real-Time Message Detection

New messages on X are detected in real time via Twitter's native DM WebSocket connection (binary Thrift protocol). This means conversations appear in your Inbox as they happen without polling delays.

## AI Status Indicators

- **AI ON toggle**: Visible at the top of each conversation — indicates whether AI can auto-reply
- **Green indicators**: AI-generated responses (pending or sent)

## AI Control Per Conversation

Toggle AI on or off for individual conversations:

- **AI ON**: AI generates and sends responses automatically based on your prompts and tone examples
- **AI OFF**: Only your manual messages are sent

The toggle applies to that single conversation only, not the entire sequence.

## Call Briefs

Click the **Call Brief** button in any conversation to generate a pre-call preparation document. The brief pulls data from the lead's profile, conversation history, and buyer intelligence to give you talking points before a meeting.

See **[Call Briefs](../meetings/call-briefs.md)** for details.

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How AI generates responses
- **[Manual Controls](manual-controls.md)**: Send manual messages, toggle AI, manage conversations
- **[Tone Examples](tone-examples.md)**: Customize the AI's voice
