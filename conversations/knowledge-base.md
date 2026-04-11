# Knowledge Base & RAG

The Knowledge Base is AutoReach's memory system. Upload your sales playbooks, case studies, FAQs, and objection handling docs, and the AI will reference them when generating responses—making your AI assistant smarter with every document you add.

## What Is RAG?

**RAG** stands for **Retrieval-Augmented Generation**. It means:

1. **Retrieve**: When the AI needs to generate a response, it searches your Knowledge Base for relevant documents
2. **Augment**: The relevant info is pulled into the AI's context
3. **Generate**: The AI writes the response, informed by your docs

This approach is far better than "fine-tuning" the AI on your data. The AI stays current with your docs and can reference up-to-date case studies, pricing, and processes without needing retraining.

## Uploading Documents

You can upload:

- **PDF files** — Sales decks, case studies, whitepapers
- **DOCX files** — Word documents, playbooks, sales guides
- **TXT files** — FAQs, objection handling scripts, notes

Simply drag and drop or click **Upload Documents** in your Knowledge Base section.

{% hint style="info" %}
**File Size Limits**: Most documents up to 10 MB are supported. If you hit a limit, split large documents into separate uploads.
{% endhint %}

## How Documents Are Processed

When you upload a document, AutoReach:

1. **Chunks the document** into semantic segments (paragraphs, sections, etc.)
2. **Generates embeddings** for each chunk using OpenAI's `text-embedding-3-small` model
3. **Stores embeddings** in **pgvector** (a vector database)
4. **Indexes by relevance** so the AI can quickly find matching content

This entire process happens automatically in the background. You don't need to do anything—just upload and the Knowledge Base is ready to use.

## How Knowledge Base Is Retrieved

When generating a response, the AI:

1. **Extracts key topics** from the current conversation
2. **Searches your Knowledge Base** for relevant documents using **cosine similarity**
3. **Sets a similarity threshold** of **0.25** (on a scale of 0 to 1)
4. **Pulls the top matching chunks** into the context window
5. **Uses them to inform the response**

All this happens in milliseconds while the AI is writing the response.

{% hint style="tip" %}
**Why 0.25 Threshold?**: A threshold of 0.25 is lenient (it brings in more potentially relevant docs). This helps the AI find context even when the conversation topic doesn't exactly match your document titles. Too high a threshold would miss useful information.
{% endhint %}

## Token Budgets

The AI has separate token limits for different retrieval sources to balance context and efficiency:

- **Knowledge Base max**: 600 tokens
- **Tone Examples max**: 500 tokens
- **Total RAG budget**: 1,100 tokens

This means the AI can include significant context from your docs and tone examples while staying within token limits.

{% hint style="info" %}
**What Are Tokens?**: Roughly, 1 token ≈ 4 characters. A 600-token knowledge base can include ~2,400 characters (about 1–2 pages of text).
{% endhint %}

## When Knowledge Base Is Used

The Knowledge Base powers AI responses in three key moments:

### 1. Cold DM Generation
When the AI generates your initial outreach message, it references your Knowledge Base to:

- Match your company's value proposition
- Reference relevant metrics and case studies
- Include credible social proof

### 2. Response Generation
When a prospect replies, the AI searches your Knowledge Base for:

- Relevant case studies (if the prospect's industry matches)
- Objection handling scripts (if they raise a common concern)
- Product details (if they ask about your solution)

### 3. Offer-Specific Context
Your Knowledge Base can be attached to a specific **Offer** (ICP), so:

- Different offers can have different knowledge bases
- AI responses are tailored to each target audience
- Case studies for Enterprise clients don't confuse SMB responses

## Best Practices for Your Knowledge Base

### 1. Upload Your Sales Playbook
Include:

- Your core value proposition
- Typical buyer personas
- Sales process steps
- Key questions to ask in each stage

**Why**: The AI will align responses with your documented process.

---

### 2. Include Objection Handling
Upload a document with:

- Common objections you hear (budget, timing, fit, etc.)
- Your standard responses to each
- Counter-arguments with data

**Why**: When the AI enters the Objections stage, it'll have a playbook to reference.

---

### 3. Add Case Studies
Include:

- 3–5 detailed case studies from similar prospects
- Before/after metrics (time saved, revenue impact, etc.)
- Company size, industry, specific challenge

**Why**: The AI can reference relevant proof points when a prospect asks "Does this work for companies like mine?"

---

### 4. Create a FAQ Document
Include:

- Pricing (if relevant)
- Common technical questions
- Implementation timeline
- Support and onboarding details

**Why**: The AI can answer prospect questions without you needing to jump in.

---

### 5. Keep It Updated
- Review your Knowledge Base quarterly
- Replace outdated case studies with fresh ones
- Update pricing, timelines, or process changes
- Remove conflicting information

**Why**: Stale docs will lead to stale or conflicting AI responses.

---

## Token Budget Strategy

Your 1,100 token RAG budget is split across Knowledge Base (600) and Tone Examples (500). If you're running out of tokens:

- **Prioritize brevity**: Keep case studies to 100–150 words each
- **Use summaries**: Instead of uploading full whitepapers, create summary docs
- **Segment by offer**: If you have multiple offers, use separate Knowledge Bases for each

If you consistently exceed your budget, consider uploading only your highest-impact docs.

{% hint style="warning" %}
**Over the Token Limit?**: The AI will pull the most relevant chunks first, so if you exceed limits, less relevant content gets truncated. Quality over quantity.
{% endhint %}

## Example: A Well-Structured Knowledge Base

```
📁 Knowledge Base
├── Playbook.docx (Your sales process, buyer personas, value prop)
├── Case Studies.pdf (3–5 recent case studies with metrics)
├── Objection Handling.docx (Common objections + responses)
├── FAQ.txt (Pricing, implementation, support FAQs)
└── Product Overview.pdf (Feature overview, use cases)
```

This structure gives the AI a complete picture of your business without overloading any single category.

## Monitoring Knowledge Base Usage

Check your sequence activity to see:

- How often the AI is referencing your Knowledge Base
- Which documents are being retrieved most often
- Whether responses are citing your docs appropriately

If a document is never retrieved, it might be:

- Not relevant to your target audience
- Poorly worded (cosine similarity can't find it)
- Redundant with other docs

Consider removing or rewriting it.

---

## Next Steps

- Learn how the AI uses Knowledge Base in [AI Response Engine](ai-response-engine.md)
- Understand conversation stages that benefit most from Knowledge Base in [Conversation Stages](conversation-stages.md)
- Review knowledge retrieval in [Tone Examples & Customization](tone-examples.md)
