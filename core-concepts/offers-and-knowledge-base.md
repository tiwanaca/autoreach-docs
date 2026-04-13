# Offers & Knowledge Base

An **offer** is the foundation of everything in AutoReach. It is not just a description of your product: it is the intelligence engine that powers lead discovery, scoring, personalization, and AI responses.

## What Is an Offer?

One offer = one specific product or service you're selling.

**Examples:**

- "Workflow automation for mid-market SaaS companies"
- "Executive coaching for first-time VPs"
- "API compliance auditing for financial services firms"

You can create and manage multiple offers, each with its own lead pipeline, sequences, and knowledge base.

## Offer Fields

When you create an offer, you define:

### Core Definition

- **Name:** What you are calling this offer (required)
- **Description:** Detailed description of what you are selling and why (required)
- **Website:** Your website URL. You can use the "Extract from Website" feature to auto-populate offer fields from your site — this is a separate step, not automatic on save.

### Target Audience

- **Target audience:** Free-form ICP definition. You can include who to target, who to avoid, and any context that helps AutoReach understand your ideal buyer.
- **Locations:** Geographic focus (pipe-separated), with a **location filter type** setting that controls whether leads are matched by their own location or their company's HQ location
- **Industries:** LinkedIn industry IDs used to filter people searches
- **Language:** The language for your outreach messages (ISO 639-1 code, e.g., "en", "es", "it")
- **Qualification criteria:** Custom qualification rules stored as structured data

### Market Positioning

- **Pain points:** Problems your offer solves (used for intent matching and message personalization)
- **Known competitors:** Companies or tools that compete with you (helps detect leads engaging with competitors — these leads are scored as Poor Fit with zeroed scores, not Disqualified)
- **Search signals:** Natural language phrases your buyers post on social media (e.g., "I need better customer data integration")
- **Signal types:** Categories of signals to look for during discovery
- **Signal likelihood:** How likely your target buyers post about this on social media (high/medium/low). This adjusts how heavily intent signals are weighted in scoring.

### Value

- **Average value:** Expected contract size ($). Used to estimate pipeline value.

## How Offers Power Everything

Your offer definition cascades through AutoReach's entire system:

### 1. Lead Discovery

AutoReach uses your offer's **search signals** to find relevant leads:

```
"Looking for project management software"
↓
Searches X and LinkedIn for these keywords
↓
Finds people posting about project management needs
↓
Adds them as leads
```

More specific search signals = more targeted discovery.

### 2. Lead Scoring

Your offer's **target audience** and **pain points** guide the buyer intelligence system:

- People matching your target industry get higher fit scores
- People posting about your pain points get higher intent scores
- People in your preferred locations get a fit boost
- People at competitor companies are marked as Poor Fit with zeroed scores

### 3. DM Personalization

When sequences send DMs, AutoReach uses your offer's **description** and **pain points** to personalize messages:

```
"Hi [name], I noticed you're in [industry] and posted about [pain_point].
We help teams like yours solve [pain_point] with [benefit]. Worth a quick call?"
```

### 4. AI Responses

When leads reply, AutoReach's conversation AI uses your offer to:

- Understand context of the discussion
- Generate on-brand replies
- Know when to escalate to a human
- Suggest next steps

### 5. Signal Likelihood Weighting

Your **signal likelihood** setting adjusts how the three scoring dimensions (fit, intent, timing) are weighted:

- **High likelihood:** Your buyers frequently post about their needs on social media. Intent signals carry more weight.
- **Medium likelihood** (default): Your buyers sometimes post about their needs. Balanced weighting.
- **Low likelihood:** Your buyers rarely post about their needs. Fit becomes the dominant factor.

> **Tip:** Spend time defining your offer well. A great offer definition is a force multiplier that makes every downstream feature smarter.

## The Knowledge Base System

The **Knowledge Base** lets you upload your strategic docs, case studies, pricing, qualification criteria, and more. AutoReach uses these documents to:

