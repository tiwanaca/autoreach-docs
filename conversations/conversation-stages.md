# Conversation Stages

AutoReach divides your outreach conversations into 7 distinct stages. Each stage has its own tone, goals, and word-count targets. The AI automatically detects which stage you're in and adapts accordingly.

## The 7 Stages

### 1. Opener Reply
**Triggered**: Lead just responded to your cold DM  
**Length Target**: 50–80 words  
**Goal**: Acknowledge their message, be genuinely interested, light touch

**AI Behavior**:
- Short and conversational
- Reference something specific they said
- Don't pitch yet—you're just getting to know them
- Keep it human and warm

**Example**:
> *Good call. Yeah, most teams we talk to are running into this same issue. How long have you been managing this in-house?*

---

### 2. Discovery
**Triggered**: You're asking questions and learning about their situation  
**Length Target**: 70–100 words  
**Goal**: Dig deeper into their pain, timeline, and constraints

**AI Behavior**:
- Curious and investigative
- Ask targeted, specific questions
- Build on what they've already shared
- Show you understand their world
- One question per message (sometimes two if they're related)

**Example**:
> *Makes sense. When you say the process is manual, how many hours a week is your team spending on it? And is this something your boss has flagged as a priority to fix, or more of a "nice-to-have"?*

---

### 3. Value Prop
**Triggered**: Lead is asking about your solution or you're introducing it  
**Length Target**: 80–120 words  
**Goal**: Show how you solve their specific problem without overselling

**AI Behavior**:
- Confident but consultative
- Tie your value directly to what they mentioned
- Share relevant case studies or proof points (from knowledge base)
- Position it as a conversation topic, not a done deal
- Avoid giving away too much (anti-consulting rule)

**Example**:
> *We've worked with teams like yours at [Company] who were doing this manually. Once they switched, they cut that time in half and freed up cycles for higher-impact work. Worth having a quick conversation to see if we could do the same for your team?*

---

### 4. Objections
**Triggered**: Lead raises a concern, budget question, or pushback  
**Length Target**: 50–100 words  
**Goal**: Address concerns directly and compassionately

**AI Behavior**:
- Validate their concern first ("That makes sense")
- Address the objection head-on
- Provide a specific counter-point or alternative
- Don't get defensive
- Move forward with a next step

**Example**:
> *Totally get that—cost is always a conversation. Here's the thing: most teams see ROI within 60 days because of the time savings. Plus we offer a free 30-day trial so you can test it with your team before committing.
 Ready to see it?*

---

### 5. Soft Close
**Triggered**: Lead seems ready to move forward or book a call  
**Length Target**: 40–70 words  
**Goal**: Suggest the next step naturally, without being pushy

**AI Behavior**:
- Calm and collected
- Suggest a specific, easy next step (call, demo, trial)
- Make it feel collaborative, not transactional
- Reference what made them interested

**Example**:
> *Perfect. Let's get you set up with a 20-min demo so you can see it in action. How's Tuesday at 2pm for you?*

---

### 6. Graceful Exit
**Triggered**: Lead declines or goes silent for a very long time  
**Length Target**: 30–50 words  
**Goal**: Exit with dignity, leave the door open for the future

**AI Behavior**:
- Respectful and low-pressure
- Acknowledge their decision
- Offer a soft re-engagement point
- Don't push back or be passive-aggressive

**Example**:
> *Totally understand. If priorities change and you want to revisit this, feel free to reach out. Happy to help whenever you're ready.*

---

### 7. Follow Up
**Triggered**: Lead went silent for a period (configurable); you're re-engaging  
**Length Target**: 50–80 words  
**Goal**: Get back on their radar with a fresh angle or new information

**AI Behavior**:
- Light touch, not pushy
- Reference something new (new feature, case study, benchmark data)
- Acknowledge the silence without calling it out directly
- Give them an easy reason to engage again

**Example**:
> *Quick thought: [New thing relevant to them]. Reminds me of our conversation about [their specific pain]. Curious if this changes anything for you?*

---

## Automatic Stage Detection

You don't need to manually tag conversations. AutoReach automatically detects the stage by analyzing:

- **Message history**: How many messages have been exchanged?
- **Conversation content**: Are they asking about your product? Raising objections? Going silent?
- **Lead signals**: Did they say "yes"? Did they say "no"? Are they hot or cold?
- **Sentiment and intent**: Extract intent from message text

The AI uses this analysis to pick the right stage and adjust its response accordingly.

{% hint style="info" %}
**No Perfect Classification**: Sometimes conversations jump between stages (e.g., from Soft Close back to Objections if they raise concerns). The AI is smart enough to re-classify mid-conversation.
{% endhint %}

## Word Count Targets

Each stage has a word-count range to keep messages natural and readable:

| Stage | Min Words | Max Words | Why? |
|-------|-----------|-----------|------|
| Opener Reply | 50 | 80 | Short and punchy—don't overwhelm a cold lead |
| Discovery | 70 | 100 | Room to ask thoughtful questions |
| Value Prop | 80 | 120 | Need space to explain your value without overselling |
| Objections | 50 | 100 | Direct, but not dismissive |
| Soft Close | 40 | 70 | Keep it simple and easy |
| Graceful Exit | 30 | 50 | Brief, respectful goodbye |
| Follow Up | 50 | 80 | Fresh but not overwhelming |

These targets prevent your messages from being too long (which kills response rates) or too short (which feels dismissive).

{% hint style="tip" %}
**Pro Tip**: If you notice the AI consistently overshooting word counts in a certain stage, review your tone examples for that stage. You might have examples that are naturally longer, which trains the AI to write longer.
{% endhint %}

## How to Use Stages

As you build your outreach strategy:

1. **Upload relevant tone examples** for each stage to your sequence
2. **Make sure your knowledge base** has stage-relevant context (e.g., objection-handling docs for the Objections stage)
3. **Let the AI auto-detect** stages and adapt responses
4. **Review responses** early on to see if stage detection is accurate
5. **Use the Conversation Analyzer** to see if your tone matches stage expectations

---

## Next Steps

- Learn how to customize stages with [Tone Examples & Customization](tone-examples.md)
- Deep dive into the [AI Response Engine](ai-response-engine.md)
- Build your [Knowledge Base](knowledge-base.md) to power stage-specific responses
