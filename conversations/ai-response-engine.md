# AI Response Engine

The AI Response Engine is the brain behind AutoReach's conversational outreach. It analyzes each incoming message, understands context, and generates personalized responses that feel human and move deals forward.

## How Responses Are Generated

Every time a prospect replies to you, AutoReach runs this flow:

```
Fetch Conversation History (last 10 messages)
        |
Extract Lead Context & Signals
        |
Classify Conversation Stage
        |
Build Stage-Specific Prompt
        |
Generate Response (Claude or GPT)
        |
Validate Length, Format, Patterns
        |
Schedule with Human-Like Delay (30s-5min)
        |
Send
```

This entire process takes seconds, but the resulting message looks like you took 5 minutes to write it.

## Model Selection

AutoReach uses **Claude as the primary AI model** with GPT as an intelligent fallback:

- Claude excels at nuance, context awareness, and natural conversational tone
- If Claude is unavailable, GPT seamlessly takes over
- Both models respect your tone examples and anti-consulting rules
- You don't need to choose. This happens automatically

## Anti-Consulting Rules

One of the biggest mistakes in B2B outreach is giving away too much value too early. AutoReach prevents this with built-in guardrails:

- Don't over-explain your solution before qualifying the prospect
- Don't answer every technical question in detail (save it for the call)
- Don't act like a free consultant
- Redirect curiosity to conversations: *"This is exactly what we'd dig into on a quick call"*

These rules are baked into the AI prompts and reinforced by response validation.

{% hint style="warning" %}
**When to Break the Rules**: If a prospect is genuinely ready to evaluate (they're asking detailed questions about your product), it's okay to share more value. The AI detects this via conversation stage and adjusts accordingly.
{% endhint %}

## Response Validation

Before any message is scheduled to send, AutoReach validates:

- **Length**: Does it match the conversation stage guidelines? (e.g., 50-80 words for openers)
- **Formatting**: No markdown, bullets, or overly formatted text in DMs
- **Anti-patterns**: See the blocked patterns list below
- **Tone match**: Does the response align with your provided tone examples?

Responses that fail validation are flagged for manual review before sending.

## Human-Like Delay Scheduling

To avoid looking like a bot, AutoReach doesn't send responses instantly. Instead:

- Responses are scheduled with a randomized delay between **30 seconds and 5 minutes**
- The delay varies per conversation to mimic natural response behavior
- You can still manually send messages immediately at any time
- The delay is configurable per sequence if needed

## Enforced Anti-Patterns

The AI is trained to **never use** these phrases and patterns:

- "I'd love to" (overused, unnatural)
- "Absolutely" or "For sure" (too formal/bot-like)
- "Happy to [verb]" (cliched)
- Em dashes in DMs
- Semicolons (;) in casual messages
- Bullet points in DMs (breaks conversational flow)
- "Worth a quick look?" (overused closing)

{% hint style="info" %}
**Why These Rules?** These phrases are telltale signs of AI-generated content. Real salespeople don't use them. Blocking them makes AutoReach responses indistinguishable from human outreach.
{% endhint %}

## What Always Works

Conversely, the AI is encouraged to:

- **Use contractions** ("I'm", "you're", "they're"). Formal writing sounds robotic
- **Use sentence fragments.** *"Totally understand. Budget is always tight."* This feels more natural
- **Match the lead's energy.** If they're casual, be casual. If they're formal, match that
- **Ask one question max per message.** Multiple questions feel like an interrogation
- **Skip the question sometimes.** Not every response needs to ask for something

## Stage-Specific Generation

The AI adapts response style based on where you are in the conversation:

- **Opener Reply**: Light acknowledgment, no pitch
- **Discovery**: Inquisitive, learning-focused
- **Value Prop**: Confident but consultative
- **Objections**: Direct, empathetic addressing
- **Soft Close**: Natural next-step suggestion
- **Graceful Exit**: Respectful, door-left-open
- **Follow Up**: Fresh angle, minimal pressure

See [Conversation Stages](conversation-stages.md) for the full stage breakdown.

## Performance Monitoring

The [Conversation Analyzer](conversation-analyzer.md) reviews your AI-generated conversations and suggests improvements:

- Are responses matching your tone?
- Are they hitting the word count targets?
- Are they moving deals forward or stalling?
- Should you adjust the prompt or tone examples?

Run regular analyses to continuously improve your AI's performance.

{% hint style="tip" %}
**Pro Tip**: After your first 20 conversations, run the Conversation Analyzer. You'll get specific feedback on whether to adjust your tone examples, prompts, or knowledge base.
{% endhint %}

## Next Steps

- Review how conversation stages shape responses in [Conversation Stages](conversation-stages.md)
- Customize your AI's voice with [Tone Examples & Customization](tone-examples.md)
- Optimize with the [Conversation Analyzer](conversation-analyzer.md)
