# Manual Controls

You always have full control over conversations. These controls let you step in, override AI responses, and handle conversations that need a human touch.

## Send Manual Messages

Send a message directly from the Inbox without AI involvement:

1. Open a conversation
2. Type your message
3. Click Send

Manual messages are:
- **Sent instantly** — no human-like delay scheduling
- **Not subject to daily limits** — manual DMs don't count against your action limits
- **Auto-cancel pending AI responses** — if the AI had a response queued, it's immediately cancelled when you send a manual message

## AI ON/OFF Toggle

At the top of any conversation, toggle AI responses:

- **AI ON**: AI generates and sends responses automatically
- **AI OFF**: Only your manual messages are sent

The toggle applies to that single conversation only. You can have AI enabled for most conversations while handling your hottest prospects manually.

## Conversation Follow-Ups

When a lead goes silent, AutoReach can automatically send follow-up messages to re-engage them.

### Configuration (Per-Sequence)

| Setting | Default | Range |
|---|---|---|
| Follow-up enabled | false | — |
| Wait days | 3 | 1–30 |
| Max follow-ups | 2 | 1–10 |

When the system detects a conversation where the lead hasn't responded within the configured wait period, it generates a fresh-angle follow-up message and queues it for delivery.

Follow-ups respect:
- The max follow-up count per conversation
- The max AI responses per conversation limit
- Your activity window

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How AI generates responses
- **[Conversation Stages](conversation-stages.md)**: When to intervene based on stage
- **[Inbox](inbox.md)**: Managing your conversation list
