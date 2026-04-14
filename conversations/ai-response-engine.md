# AI Response Engine

The AI Response Engine generates contextual, stage-aware replies to incoming messages across X and LinkedIn.

## Response Flow

When a new inbound message is detected, AutoReach:

1. **Classifies the conversation stage** (Opener Reply, Discovery, Objection Handling, etc.)
2. **Retrieves relevant context** from your knowledge base and tone examples
3. **Generates a response** tailored to the stage, lead context, and your voice
4. **Sends with natural timing** to avoid instant robotic replies

## Conversation Stages

AutoReach classifies conversations into 7 stages. Each stage has its own tone and goals. The AI detects the current stage and adapts its responses accordingly.

### 1. Opener Reply

**Triggered**: Lead just responded to your cold DM.
**Goal**: Acknowledge their message, show genuine interest, keep it light. No pitching.

### 2. Discovery

**Triggered**: You are learning about their situation.
**Goal**: Ask targeted questions about their pain points, timeline, and constraints.

### 3. Value Prop

**Triggered**: Lead is asking about your solution or you are introducing it.
**Goal**: Connect your value directly to what the lead mentioned, using relevant proof points from your knowledge base.

### 4. Objection Handling

**Triggered**: Lead raises a concern, budget question, or pushback.
**Goal**: Validate the concern first, then address it with a specific counter-point and clear next step.

### 5. Soft Close

**Triggered**: Lead seems ready to move forward or book a call.
**Goal**: Propose a specific, easy next step without being pushy.

### 6. Follow Up

**Triggered**: Lead went silent for a configurable period.
**Goal**: Re-engage with a fresh angle or new information that gives the lead a reason to respond.

### 7. Graceful Exit

**Triggered**: Lead declines or the conversation has reached a dead end.
**Goal**: Exit respectfully and leave the door open for the future.

### Stage Detection

The AI classifies the current stage based on the full conversation history. Conversations can move between stages non-linearly. For example, from Soft Close back to Objection Handling if the lead raises new concerns. The classifier re-evaluates on every new message.

## Anti-Consulting Guardrails

The AI is designed to avoid giving away too much value before qualifying a prospect. It redirects detailed technical questions toward a call or meeting rather than answering everything in a DM. This keeps conversations moving toward a booking rather than becoming free consulting sessions.

## Max AI Responses Per Conversation

The "Max AI responses per conversation" setting on each sequence limits how many AI replies are sent in a single conversation:

- Value 0 = unlimited responses
- When the count is reached, AI is disabled on that conversation
- Also checked before queuing follow-up messages

## Conversation Follow-Ups

When a lead goes silent, the follow-up scheduler can automatically re-engage:

| Setting | Default | Range |
|---|---|---|
| Follow-up enabled | false | - |
| Wait days | 3 | 1-30 |
| Max follow-ups | 2 | 1-10 |

When a lead has not responded within the configured wait period, a follow-up message is generated with a fresh angle and sent automatically.

Follow-ups respect:
- The max follow-up count per conversation
- The max AI responses per conversation limit
- Your activity window

## Next Steps

- **[Tone and Knowledge Base](tone-and-knowledge.md)**: Customize the AI's voice and provide sales context
- **[Conversation Analyzer](conversation-analyzer.md)**: AI suggestions for improving your sequences
