# Tone Examples & Customization

Tone examples are conversation samples that teach the AI exactly how you want to sound. They're the single most effective way to make AutoReach's responses feel authentic to your voice and sales style.

## What Are Tone Examples?

Tone examples are real (or realistic) conversation snippets that demonstrate:

- How you greet prospects
- How you ask questions
- How you respond to objections
- How you close opportunities
- Your casual language, humor, and energy level

The AI uses these examples to match your voice, word choice, sentence length, and conversational style in its generated responses.

## How They're Generated

When you create an offer, AutoReach auto-generates **21 tone examples** via two parallel AI calls:

- **11 conversation-building examples** (discovery, value prop, objections, etc.)
- **10 closing examples** (soft close, graceful exit, follow-up)

These examples capture different tones and scenarios so the AI has a diverse range to learn from.

### Deduplication

AutoReach automatically removes redundant or overly similar examples using **Jaccard similarity**. If two examples are more than **85% similar**, the weaker one is removed. This keeps your tone library focused and non-repetitive.

{% hint style="info" %}
**Jaccard Similarity**: A measure of how much two pieces of text overlap. Similarity > 0.85 means the examples are almost identical, so removing one saves the AI from learning the same pattern twice.
{% endhint %}

## Anti-Pattern Detection

During generation, AutoReach actively removes examples that contain:

- Overused phrases like "Worth a quick look?"
- Formal language ("I would", instead of "I'd")
- Bullet points and markdown (breaks DM flow)
- Em dashes and semicolons
- Over-explaining or giving away too much value

This ensures your tone library contains only high-quality, authentic examples.

## Contraction Enforcement

All examples are normalized to **use contractions**:

- "I'm" instead of "I am"
- "You're" instead of "You are"
- "They've" instead of "They have"

Contractions feel natural and conversational. Without them, the AI sounds robotic.

## How Tone Examples Are Retrieved

When the AI generates a response for a conversation, it:

1. **Detects the conversation stage** (Discovery, Objections, Soft Close, etc.)
2. **Finds similar tone examples** for that stage using **cosine similarity**
3. **Sets a similarity threshold** of 0.5 (on a scale of 0 to 1)

Only examples above the 0.5 threshold are used to inform the response. This keeps the AI focused on examples that match the current conversation stage and tone.

{% hint style="tip" %}
**Why 0.5 Threshold?**: A threshold of 0.5 means the AI looks for examples that are moderately similar to the current conversation. Too high (e.g., 0.9) and it would only find near-identical examples. Too low (e.g., 0.2) and it would pull in examples from the wrong stage.
{% endhint %}

## Reviewing and Editing Tone Examples

You can review, edit, or delete tone examples at any time:

1. **Open your sequence** → **Tone Examples** tab
2. **View all examples** by stage (Opener Reply, Discovery, Objections, etc.)
3. **Edit an example** to match your voice better
4. **Delete an example** if it doesn't fit your style
5. **Add custom examples** for specific scenarios you've handled well

### When to Edit

Edit tone examples if:

- The auto-generated examples are too formal or too casual
- They use language you'd never use
- They don't capture your sales style
- You've found a great response in a real conversation and want to replicate it

### When to Add

Add custom examples when:

- You've had a conversation that went really well and want the AI to match that energy
- A specific stage (like Objection Handling) needs more examples
- You want to capture a unique quirk of your voice (humor, specific jargon, etc.)

### When to Delete

Delete examples when:

- They contain anti-patterns (phrases you don't actually use)
- They don't match your voice
- They're redundant with other examples
- They're too long or too short compared to your actual style

{% hint style="warning" %}
**Deleting Examples**: Once deleted, examples won't be used to train future AI responses. Make sure you're not deleting something you actually like—you can always edit instead of delete.
{% endhint %}

## Matching Tone, Length, and Energy

The AI uses your tone examples to:

- **Match word choice** — If your examples use "totally" instead of "absolutely", the AI will too
- **Match sentence structure** — If your examples use short, punchy sentences, the AI follows suit
- **Match formality level** — If you're casual, the AI sounds casual
- **Match question style** — Do you ask open-ended or closed-ended questions?
- **Match energy** — Are you enthusiastic, matter-of-fact, or somewhere in between?

The more consistent your tone examples are, the more consistent the AI's responses will be.

## Pro Tips for Tone Examples

1. **Review after your first 5 conversations** — Have the AI responses matched your actual voice? If not, edit examples.

2. **Keep examples 40–120 words** — This range captures full conversational turns without being unwieldy.

3. **Mix stages** — Make sure you have examples for all 7 conversation stages. If you have 10 examples of Discovery and none of Objection Handling, the AI will struggle with objections.

4. **Use real conversations** — The best tone examples come from conversations that actually went well with prospects. Copy & paste them in!

5. **Update quarterly** — As your sales pitch evolves, refresh your tone examples to match your current voice.

---

## Next Steps

- Learn about all 7 conversation stages in [Conversation Stages](conversation-stages.md)
- See how the AI uses tone examples in [AI Response Engine](ai-response-engine.md)
- Review tone examples with the [Conversation Analyzer](conversation-analyzer.md)