- Make AI responses more accurate and on-brand
- Understand your business deeper than just the offer description
- Qualify leads better with custom criteria
- Generate better personalization in DMs

### Supported File Types

- PDF
- DOCX (Word)
- TXT

Limit: 10 documents per offer, 10MB per file.

### How It Works

When you upload a document, AutoReach processes it through a full RAG (Retrieval-Augmented Generation) pipeline:

1. The file is stored in cloud storage
2. A background worker parses the document, splits it into 512-token chunks (with 50-token overlap), and generates vector embeddings for each chunk
3. Embeddings are stored for similarity search

When a prospect replies to your outreach, AutoReach performs a vector similarity search against your knowledge base chunks to find the most relevant content (up to 600 tokens of context), then feeds it to the AI alongside the conversation to generate accurate, on-brand responses.

> **Warning:** Upload your best docs: case studies, pricing, qualification criteria, objection handling, and key talking points. A few high-quality documents will perform better than a large volume of generic content.

## Tone Examples

**Tone examples** are conversation samples that define your outreach voice. They are configured **per sequence**, not at the offer level.

Tone examples show AutoReach how you talk to prospects. They cover different conversation stages like openings, value propositions, objection handling, social proof, and closing. You add tone examples manually to your sequence, and can edit or remove them at any time. Once added, AutoReach auto-generates a tone summary in the background that the AI uses alongside the examples. During conversations, up to 500 tokens of relevant tone example content is retrieved via vector similarity search to keep AI responses on-voice.

> **Tip:** Review and edit your tone examples in your sequence's Advanced Settings. If your samples sound corporate but you are naturally casual, your AI replies will not match your real voice.

## Conversation Analyzer

The **Conversation Analyzer** is an AI system that reviews your outreach conversations and suggests improvements.

### What It Does

1. **Samples conversations** from your sequence — comparing positive outcomes (meeting booked) against negative ones (lost, graceful exit)
2. **Identifies patterns** in what worked vs. what didn't
3. **Suggests specific actions**:
   - **Add tone example** — new conversation samples to guide AI voice
   - **Modify tone example** — adjust existing examples based on what worked
   - **Remove tone example** — drop examples that are hurting performance
   - **Modify prompt** — changes to AI prompts (DM generation, warmup, or response prompts)

The analyzer focuses on tone examples and prompts, not offer-level fields like pain points or personalization settings.

### How to Use It

Access the Conversation Analyzer from your sequence page. It reviews your conversations and returns actionable suggestions. You can apply or dismiss each suggestion — applying writes the changes directly to your sequence's tone examples or prompts.

> **Tip:** The Conversation Analyzer works best with sufficient data. Run it monthly to see patterns emerge.

## Managing Multiple Offers

You can create multiple offers in AutoReach. Each offer:

- Has its own lead pipeline
- Can run independent sequences
- Has a separate knowledge base
- Has isolated scoring logic

**Common setup:**

- Offer 1: "Core product for mid-market"
- Offer 2: "Enterprise premium service"
- Offer 3: "International expansion service"

Each has different ICPs, signals, and messaging.

> **Warning:** If a lead fits both Offer 1 and Offer 2, they'll appear in both pipelines. This is intentional, as different offers might have different sales approaches to the same person.

## Best Practices

> **Tip:** A narrow, well-defined offer (yoga for busy parents aged 30-45) scores better than broad offers (fitness for everyone). Specific signals lead to specific discovery, which produces higher-quality leads.

> **Tip:** As you close deals, update your offer's "average deal value". As you learn what types of companies buy, refine your target audience.

> **Tip:** You can run AutoReach without a knowledge base, but uploading your best docs will make AI responses more sophisticated and on-brand.

> **Warning:** Uploading 200-page documents doesn't help. Upload 5-10 high-quality docs instead. Longer isn't smarter; relevance is.

## Next Steps

- **[Creating Your First Offer](../getting-started/create-offer.md)**: Walk through the offer creation process step by step
- **[Knowledge Base](../conversations/knowledge-base.md)**: Learn more about uploading and managing knowledge base documents
