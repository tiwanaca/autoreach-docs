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

- **Name:** What you're calling this offer
- **Description:** Detailed description of what you're selling and why

### Target Audience

- **Target audience:** ICP definition (e.g., "CTOs at B2B SaaS companies with 50-500 employees")
- **Preferred locations:** Geographic focus (e.g., "North America, Western Europe")
- **Industry:** Target industries (financial services, healthcare, etc.)

### Market Positioning

- **Pain points:** 3-5 problems your offer solves
- **Competitors:** 3-6 competing products/companies
- **Search signals:** Natural language phrases your buyers post (e.g., "I need better customer data integration")
- **Signal likelihood:** How likely your target buyers post about this on social (high/medium/low)

### Value

- **Average deal value:** Expected contract size ($)

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

- People matching your target industry - Higher fit
- People posting about your pain points - Higher intent
- People in preferred locations - Fit adjustment
- People at competitor companies - Fit = 0

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

Your **signal likelihood** setting (high/medium/low) adjusts how heavily intent signals are weighted in scoring:

- **High likelihood** - "Workflow automation" is frequently discussed; weight intent 50%
- **Medium likelihood** - "Compliance auditing" sometimes discussed; weight intent 30%
- **Low likelihood** - "Specialized technical consulting" rarely discussed; weight intent 20%

{% hint style="info" %}
**Pro Tip:** Spend time defining your offer well. A great offer definition is a force multiplier that makes every downstream feature smarter.
{% endhint %}

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
- Markdown

### How It Works: RAG Pipeline

Your knowledge base documents flow through a Retrieval-Augmented Generation (RAG) pipeline:

```
1. Upload Document
   ↓
2. Chunking
   Your document is split into overlapping chunks (~500 tokens each)
   ↓
3. Embedding
   Each chunk is converted to a vector using OpenAI's text-embedding-3-small
   ↓
4. Storage
   Embeddings stored in pgvector database for fast retrieval
   ↓
5. Retrieval
   When AI needs context, it searches for relevant chunks
   ↓
6. Response Generation
   Most relevant chunks are passed to Claude for response generation
```

### Retrieval Limits

AutoReach has strict token budgets to keep AI responses fast:

| Context Type             | Token Budget  |
|--------------------------|---------------|
| Knowledge base documents | 600 tokens    |
| Tone examples            | 500 tokens    |
| **Total context**        | **1100 tokens** |

This means if you upload 50 pages of documentation, AutoReach will intelligently retrieve only the most relevant 600 tokens of that content when generating a reply.

{% hint style="warning" %}
**Quality Over Quantity:** Don't dump your entire playbook into the knowledge base. Upload your best docs: pricing, qualification criteria, case studies, objection handling, key talking points.
{% endhint %}

## Tone Examples

**Tone examples** are conversation samples that define your outreach voice. They show AutoReach how you talk to prospects:

```
Example 1:
Me: "Hey Sarah, how's your hiring going?"
Prospect: "Pretty good, we're scaling the team"
Me: "Cool! Any particular areas you're struggling to hire for?"
Prospect: "Yeah, finding good product managers is tough"
Me: "I can help with that. Mind if I send you 5 PMs I know? No strings."

Example 2:
Me: "I just saw you got funding. Congrats!"
Prospect: "Thanks, raising Series B for marketing automation"
Me: "That's huge. What are you prioritizing first?"
```

### Auto-Generated Tones

AutoReach generates **21 tone example templates** automatically when you create an offer. These cover different conversation stages:

- **Opening:** How you start conversations
- **Value prop:** How you pitch
- **Objection handling:** How you respond to "not interested"
- **Social proof:** How you use case studies
- **Closing:** How you ask for meetings
- ...and more

You can edit, remove, or add custom tone examples to fine-tune how AI responds.

### Tone Example Token Budget

Tone examples get 500 tokens of the 1,100-token total context budget. If you have 30 tone examples, AutoReach will intelligently retrieve the most relevant 2-3 examples for each situation.

{% hint style="info" %}
**Pro Tip:** Edit your auto-generated tone examples to match your actual voice. AI learns from examples. If your samples sound corporate but you're naturally casual, your AI replies won't match.
{% endhint %}

## Conversation Analyzer

The **Conversation Analyzer** is an AI system that reviews your outreach conversations and suggests improvements.

### What It Does

1. **Analyzes conversations** from your completed sequences
2. **Identifies patterns** in what worked (got replies) vs. what didn't (silence)
3. **Suggests improvements** for:
   - Tone and voice (be more casual, less sales-y, etc.)
   - Message templates (stronger opening hooks, clearer CTAs)
   - Pain point focus (emphasize a specific pain point more)
   - Personalization (use more/less personalization)

### Running an Analysis

Access via your offer dashboard:

```
1. Click "Analyze Conversations"
2. Analyzer reviews last 30 days of conversations
3. Returns 5-10 suggestions per category
4. You can accept or reject suggestions
5. Accepted changes update your tone examples and DM prompts
```

### Example Output

```
SUGGESTION 1: Increase casual tone
Impact: +12% reply rate in test conversations
Apply to: DM opening template
Confidence: High

SUGGESTION 2: Lead with social proof instead of pain point
Impact: +8% reply rate
Apply to: Objection handling tone examples
Confidence: Medium
```

{% hint style="info" %}
**Run Monthly:** Conversation Analyzer works best with sufficient data. Run monthly to see patterns emerge. With small sample sizes (< 20 conversations), suggestions are less reliable.
{% endhint %}

## Managing Multiple Offers

You can create multiple offers in AutoReach. Each offer:

- Has its own lead pipeline
- Can run independent sequences
- Has a separate knowledge base
- Gets its own tone examples
- Has isolated scoring logic

**Common setup:**

- Offer 1: "Core product for mid-market"
- Offer 2: "Enterprise premium service"
- Offer 3: "International expansion service"

Each has different ICPs, signals, and messaging.

{% hint style="warning" %}
**Leads Can Match Multiple Offers:** If a lead fits both Offer 1 and Offer 2, they'll appear in both pipelines. This is intentional, as different offers might have different sales approaches to the same person.
{% endhint %}

## Best Practices

{% hint style="info" %}
**Start Specific:** A narrow, well-defined offer (yoga for busy parents aged 30-45) scores better than broad offers (fitness for everyone). Specific signals lead to specific discovery, which produces higher-quality leads.
{% endhint %}

{% hint style="info" %}
**Update Based on Reality:** As you close deals, update your offer's "average deal value". As you learn what types of companies buy, refine your target audience.
{% endhint %}

{% hint style="info" %}
**Knowledge Base is Optional But Powerful:** You can run AutoReach without a knowledge base, but uploading your best docs will make AI responses more sophisticated and on-brand.
{% endhint %}

{% hint style="warning" %}
**Don't Overload the Knowledge Base:** Uploading 200-page documents doesn't help. Upload 5-10 high-quality docs instead. Longer isn't smarter; relevance is.
{% endhint %}
