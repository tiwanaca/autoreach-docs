# Knowledge Base

The Knowledge Base stores your sales documents so the AI can reference them when generating responses. Upload playbooks, case studies, FAQs, and objection handling docs to make the AI smarter and more context-aware.

## How It Works

Documents are processed through a RAG (Retrieval-Augmented Generation) pipeline:

1. **Upload**: Documents are uploaded per-offer
2. **Chunking**: Text is split into chunks for optimal retrieval
3. **Embedding**: Each chunk is converted to a vector embedding
4. **Storage**: Embeddings are stored for semantic search

## When Knowledge Base Is Used

When the AI generates a response, it searches your knowledge base for the most relevant chunks and injects them into the prompt.

**Token budget**: Knowledge base context is capped at **600 tokens** per response. Combined with tone examples (500 tokens), the total RAG budget is **1,100 tokens**.

Knowledge base is scoped per-offer — different offers can have different knowledge bases, so AI responses are tailored to each target audience.

### Key Moments

- **Cold DM generation**: References your value proposition, metrics, and case studies
- **Response generation**: Finds relevant objection handling scripts, product details, or case studies based on the conversation topic
- **Offer-specific context**: Ensures Enterprise case studies don't appear in SMB conversations

## Uploading Documents

### Supported File Formats

- **PDF**: Sales decks, case studies, whitepapers, one-pagers
- **DOCX**: Playbooks, sales guides, process documents
- **TXT**: FAQs, objection handling scripts, notes, quick-reference sheets

### Document Limit

You can upload up to **10 documents per offer**. If you need to add more, remove an older or less relevant document first. Quality matters more than quantity -- a few well-written documents outperform a large collection of vague or overlapping content.

### How to Upload

1. Navigate to your Offer and open the **Knowledge Base** section
2. Click **Upload Documents**
3. Select one or more files from your computer (PDF, DOCX, or TXT)
4. Click **Upload** to begin processing

After uploading, AutoReach automatically splits your documents into sections, generates embeddings, and indexes them for semantic search. This process takes a few seconds per document. Once complete, your knowledge base is ready to use.

> **Tip:** You can upload multiple files at once. Each file is processed independently, so a failed upload for one document does not affect the others.

### What Makes a Good Knowledge Base Document

The AI retrieves the most relevant sections from your knowledge base when generating responses. Documents that are specific, detailed, and clearly organized produce the best results.

**Strong candidates for your knowledge base:**

- **Case studies** with concrete results: "We helped Company X reduce churn by 40% in 3 months" gives the AI a specific proof point to reference when a lead asks about ROI
- **Objection handling scripts**: Common pushbacks (e.g., "We already have a solution," "Not in the budget") with your proven responses
- **Pricing and packaging guides**: So the AI can speak accurately about what you offer and at what price
- **Product or service overviews**: Feature descriptions, use cases, and differentiators
- **Implementation and onboarding docs**: Timeline, process steps, and what the customer can expect
- **FAQ documents**: Answers to the questions your sales team hears most often

**Documents to avoid:**

- Generic marketing copy with no specifics
- Internal engineering or technical documentation not relevant to sales conversations
- Excessively long documents where key points are buried (break these into focused sections instead)

## How the AI Uses Your Knowledge Base

When the AI generates a response, it performs a **semantic search** across your knowledge base to find the most relevant sections. Rather than keyword matching, it understands the meaning of what the lead said and retrieves content that addresses their question or concern.

The retrieved content is injected into the AI's context within a **600-token budget**. This means the AI sees roughly a page of relevant knowledge base content per response. Combined with tone examples (which have their own 500-token budget), the total contextual input is capped at 1,100 tokens.

For example, if your knowledge base includes a case study about reducing churn by 40%, and a lead asks "What kind of results do your clients see?", the AI might reference that specific case study in its reply -- making the response grounded in real data rather than generic claims.

## Tips for Better AI Responses

1. **Be specific with numbers and outcomes**: "Reduced onboarding time from 6 weeks to 10 days" is far more useful to the AI than "We speed up onboarding"
2. **Use clear section headings**: The chunking process works best when your documents have logical sections with descriptive headers
3. **Write in the voice you want the AI to use**: If your knowledge base documents are formal, the AI will lean formal. If they are conversational, responses will reflect that
4. **Cover common objections explicitly**: Write out the objection and your ideal response. The AI will adapt this to each conversation
5. **Update after wins**: When you close a deal, add the story as a case study. Fresh, specific examples improve response quality over time
6. **Remove outdated content**: Old pricing, discontinued features, or stale case studies can cause the AI to reference information that is no longer accurate

## Best Practices

1. **Upload your sales playbook** — core value proposition, buyer personas, sales process steps
2. **Include objection handling** — common objections with your standard responses
3. **Add case studies** — 3-5 detailed case studies with before/after metrics
4. **Create a FAQ document** — pricing, implementation timeline, support details
5. **Keep it updated** — review quarterly, replace stale content, remove conflicting information

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How the AI uses knowledge base during generation
- **[Tone Examples](tone-examples.md)**: The other half of the RAG context
