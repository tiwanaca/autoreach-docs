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

- **Name:** What you are calling this offer
- **Description:** Detailed description of what you are selling and why
- **Website:** Your website URL (used by AI to auto-populate fields)

### Target Audience

- **Target audience:** Free-form ICP definition. You can include who to target, who to avoid, and any context that helps AutoReach understand your ideal buyer.
- **Locations:** Geographic focus with an option to filter by **lead location** or **company HQ location**
- **Target industries:** LinkedIn industries used to filter people searches
- **Target language:** The language for your outreach messages (e.g., English, Spanish, Italian)

### Market Positioning

- **Pain points:** Problems your offer solves (used for intent matching and message personalization)
- **Known competitors:** Companies or tools that compete with you (helps detect leads engaging with competitors)
- **Search signals:** Natural language phrases your buyers post on social media (e.g., "I need better customer data integration")
- **Signal likelihood:** How likely your target buyers post about this on social media (high/medium/low). This adjusts how heavily intent signals are weighted in scoring.

### Value

- **Deal value:** Expected contract size ($). Used to estimate pipeline value.

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
- People at competitor companies are automatically disqualified

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

### How It Works

When you upload documents, AutoReach processes and indexes them so the AI can retrieve the most relevant sections when generating responses. When a prospect replies to your outreach, AutoReach searches your knowledge base for context that matches the conversation and uses it to generate accurate, on-brand responses.

Even if you upload many pages of documentation, AutoReach intelligently retrieves only the most relevant content for each conversation.

{% hint style="warning" %}
**Quality Over Quantity:** Upload your best docs: case studies, pricing, qualification criteria, objection handling, and key talking points. A few high-quality documents will perform better than a large volume of generic content.
{% endhint %}

## Tone Examples

**Tone examples** are conversation samples that define your outreach voice. They are configured **per sequence** in the sequence's Advanced Settings, not at the offer level.

Tone examples show AutoReach how you talk to prospects. They cover different conversation stages like openings, value propositions, objection handling, social proof, and closing. AutoReach auto-generates tone examples when you create a sequence, and you can edit, remove, or add custom examples to fine-tune how AI responds.

{% hint style="info" %}
**Pro Tip:** Review and edit your tone examples in your sequence's Advanced Settings. If your samples sound corporate but you are naturally casual, your AI replies will not match your real voice.
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

### How to Use It

Access the Conversation Analyzer from your sequence. It reviews your recent conversations and returns actionable suggestions. You can accept or dismiss each suggestion.

{% hint style="info" %}
**Run Monthly:** The Conversation Analyzer works best with sufficient data. Run it monthly to see patterns emerge.
{% endhint %}

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

## Next Steps

- **[Creating Your First Offer](../getting-started/create-offer.md)**: Walk through the offer creation process step by step
- **[Knowledge Base](../conversations/knowledge-base.md)**: Learn more about uploading and managing knowledge base documents
