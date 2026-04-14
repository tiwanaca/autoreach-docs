# Conversation Analyzer

The Conversation Analyzer reviews your conversations, identifies patterns, and generates actionable suggestions to improve your AI's outreach voice.

## How It Works

When you run an analysis:

1. Fetches all replied conversations for the sequence
2. Classifies outcomes (positive, negative, neutral) based on conversation status
3. Analyzes patterns across your conversations using AI
4. Generates actionable suggestions for improvement

Analysis is triggered manually-  it is not automatic.

## Suggestion Types

The Analyzer generates four types of suggestions:

### Modify Tone Example

An existing tone example isn't matching your actual voice. The Analyzer identifies the misalignment and suggests specific edits.

### Add Tone Example

A conversation stage is missing examples or has too few. The Analyzer identifies a gap and suggests a new example based on your successful conversations.

### Remove Tone Example

A tone example contains anti-patterns or is consistently associated with stalled conversations. The Analyzer recommends removing it.

### Modify Prompt

Your AI prompt needs adjustment. Each prompt modification suggestion targets a specific prompt field:
- **AI Prompt**-  general conversation AI instructions
- **Warmup Prompt**-  warmup engagement prompt
- **DM Generation Prompt**-  cold DM generation prompt

## Applying Suggestions

For each suggestion, you can:

- **Apply**: Implement the change immediately
- **Dismiss**: Skip the suggestion
- **Edit**: Modify the suggestion before applying

## When to Run Analysis

Run the Conversation Analyzer after accumulating enough conversations for meaningful patterns-  typically after 20+ replied conversations. The more data available, the more reliable the suggestions.

## Next Steps

- **[Tone and Knowledge Base](tone-and-knowledge.md)**: Manage the tone examples that suggestions modify
- **[AI Response Engine](ai-response-engine.md)**: How tone and prompt changes affect responses
