# Conversation Stages

AutoReach classifies conversations into 7 stages. Each stage has its own tone and goals. The AI detects the current stage and adapts its responses accordingly.

## The 7 Stages

### 1. Opener Reply (`opener_reply`)

**Triggered**: Lead just responded to your cold DM.
**Goal**: Acknowledge their message, show genuine interest, keep it light. No pitching.

### 2. Discovery (`discovery`)

**Triggered**: You're learning about their situation.
**Goal**: Ask targeted questions about their pain points, timeline, and constraints.

### 3. Value Prop (`value_prop`)

**Triggered**: Lead is asking about your solution or you're introducing it.
**Goal**: Connect your value directly to what the lead mentioned, using relevant proof points from your knowledge base.

### 4. Objection Handling (`objection_handling`)

**Triggered**: Lead raises a concern, budget question, or pushback.
**Goal**: Validate the concern first, then address it with a specific counter-point and clear next step.

### 5. Soft Close (`soft_close`)

**Triggered**: Lead seems ready to move forward or book a call.
**Goal**: Propose a specific, easy next step without being pushy.

### 6. Follow Up (`follow_up`)

**Triggered**: Lead went silent for a configurable period.
**Goal**: Re-engage with a fresh angle or new information that gives the lead a reason to respond.

### 7. Graceful Exit (`graceful_exit`)

**Triggered**: Lead declines or the conversation has reached a dead end.
**Goal**: Exit respectfully and leave the door open for the future.

## Stage Detection

Stage detection uses a two-layer approach:

**Heuristic shortcuts** (no AI call needed):
- If message count is 1 or fewer → always `opener_reply` (confidence 1.0)
- If objection count is 2 or more → always `graceful_exit` (confidence 1.0)

**AI classification**: For all other cases, a lightweight AI model classifies the stage based on the full conversation history.

**Fallback**: If the AI call fails, a keyword-based rule system runs, checking for exit signals, buying signals, information-seeking signals, and message length.

Conversations can move between stages non-linearly — for example, from `soft_close` back to `objection_handling` if the lead raises new concerns. The classifier re-evaluates on every new message.

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How stage-specific responses are generated
- **[Tone Examples](tone-examples.md)**: Customize the AI's voice per stage
- **[Knowledge Base](knowledge-base.md)**: Add stage-relevant context for the AI to reference
