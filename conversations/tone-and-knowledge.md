# Tone Examples and Knowledge Base

Tone examples and the knowledge base are the two tools you use to control how the AI communicates on your behalf. Tone examples teach the AI *how* to sound. The knowledge base teaches the AI *what* to say.

---

## Tone Examples

Tone examples are conversation samples that teach the AI how you want to sound. They are the most effective way to make AI responses feel authentic to your voice and sales style.

### How They Work

Tone examples are stored **per-sequence**. Each example contains:

- A **label** describing the scenario
- A **stage** classification (Opener Reply, Discovery, Objection Handling, etc.)
- A **conversation** with message pairs showing the exchange
- A **source type** indicating how it was created

When generating a response, the AI retrieves the most relevant tone examples based on the current conversation context. Examples cover all conversation stages including a dedicated "Not a Fit" category for gracefully handling leads that are not a match.

### Auto-Capture from Conversations

Tone examples are automatically captured from real conversation outcomes:

**Winning Conversations** - When a conversation reaches **Meeting Booked** status, the system extracts the best exchanges and saves them as examples, automatically classified by conversation stage. Duplicate examples are detected and skipped.

### Tone Summary

A **tone summary** is a style guide automatically extracted from your tone examples by AI. It captures your vocabulary, communication style, and common patterns. You can regenerate it from the tone examples section to keep it current with your evolving voice.

### Managing Tone Examples

Open your sequence's **Settings** tab and scroll to the Tone Examples section to:

- **View** examples organized by stage
- **Edit** text to better match your voice
- **Delete** examples that don't fit your style
- **Add** custom examples from conversations that went well

Use contractions (I'm, you're, they've) in your examples. Non-contracted language sounds robotic in DMs.

---

## Knowledge Base

The Knowledge Base stores your sales documents so the AI can reference them when generating responses. Upload playbooks, case studies, FAQs, and objection handling docs to make the AI smarter and more context-aware.

### How It Works

Documents are uploaded per-offer. After uploading, AutoReach automatically processes and indexes your documents so the AI can search them for relevant content when generating responses.

Knowledge base is scoped per-offer, so different offers can have different knowledge bases. This ensures AI responses are tailored to each target audience.

### When Knowledge Base Is Used

- **Cold DM generation**: References your value proposition, metrics, and case studies
- **Response generation**: Finds relevant objection handling scripts, product details, or case studies based on the conversation topic
- **Offer-specific context**: Ensures Enterprise case studies do not appear in SMB conversations

### Uploading Documents

**Supported file formats:**

- **PDF**: Sales decks, case studies, whitepapers, one-pagers
- **DOCX**: Playbooks, sales guides, process documents
- **TXT**: FAQs, objection handling scripts, notes, quick-reference sheets

You can upload up to **10 documents per offer**. Quality matters more than quantity. A few well-written documents outperform a large collection of vague or overlapping content.

**How to upload:**

1. Navigate to your Offer and open the **Knowledge Base** section
2. Click the upload area or drag a file onto it
3. Select a file from your computer (PDF, DOCX, or TXT)

Processing takes a few seconds per document. Once complete, your knowledge base is ready to use.

### What Makes a Good Knowledge Base Document

**Strong candidates:**

- **Case studies** with concrete results: "We helped Company X reduce churn by 40% in 3 months" gives the AI a specific proof point to reference
- **Objection handling scripts**: Common pushbacks with your proven responses
- **Pricing and packaging guides**: So the AI can speak accurately about what you offer
- **Product or service overviews**: Feature descriptions, use cases, and differentiators
- **Implementation and onboarding docs**: Timeline, process steps, and what the customer can expect
- **FAQ documents**: Answers to the questions your sales team hears most often

**Documents to avoid:**

- Generic marketing copy with no specifics
- Internal engineering or technical documentation not relevant to sales conversations
- Excessively long documents where key points are buried (break these into focused sections instead)

### Tips for Better AI Responses

1. **Be specific with numbers and outcomes**: "Reduced onboarding time from 6 weeks to 10 days" is far more useful to the AI than "We speed up onboarding"
2. **Use clear section headings**: Processing works best when your documents have logical sections with descriptive headers
3. **Write in the voice you want the AI to use**: If your knowledge base documents are formal, the AI will lean formal. If they are conversational, responses will reflect that
4. **Cover common objections explicitly**: Write out the objection and your ideal response. The AI will adapt this to each conversation
5. **Update after wins**: When you close a deal, add the story as a case study. Fresh, specific examples improve response quality over time
6. **Remove outdated content**: Old pricing, discontinued features, or stale case studies can cause the AI to reference information that is no longer accurate

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How the AI uses tone examples and knowledge base during generation
- **[Conversation Analyzer](conversation-analyzer.md)**: AI suggestions for improving your conversations
