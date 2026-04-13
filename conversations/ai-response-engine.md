# AI Response Engine

The AI Response Engine generates contextual, stage-aware replies to incoming messages across X and LinkedIn.

## Response Flow

When a new inbound message is detected:

1. **Stage classification**: The conversation stage is identified (opener_reply, discovery, etc.)
2. **Objection check**: Message is checked for negative/sensitive content
3. **RAG context**: Knowledge base and tone examples are retrieved via semantic search
4. **System prompt assembly**: A multi-layer prompt is built with stage instructions, RAG context, tone examples, offer context, and conversation history
5. **AI generation**: The content AI model generates a response
6. **Human delay simulation**: A typing/composition delay is applied before sending
7. **Message delivery**: Sent via the appropriate platform API
8. **Database save**: Message saved and AI response count incremented

## Scheduling Architecture

The AI response system uses background scheduling, not WebSocket-based generation:

| Scheduler | Interval | Purpose |
|---|---|---|
| AI response scheduler | Every 60 seconds | Polls for due responses |
| Follow-up scheduler | Every 10 minutes | Detects stale conversations where the lead went silent |
| AI response worker | Concurrency 2 | Processes individual response jobs |

Rate limiting: Maximum **20 AI responses per 60 seconds** at the worker level.

Crash recovery: A uniqueness constraint on each conversation and inbound message prevents duplicate responses after crashes or retries.

## RAG Context

Each response includes relevant context retrieved via semantic search from your knowledge base (600 tokens) and tone examples (500 tokens). See [Knowledge Base](knowledge-base.md) for document management and [Tone Examples](tone-examples.md) for conversation samples.

## Stage-Specific Generation

The AI adapts response style based on the detected conversation stage:

- **Opener Reply**: Light acknowledgment, no pitch
- **Discovery**: Inquisitive, learning-focused
- **Value Prop**: Confident but consultative
- **Objection Handling**: Direct, empathetic
- **Soft Close**: Natural next-step suggestion
- **Follow Up**: Fresh angle, minimal pressure
- **Graceful Exit**: Respectful, door left open

## Anti-Consulting Rules

Built-in guardrails prevent giving away too much value before qualifying:

- Don't over-explain your solution before qualifying the prospect
- Don't answer every technical question in full detail
- Redirect curiosity to conversations: "This is exactly what we'd dig into on a quick call"

The AI detects when a prospect is genuinely evaluating (via stage detection) and adjusts accordingly.

## Max AI Responses Per Conversation

The "Max AI responses per conversation" setting on each sequence limits how many AI replies are sent in a single conversation:

- Value 0 = unlimited responses
- When the count is reached, AI is disabled on that conversation
- Also checked before queuing follow-up messages

## Conversation Follow-Ups

When a lead goes silent, the follow-up scheduler can automatically re-engage:

| Setting | Default | Range |
|---|---|---|
| Conversation follow-up enabled | false | — |
| Follow-up wait days | 3 | 1–30 |
| Max follow-up count | 2 | 1–10 |

The follow-up scheduler runs every 10 minutes, checking for conversations where the lead hasn't responded within the configured wait period. Follow-up messages are generated with a fresh angle and queued for delivery.

## Next Steps

- **[Conversation Stages](conversation-stages.md)**: How stages are detected and classified
- **[Tone Examples](tone-examples.md)**: Customize the AI's voice
- **[Knowledge Base](knowledge-base.md)**: Add context for smarter responses
