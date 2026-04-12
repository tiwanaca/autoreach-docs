# Manual Controls

While AutoReach's AI is powerful, you're always in control. These manual controls let you step in, override automations, and handle conversations that need a human touch.

## Send Manual DMs

At any time, you can type and send a message directly without triggering AI response generation:

1. **Open a conversation** in your Inbox
2. **Type your message** in the message box
3. **Click Send**

### Key Behavior

- **Bypasses daily budget limits.** Manual DMs don't count against your daily action limits (DM count, daily limits, etc.)
- **Cancels pending AI responses.** If the AI had a response scheduled to send, it's immediately cancelled when you send a manual message
- **Sent instantly.** No human-like delay scheduling. Your message goes out right away
- **Shows as yours.** Recipients see it as coming from you, not from any automation

This is perfect when a prospect asks a very specific question, is ready to book a call, or you just need to add a personal touch.

{% hint style="tip" %}
**Pro Tip**: Jump in manually when prospects are hot. If they're asking detailed questions or hinting they want to move forward, your quick manual response will close faster than waiting for AI.
{% endhint %}

## AI ON/OFF Toggle

At the top of any conversation, toggle AI responses on or off:

- **AI ON**: AutoReach will generate responses automatically
- **AI OFF**: Only your manual messages will be sent; the AI won't reply

### Use Cases

- **Turn AI OFF** if you want to handle a specific prospect manually
- **Turn AI OFF** if the conversation has gotten too complex for automation
- **Turn AI ON** after you've manually closed a deal to keep the sequence moving for other leads

The toggle applies only to that single conversation, not your entire sequence.

{% hint style="info" %}
**Per-Conversation Control**: You might have AI ON for 90% of your leads and AI OFF for your hottest prospects. That's totally fine, and recommended.
{% endhint %}

## Star/Flag Important Conversations

Mark conversations as important for quick filtering:

1. **Click the star icon** next to a conversation name
2. **View all starred conversations** by filtering your Inbox

Use this to:

- Flag hot prospects you want to close this week
- Mark conversations that need follow-up tomorrow
- Highlight deals where you're waiting for a specific answer

Your starred conversations stay at the top of your Inbox for easy access.

## Cancel Pending AI Responses

If you've sent a manual message and realize the AI has a response scheduled to send, you can cancel it:

1. **Open the conversation**
2. **Look for any pending AI responses** (usually shown as "AI response scheduled for [time]")
3. **Click Cancel** to prevent it from sending

This is useful if:

- You sent a manual message that changes the conversation flow
- The AI response is no longer relevant
- You want to handle the next reply yourself

{% hint style="warning" %}
**Auto-Cancellation**: When you send a manual message, pending AI responses are automatically cancelled. You don't need to do this manually. It happens by default.
{% endhint %}

## Stale Conversation Follow-Ups

When a lead goes silent for a configured period (default: 5 days), AutoReach can automatically schedule a follow-up message.

### How It Works

1. **AI detects silence.** No messages from the lead for 5+ days
2. **Generates follow-up.** Creates a light-touch, fresh-angle message
3. **Schedules send.** Places it in the queue for your next outreach window
4. **Respects your schedule.** Follow-ups only send during your configured outreach hours

### Configuration

You can customize:

- **Silence threshold**: How many days before a follow-up is triggered (default: 5 days)
- **Follow-up message tone**: Customize the follow-up prompt to match your style
- **Enable/disable per sequence**: Some sequences might not need follow-ups

### AI Verification

Before sending a follow-up, the AI:

- **Checks conversation status.** Is the lead still active? Are there any recent indirect signals (likes, shares, comments)?
- **Verifies relevance.** Is a follow-up actually appropriate, or did the lead explicitly decline?
- **Avoids over-persistence.** Respects a max follow-up count per conversation (configurable, default: 3)

{% hint style="tip" %}
**Why Follow-Ups Work**: Most deals don't close on the first try. A light follow-up after 5 days can re-engage leads who were interested but distracted.
{% endhint %}

## Pausing and Resuming Sequences

While not strictly a per-conversation control, you can pause your entire sequence to halt all automations, then resume when ready.

### Pause

- Cancels all pending actions
- Pauses all active leads in the sequence
- Stops new actions from being scheduled

**Use case**: You're taking a week off and don't want messages going out.

### Resume

- Re-activates all paused leads
- Reschedules actions that were in progress
- Validates account health before resuming

**Use case**: You're back from vacation and want to jump back in.

## Conversation Controls Workflow

Here's a typical workflow using these controls:

```
1. Inbox: Prospect replies to cold DM
   |
2. AI generates response automatically
   |
3. You review the response (30s before send)
   |
4. Two options:
   a) It looks good - Let it send automatically
   b) Looks off - Send your own manual message instead
   |
5. Prospect replies to your manual message
   |
6. If they seem ready to close - Turn AI OFF and take over
   |
7. If you need time - Turn AI ON and let AI handle follow-ups
```

## Best Practices

### 1. Let AI Run Most Conversations

Don't jump in on every conversation. The AI is trained to handle most scenarios. Intervene only when:

- Responses feel off-brand
- A prospect is clearly hot and ready to close
- Technical details need your expertise

### 2. Review Pending Responses

Before pending AI responses send, take 30 seconds to:

- Read the message once more
- Make sure it aligns with what you'd say
- Cancel if it doesn't feel right

### 3. Use Stars for Prioritization

Star your top 5-10 hottest deals so you can focus on closing those while the AI handles volume.

### 4. Set Follow-Up Expectations

Customize your follow-up delay and max count. If your sales cycle is long, increase the silence threshold. If you have short cycles, decrease it.

### 5. Combine Manual and AI

The best results come from a mix:

- **AI handles discovery** (70% of conversations)
- **You handle objections and closing** (30% of conversations)

This balances volume with conversion.

{% hint style="info" %}
**The 70/30 Rule**: Let the AI do the heavy lifting on early-stage conversations while you focus your expertise on closing deals. This maximizes both volume and win rate.
{% endhint %}

---

## Next Steps

- Learn how the AI generates responses in [AI Response Engine](ai-response-engine.md)
- Understand when to intervene by reading [Conversation Stages](conversation-stages.md)
- Review your Inbox and conversation list in [Inbox & Real-Time Messaging](inbox.md)
