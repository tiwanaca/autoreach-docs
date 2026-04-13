# Conversation Stages

AutoReach classifies conversations into 7 stages. Each stage has its own tone and goals. The AI detects the current stage and adapts its responses accordingly.

## The 7 Stages

### 1. Opener Reply

**Triggered**: Lead just responded to your cold DM.
**Goal**: Acknowledge their message, show genuine interest, keep it light. No pitching.

### 2. Discovery

**Triggered**: You're learning about their situation.
**Goal**: Ask targeted questions about their pain points, timeline, and constraints.

### 3. Value Prop

**Triggered**: Lead is asking about your solution or you're introducing it.
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

## Stage Detection

The system uses message patterns and conversation signals to determine the current stage. A lightweight AI model classifies the stage based on the full conversation history.

Conversations can move between stages non-linearly — for example, from Soft Close back to Objection Handling if the lead raises new concerns. The classifier re-evaluates on every new message.

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How stage-specific responses are generated
- **[Tone Examples](tone-examples.md)**: Customize the AI's voice per stage
- **[Knowledge Base](knowledge-base.md)**: Add stage-relevant context for the AI to reference
