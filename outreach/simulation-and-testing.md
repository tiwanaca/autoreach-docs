# Simulation and A/B Testing

Test your outreach sequences in a safe environment before going live. The Conversation Simulator lets you run realistic multi-turn conversations with AI-powered lead personas, debug every aspect of AI decision-making, and score your messaging quality, all without sending anything to real people.

## Getting Started

Navigate to **Simulation** in the sidebar. The simulator opens with a three-step setup wizard.

### Step 1: Select Sequence

Choose which sequence to simulate. Active, paused, and draft sequences are all available. The simulator loads the sequence's DM template, AI prompt, and all configuration.

### Step 2: Select Lead

Two options for choosing who to simulate with:

**All Leads tab** - Search your existing leads by name, username, company, or email. Filter by buyer state (Ready, Emerging, Low Priority, Not Scored). The simulator loads their full profile, enrichment data, and recent activity.

**Custom Lead tab** - Create a synthetic lead on the fly. Only a name is required. Optionally add company, role, and bio. Useful for testing edge cases or specific personas without needing a real lead in your pipeline.

> **Tip:** Simulate with 3-5 diverse leads across different roles, industries, and company sizes. Include at least one lead with minimal data to ensure messages still read well when enrichment is sparse.

### Step 3: Choose Mode

Three simulation modes are available:

| Mode | Description |
|---|---|
| **Manual** | You play the lead - type responses and see how AI replies in real time |
| **Automatic** | AI plays both sides - watch a full conversation unfold with configurable lead personas |
| **Batch** | Run multiple automatic simulations at once with different persona combinations |

**Persona presets** - In Automatic and Batch modes, select from built-in lead personalities:

| Persona | Behavior |
|---|---|
| Hard to convince | Skeptical, needs proof, pushes back |
| Easy & enthusiastic | Genuinely interested, moves fast |
| Asks lots of questions | Curious, wants to understand everything |
| Not a fit | Misunderstood the DM, looking for work |
| Price sensitive | Budget-conscious, needs ROI justification |
| Uses a competitor | Already has a solution, wants differentiation |
| Skeptical | Suspects spam or bot, cautious |
| Terse responder | Replies in 1-5 words |

You can also write a **custom persona** description for specific scenarios (e.g., "A VP of Engineering at a 500-person company who just switched from a competitor last month").

## Manual Mode

In Manual mode, the AI sends the opening DM based on your sequence template. You then type responses as the lead and watch how the AI handles each reply.

Use this to stress-test specific scenarios:

- **Positive reply** - "This looks great!" - does AI offer clear next steps?
- **Objection** - "Too expensive." - does AI handle it gracefully?
- **Question** - "How is this different from X?" - does AI provide a credible answer?
- **Skepticism** - "Is this automated?" - does AI respond naturally?

## Automatic Mode

In Automatic mode, the AI plays both sides of the conversation. The selected persona determines how the simulated lead behaves. You see the conversation unfold turn by turn with a live turn counter.

Controls during an automatic simulation:

- **Stop** - End the simulation early

After the conversation ends, you can continue it:

- **Lead replies** - Add another lead message to extend the conversation
- **AI sends follow-up** - See how the AI follows up after silence

The conversation ends naturally when one of these occurs:

| Exit Reason | Description |
|---|---|
| No Reply | The lead persona stops responding |
| End Conversation | The lead explicitly ends the chat |
| Exit | The AI reaches a natural conclusion |
| Max Turns | The conversation hit the turn limit |
| Error | Something went wrong during generation |

## Batch Mode

Run 2-25 simulations at once, each with a different combination of persona presets. Batch mode shows all conversations in a live grid with real-time progress.

Each run shows:
- Persona labels
- Live conversation turns
- Exit reason
- Turn count
- Scorecard scores

After all runs complete, you get a **batch summary** with:
- Average scores across all runs
- Goal completion rate
- Breakdown by exit reason
- **Weak spot analysis** - identifies which conversation stage has the highest drop-off rate, showing you exactly where your messaging loses leads

## Scorecard

Every completed simulation (automatic or batch) generates a scorecard that grades your AI's performance:

| Metric | Scale | What It Measures |
|---|---|---|
| Objection Handling | 1-10 | How well the AI addressed concerns and pushback |
| Tone Consistency | 1-10 | Whether the AI maintained a natural, consistent voice |
| Relevance | 1-10 | Whether responses addressed the lead's actual points |
| Naturalness | 1-10 | How real vs. scripted the conversation felt |

