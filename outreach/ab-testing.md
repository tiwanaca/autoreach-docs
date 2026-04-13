# A/B Testing with the Simulator

The Conversation Simulator includes a built-in **A/B Compare** mode that runs the same scenario with two different AI prompts side by side. This lets you see exactly how prompt changes affect conversation quality before applying them to live sequences.

For full simulator instructions, see [Simulation](simulation.md).

## How A/B Compare Works

1. Open the simulator and select a sequence, lead, and **Automatic** mode
2. Toggle **A/B Compare** on in the toolbar
3. The simulator creates two conversation slots: **Prompt A** (your current AI prompt) and **Prompt B** (an editable copy)
4. Edit Prompt B with your changes — different tone, different instructions, different strategy
5. Both conversations run simultaneously against the same lead and persona
6. Each slot gets its own scorecard so you can compare results directly

Both conversations use the same lead data, the same persona presets, and the same DM template — only the AI prompt differs. This isolates the impact of your prompt changes.

## What to Test

### Tone Shifts

Compare a professional prompt against a casual one. For example:

- **Prompt A:** "Be professional and consultative. Use industry terminology."
- **Prompt B:** "Be conversational and friendly. Keep it simple."

Watch how each handles the same lead persona and check which produces better scorecard results.

### Objection Handling

Test different approaches to pushback:

- **Prompt A:** "When the lead pushes back on price, acknowledge their concern and offer a case study."
- **Prompt B:** "When the lead pushes back on price, reframe the conversation around ROI."

Use the "Price Sensitive" or "Hard to Convince" persona to trigger objections.

### Conversation Strategy

Compare different approaches to moving the conversation forward:

- **Prompt A:** "Ask discovery questions before pitching. Understand their situation first."
- **Prompt B:** "Lead with value. Share a relevant insight and suggest a call."

### Length and Detail

Test verbose vs. concise instructions:

- **Prompt A:** A detailed prompt with specific instructions for each conversation stage
- **Prompt B:** A minimal prompt that gives the AI more freedom

## Reading the Results

After both conversations finish, compare the scorecards side by side:

| Metric | What to Compare |
|---|---|
| Objection Handling | Which prompt addressed pushback more effectively? |
| Tone Consistency | Which maintained a more natural voice throughout? |
| Relevance | Which stayed more focused on the lead's actual needs? |
| Naturalness | Which conversation felt less scripted? |
| Goal Completed | Did one prompt reach a meeting booking while the other stalled? |
| Turns to Close | Which reached the goal faster? |

## Tips for Effective A/B Testing

1. **Change one thing at a time.** If you change tone, strategy, and length all at once, you cannot tell which change made the difference.

2. **Run multiple comparisons.** Test with at least 3-5 different leads and personas. A prompt that works well with an enthusiastic lead may fail with a skeptical one.

3. **Use challenging personas.** Easy leads do not differentiate prompts well. Use "Hard to Convince", "Skeptical", or "Uses Competitor" to stress-test.

4. **Check the debug panel.** Click individual messages to see how the AI interpreted the conversation stage, what knowledge base content it pulled, and what signals it detected. This reveals *why* one prompt outperformed the other.

5. **Follow up with batch mode.** Once you have a winning prompt, run a batch of 10-25 simulations across all personas to validate it at scale before going live.

6. **Apply and iterate.** When you find a better prompt, update your sequence settings. Then run another A/B test with the next improvement.

## Next Steps

- **[Simulation](simulation.md)**: Full guide to the Conversation Simulator
- **[Cold DM Generation](cold-dm-generation.md)**: How AI generates personalized first messages
- **[Template Variables](template-variables.md)**: All available personalization variables
