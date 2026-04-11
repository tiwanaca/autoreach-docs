# Conversation Analyzer

The Conversation Analyzer is your AI coaching assistant. It reviews your conversations, spots what's working and what isn't, and generates actionable suggestions to improve your outreach voice over time.

## What It Does

The Analyzer examines:

- **Positive outcomes** — Conversations where leads replied enthusiastically, asked about your product, or booked calls
- **Negative outcomes** — Conversations that stalled, received objections, or ended prematurely
- **Tone alignment** — Are your AI-generated responses actually matching your tone examples?
- **Stage fit** — Are responses appropriate for the conversation stage detected?
- **Word count adherence** — Are responses hitting the target length for their stage?

Based on this analysis, the Analyzer generates **3–7 actionable suggestions** to optimize your outreach.

## Suggestion Types

The Analyzer generates four types of suggestions:

### 1. Modify Tone Example

**Use case**: A tone example isn't working well or isn't matching your actual voice.

**What happens**: The Analyzer identifies an existing example that's misaligned with your conversation outcomes and suggests you modify it.

**Example**:
> *Your tone example "Let me send you a resource" led to positive conversations in Discovery stage, but your actual replies use "I'll grab you a doc." Consider updating the example to match your real language.*

### 2. Add Tone Example

**Use case**: A conversation stage is missing examples or has too few.

**What happens**: The Analyzer identifies a gap (e.g., no Objection Handling examples) and suggests you add new examples.

**Example**:
> *You don't have many Objection Handling examples. I've seen "Great question. Here's the reality..." work well in your conversations. Add this as a new example to improve objection responses.*

### 3. Remove Tone Example

**Use case**: A tone example is consistently underperforming or contains problematic patterns.

**What happens**: The Analyzer flags an example that leads to stalled conversations or contains anti-patterns.

**Example**:
> *The example "I'd absolutely love to help" uses an anti-pattern ("I'd love to") that doesn't resonate with your prospects. Consider removing it.*

### 4. Modify Prompt

**Use case**: Your core AI prompt needs adjustment.

**What happens**: The Analyzer suggests changes to your main AI system prompt to better reflect your sales style or strategy.

**Example**:
> *Your current prompt emphasizes product features, but your successful conversations focus on pain points and ROI. Suggest updating the prompt to lead with pain point alignment.*

{% hint style="info" %}
**Prompt Modifications**: These are advanced suggestions. Most users won't need to modify their prompt frequently—tone examples usually handle voice adjustment. But if you have a specific strategy shift, prompt modifications can help.
{% endhint %}

## How to Use Suggestions

### 1. Run Analysis

Click **Analyze Conversations** in your sequence settings. The Analyzer will:

- Fetch your last 20-50 conversations (depending on availability)
- Classify outcomes (positive, neutral, negative)
- Identify patterns and misalignments
- Generate suggestions (usually takes 30–60 seconds)

### 2. Review Suggestions

The Analyzer presents suggestions one by one with:

- A clear explanation of why it's suggesting this
- Evidence from your conversations (e.g., "This phrase led to 3 stalled conversations")
- The specific change to make

### 3. Apply One-Click

For each suggestion, you can:

- **Apply** — Implement the change immediately
- **Dismiss** — Skip this suggestion (it won't appear again)
- **Edit** — Modify the suggestion before applying (e.g., tweak the wording)

### 4. Monitor Results

After applying suggestions, monitor your next 10–15 conversations:

- Are response rates improving?
- Are conversations moving to later stages?
- Do responses feel more authentic?

If you're seeing improvements, great! If not, you can always revert or try a different suggestion.

{% hint style="tip" %}
**When to Run Analysis**: After your first 20 conversations, then monthly as you accumulate more data. Early analysis is less accurate because the sample size is small.
{% endhint %}

## Iterative Improvement

The Analyzer is designed for iteration:

1. **Week 1**: Run analysis after 20 conversations
2. **Apply suggestions**: Update tone examples and prompts
3. **Week 2-3**: Let the AI operate with new settings
4. **Week 4**: Run analysis again on the next batch of conversations
5. **Repeat**: Continuously refine

This cycle helps you build a feedback loop where your outreach continuously improves.

## What the Analyzer Can't Do

The Analyzer is powerful but has limits:

- **It can't assess lead quality** — If a lead is a poor fit, no tone example will help
- **It can't predict outcomes** — A great response doesn't guarantee a deal (timing, budget, priorities matter)
- **It needs sample size** — Running analysis on 5 conversations is less reliable than 50
- **It can't suggest revenue impact** — It focuses on conversational quality, not pipeline value

Use the Analyzer for conversational improvement, but combine it with your own sales judgment.

{% hint style="warning" %}
**Manual Review**: Always review suggestions before applying. The Analyzer is smart, but you know your business best. If a suggestion doesn't feel right, dismiss it.
{% endhint %}

## Examples

### Example 1: Tone Misalignment

**Problem**: Your tone examples are formal ("I would"), but your actual conversations are casual ("I'd").

**Analyzer Output**:
> Modify Tone Example: "I would love to hop on a call" → "I'd love to hop on a call" (but also matches the contraction preference and removes overused phrase)

**Better suggestion**: Remove this example entirely (anti-pattern) and add a real response like "Let's jump on a call and dig into this."

---

### Example 2: Missing Stage

**Problem**: You have lots of Discovery examples but nothing for Objections.

**Analyzer Output**:
> Add Tone Example for Objections stage: "I hear that. Budget is always the first hurdle. Here's what we usually see..." - This response led to 2 positive replies in your recent conversations.

**What you do**: Approve and add this example. Now the AI has better templates for handling budget objections.

---

### Example 3: Anti-Pattern

**Problem**: One of your auto-generated examples uses "Worth a quick look?"

**Analyzer Output**:
> Remove Tone Example: "Let me send you this—worth a quick look?" (anti-pattern). This phrase appears in 3 conversations that stalled.

**What you do**: Approve the removal. The AI will stop using this phrase.

---

## Next Steps

- Review your tone examples in [Tone Examples & Customization](tone-examples.md)
- Understand conversation stages in [Conversation Stages](conversation-stages.md)
- Apply suggestions to refine your [Knowledge Base](knowledge-base.md) as well
