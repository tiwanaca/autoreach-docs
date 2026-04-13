# Tone Examples

Tone examples are conversation samples that teach the AI how you want to sound. They are the most effective way to make AI responses feel authentic to your voice and sales style.

## How They Work

Tone examples are stored **per-sequence**. Each example contains:

- A **label** describing the scenario
- A **stage** classification (Opener Reply, Discovery, Objection Handling, etc.)
- A **conversation** with message pairs showing the exchange
- A **source type** indicating how it was created

The AI retrieves the most relevant tone examples at response time via **semantic search** using vector embeddings. The search query combines the lead's latest message with the last 3 conversation messages for context.

## Stage Classification

When examples are created, they are classified into stages using keyword heuristics — checking for patterns like pricing questions, scheduling language, and question marks. This is lightweight and doesn't require an AI call.

## Auto-Capture from Conversations

Tone examples are automatically captured from real conversation outcomes:

### Winning Conversations

When a conversation reaches **Meeting Booked** status:
- The system extracts 2–3 of the best exchanges (scored by average message length and presence of questions)
- Each exchange is classified by stage via heuristics
- Duplicate detection prevents storing very similar examples
- Saved as a "Captured Win" example
- The tone summary is regenerated periodically as new examples are captured

### Losing Conversations

When a conversation reaches "Lost" or "Graceful Exit" status:
- The last 4 messages are captured
- Saved as a "Captured Loss" example at the Graceful Exit stage
- Labeled as "Anti-example: Lost conversation"

## Tone Summary

A **tone summary** is a 150–250 word style guide extracted from your tone examples by AI. It analyzes vocabulary, brevity, value-led approach, curiosity gaps, and anti-patterns (e.g., overused phrases, non-contractions, filler openings).

The summary is regenerated periodically as new examples are captured to stay current with your evolving voice.

## Managing Tone Examples

Open your sequence's **Tone Examples** tab to:

- **View** examples organized by stage
- **Edit** text to better match your voice
- **Delete** examples that don't fit your style
- **Add** custom examples from conversations that went well

All examples use contractions (I'm, you're, they've) by default — non-contracted language sounds robotic in DMs.

## Next Steps

- **[Conversation Stages](conversation-stages.md)**: The 7 stages that tone examples align to
- **[AI Response Engine](ai-response-engine.md)**: How tone examples are used during generation
- **[Conversation Analyzer](conversation-analyzer.md)**: AI suggestions for improving your tone examples