The scorecard also reports:
- **Goal completed** - whether the AI reached a soft close or meeting booking
- **Turns to close** - how many turns it took to reach the goal
- **Repetition detected** - whether the AI repeated itself
- **Stage progression** - which conversation stages were reached

## Debug Panel

Click any message in a simulation to inspect the AI's decision-making. The debug panel has four tabs:

**Stage and Signals** - Shows the classified conversation stage, confidence level, stage reasoning, detected buying signals, and objection subtype.

**System Prompt** - Reveals the full prompt sent to the AI, broken into layers: base instructions, conversation context, lead data, knowledge base content, and tone guidance.

**RAG Context** - Shows which knowledge base sections and tone examples were retrieved for this response.

**Lead Analysis** - Displays the lead's profile data, communication style, response temperature, and detected intent signals.

---

## A/B Testing

The simulator includes a built-in **A/B Compare** mode that runs the same scenario with two different AI prompts side by side. This lets you see exactly how prompt changes affect conversation quality before applying them to live sequences.

### How A/B Compare Works

1. Open the simulator and select a sequence, lead, and **Manual** or **Automatic** mode
2. Toggle **A/B Compare** on in the toolbar
3. The simulator creates two conversation slots: **Prompt A** (your current AI prompt) and **Prompt B** (an editable copy)
4. Edit Prompt B with your changes
5. Both conversations run simultaneously against the same lead and persona
6. Each slot gets its own scorecard so you can compare results directly

Both conversations use the same lead data, the same persona presets, and the same DM template. Only the AI prompt differs. This isolates the impact of your prompt changes.

### What to Test

**Tone shifts** - Compare professional vs. casual prompts and check which produces better scorecard results.

**Objection handling** - Test different approaches to pushback (e.g., case studies vs. ROI reframing). Use the "Price Sensitive" or "Hard to Convince" persona to trigger objections.

**Conversation strategy** - Compare discovery-first approaches ("Ask questions before pitching") vs. value-led approaches ("Lead with an insight and suggest a call").

**Length and detail** - Test a detailed prompt with stage-specific instructions vs. a minimal prompt that gives the AI more freedom.

### Tips for Effective A/B Testing

1. **Change one thing at a time.** If you change tone, strategy, and length all at once, you cannot tell which change made the difference.
2. **Run multiple comparisons.** Test with at least 3-5 different leads and personas.
3. **Use challenging personas.** Easy leads do not differentiate prompts well. Use "Hard to Convince", "Skeptical", or "Uses Competitor" to stress-test.
4. **Check the debug panel.** Click individual messages to see how the AI interpreted the stage, what knowledge base content it pulled, and what signals it detected.
5. **Follow up with batch mode.** Once you have a winning prompt, run a batch of 10-25 simulations across all personas to validate it at scale.
6. **Apply and iterate.** When you find a better prompt, update your sequence settings and test again.

---

## Conversation Analysis

Click **Analyze** in the toolbar to run an AI-powered review of the entire conversation. The analyzer examines the exchange and generates actionable suggestions for improving your prompts, tone examples, and messaging strategy.

Suggestions can include modifications to your AI prompt, new tone examples to add, existing tone examples to adjust, and other improvements. You can preview exactly what each suggestion would change before applying it.

## Capturing Tone Examples

When the AI produces a particularly good response during simulation, you can save it as a tone example. Click the bookmark icon on any AI message to capture that exchange as a reusable reference for future conversations.

## Toolbar

The simulation toolbar provides quick access to:

- **New** - Start a fresh simulation
- **Restart** - Re-run the current simulation from scratch
- **Analyze** - Run conversation analysis
- **Debug** - Toggle the debug panel
- **Settings** - Edit the DM template and AI prompt (changes are for testing only)
- **Lead Profile** - View the lead's full profile
- **A/B** - Toggle A/B prompt comparison

## Common Issues

**AI responses feel generic:** Add more context to your knowledge base. Upload documents about your product, case studies, and competitive positioning. Add tone examples that demonstrate your preferred voice.

**Simulation does not feel representative:** Use real leads from your pipeline rather than synthetic ones. Try different persona presets to cover a range of buyer behaviors. Run a batch of 10+ simulations to see patterns.

**Template variables showing as blank:** Check that the lead has the relevant data in their profile. Try a different lead with more complete enrichment. See [DM Personalization](dm-personalization.md) for the full list of available variables.

## Next Steps

- **[DM Personalization and Template Variables](dm-personalization.md)**: All available personalization variables
- **[Building Sequences](building-sequences.md)**: Apply what you learned to real campaigns
- **[Tone and Knowledge Base](../conversations/tone-and-knowledge.md)**: Train the AI's voice with real conversation samples
