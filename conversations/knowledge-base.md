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

Supported file types:
- **PDF**: Sales decks, case studies, whitepapers
- **DOCX**: Playbooks, sales guides
- **TXT**: FAQs, objection handling scripts, notes

Documents are automatically processed and indexed after upload.

## Best Practices

1. **Upload your sales playbook** — core value proposition, buyer personas, sales process steps
2. **Include objection handling** — common objections with your standard responses
3. **Add case studies** — 3–5 detailed case studies with before/after metrics
4. **Create a FAQ document** — pricing, implementation timeline, support details
5. **Keep it updated** — review quarterly, replace stale content, remove conflicting information

## Next Steps

- **[AI Response Engine](ai-response-engine.md)**: How the AI uses knowledge base during generation
- **[Tone Examples](tone-examples.md)**: The other half of the RAG context
