# Conversation Simulator

Test your outreach sequences in a safe environment before going live. The Conversation Simulator lets you run realistic multi-turn conversations with AI-powered lead personas, debug every aspect of AI decision-making, and score your messaging quality — all without sending anything to real people.

For strategies on comparing prompt variants side-by-side, see [A/B Testing](ab-testing.md).

## Getting Started

Navigate to **Simulation** in the sidebar. The simulator opens with a three-step setup wizard.

### Step 1: Select Sequence

Choose which sequence to simulate. Active, paused, and draft sequences are all available. The simulator loads the sequence's DM template, AI prompt, and all configuration.

### Step 2: Select Lead

Two options for choosing who to simulate with:

**All Leads tab** — Search your existing leads by name, username, company, or email. Filter by buyer state (Ready, Emerging, Low Priority, Not Scored). The simulator loads their full profile, enrichment data, and recent activity.

**Custom Lead tab** — Create a synthetic lead on the fly. Only a name is required. Optionally add company, role, and bio. Useful for testing edge cases or specific personas without needing a real lead in your pipeline.

> **Tip:** Simulate with 3-5 diverse leads across different roles, industries, and company sizes. Include at least one lead with minimal data to ensure messages still read well when enrichment is sparse.

### Step 3: Choose Mode

Three simulation modes are available:

| Mode | Description |
|---|---|
| **Manual** | You play the lead — type responses and see how AI replies in real time |
| **Automatic** | AI plays both sides — watch a full conversation unfold with configurable lead personas |
| **Batch** | Run multiple automatic simulations at once with different persona combinations |

**Persona presets** — In Automatic and Batch modes, select from built-in lead personalities:

| Persona | Behavior |
|---|---|
| Hard to Convince | Skeptical, needs proof and social validation |
| Easy Enthusiastic | Excited, moves fast, asks about next steps |
| Asks Lots of Questions | Curious, wants every detail before committing |
| Not a Fit | Misunderstands the offer or is looking for something else |
| Price Sensitive | Budget-conscious, pushes back on cost |
| Uses Competitor | Already has a competing solution |
| Skeptical | Suspects spam or automation, trust issues |
| Terse Responder | Replies in 1-5 words |

You can also write a **custom persona** description for specific scenarios (e.g., "A VP of Engineering at a 500-person company who just switched from a competitor last month").

**A/B Compare** — Available in Automatic mode. Toggle this on to test two different AI prompts against the same lead and persona, running both conversations side by side.

## Manual Mode

In Manual mode, the AI sends the opening DM based on your sequence template. You then type responses as the lead and watch how the AI handles each reply.

Use this to stress-test specific scenarios:

- **Positive reply** — "This looks great!" — does AI offer clear next steps?
- **Objection** — "Too expensive." — does AI handle it gracefully?
- **Question** — "How is this different from X?" — does AI provide a credible answer?
- **Skepticism** — "Is this automated?" — does AI respond naturally?

## Automatic Mode

In Automatic mode, the AI plays both sides of the conversation. The selected persona determines how the simulated lead behaves. You see the conversation unfold turn by turn with a live turn counter.

Controls during an automatic simulation:

- **Pause** — Temporarily stop the conversation
- **Stop** — End the simulation early

After the conversation ends, you can continue it:

- **Lead replies** — Add another lead message to extend the conversation
- **AI sends follow-up** — See how the AI follows up after silence

The conversation ends naturally when one of these occurs:

| Exit Reason | Description |
|---|---|
| No Reply | The lead persona stops responding |
| End Conversation | The lead explicitly ends the chat |
| Graceful Exit | The AI reaches a natural conclusion |
| Max Turns | The conversation hit the turn limit |

## Batch Mode

Run 2-25 simulations at once, each with a different combination of persona presets. Batch mode shows all conversations in a live grid (2-4 columns) with real-time progress.

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
- **Weak spot analysis** — identifies which conversation stage has the highest drop-off rate, showing you exactly where your messaging loses leads

## Scorecard

Every completed simulation (automatic or batch) generates a scorecard that grades your AI's performance:

| Metric | Scale | What It Measures |
|---|---|---|
| Objection Handling | 1-10 | How well the AI addressed concerns and pushback |
| Tone Consistency | 1-10 | Whether the AI maintained a natural, consistent voice |
| Relevance | 1-10 | Whether responses addressed the lead's actual points |
| Naturalness | 1-10 | How real vs. scripted the conversation felt |

The scorecard also reports:
- **Goal completed** — whether the AI reached a soft close or meeting booking
- **Turns to close** — how many turns it took to reach the goal
- **Repetition detected** — whether the AI repeated itself
- **Stage progression** — which conversation stages were reached (Opener Reply → Discovery → Solution Discussion → etc.)

## Debug Panel

Click any message in a simulation to inspect the AI's decision-making. The debug panel has four tabs:

**Stage and Signals** — Shows the classified conversation stage, confidence level, detected buying signals, lead communication style, and response temperature.

**System Prompt** — Reveals the full prompt sent to the AI, broken into layers: base instructions, conversation context, lead data, knowledge base content, and tone guidance.

**RAG Context** — Shows which knowledge base chunks and tone examples were retrieved for this response.

**Lead Analysis** — Displays the lead's profile data, enrichment results, and any detected intent signals.

## Conversation Analysis

Click **Analyze** in the toolbar to run an AI-powered review of the entire conversation. The analyzer examines the exchange and generates actionable suggestions for improving your prompts, tone examples, and messaging strategy.

Suggestions can include modifications to your AI prompt, new tone examples to add, existing tone examples to adjust, and other improvements. You can preview exactly what each suggestion would change before applying it.

## Toolbar

The simulation toolbar provides quick access to:

- **New** — Start a fresh simulation
- **Restart** — Re-run the current simulation from scratch
- **Analyze** — Run conversation analysis
- **Debug** — Toggle the debug panel
- **Settings** — Edit the DM template and AI prompt (changes are for testing only)
- **Lead Profile** — View the lead's full profile
- **A/B** — Toggle A/B prompt comparison (Automatic mode)

## Capturing Tone Examples

When the AI produces a particularly good response during simulation, you can save it as a tone example. Click the bookmark icon on any AI message to capture that exchange as a reusable reference for future conversations. See [Tone Examples](../conversations/tone-examples.md) for more.

## Common Issues

**AI responses feel generic:** Add more context to your knowledge base. Upload documents about your product, case studies, and competitive positioning. Add tone examples that demonstrate your preferred voice.

**Simulation does not feel representative:** Use real leads from your pipeline rather than synthetic ones. Try different persona presets to cover a range of buyer behaviors. Run a batch of 10+ simulations to see patterns.

**Template variables showing as blank:** Check that the lead has the relevant data in their profile. Try a different lead with more complete enrichment. See [Template Variables](template-variables.md) for the full list of available variables.

## Next Steps

- **[A/B Testing](ab-testing.md)**: Compare prompt variants side by side
- **[Building Sequences](building-sequences.md)**: Apply what you learned to real campaigns
- **[Template Variables](template-variables.md)**: All available personalization variables
- **[Cold DM Generation](cold-dm-generation.md)**: How AI generates personalized first messages
- **[Tone Examples](../conversations/tone-examples.md)**: Train the AI's voice with real conversation samples
