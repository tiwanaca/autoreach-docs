# Creating Your First Offer

An **Offer** is the foundation of AutoReach. It describes your product or service, your target audience, and your outreach goals. AutoReach uses your Offer to power AI personalization, lead scoring, and DM generation.

## What Is an Offer?

Think of an Offer as your "outreach profile." It contains:

- **What you sell**: Your product or service description
- **Who you're targeting**: Your ideal customer profile (ICP)
- **What you want to achieve**: Book calls, start conversations, provide value, soft pitch
- **Context about your business**: Pain points you solve, competitors, locations, industry focus

AutoReach's AI uses this information to:

1. **Find the right leads**: Score prospects based on how well they match your ICP
2. **Personalize messages**: Generate DMs that reference the prospect's situation and your Offer
3. **Guide conversations**: Provide context to AI auto-replies so they stay on-brand
4. **Optimize outreach**: Learn what works and suggest refinements

## Creating Your Offer

Go to **Offers** → **Create Offer**. The easiest way is to **add your website URL** — AutoReach will automatically extract your business details and pre-populate the offer fields. Review and modify what's needed, then save. You can also fill in all the details manually.

### Required Fields

#### Name

The name of your offer or product. Keep it short and clear.

**Examples**:
- "SaaS Security Audits"
- "Fractional CFO Services"
- "AI Content Writing Tool"
- "B2B Market Research"

#### Description

What you do, in 10–300 characters. Be specific about the transformation or value you provide.

**Good descriptions**:
- "We help mid-market tech companies reduce security risk through automated vulnerability scanning."
- "On-demand CFO services for early-stage startups. Financial planning, fundraising strategy, investor relations."
- "AI writing assistant that generates blog posts, emails, and product copy 10x faster than manual writing."

**Avoid**:
- Generic descriptions ("We're a software company")
- Marketing fluff ("Industry-leading solution")
- Jargon without context ("SaaS optimization platform")

#### Target Audience

Who you're trying to reach, in 10–400 characters. Describe the role, company size, industry, or pain point.

**Good target audiences**:
- "CTOs and security leads at Series B–D tech companies (50–1000 employees)"
- "Startup founders and early-stage employees managing financial operations"
- "Marketing directors at B2B SaaS companies looking to scale content production"
- "VP of Sales at enterprise software companies dealing with sales cycle delays"

#### Goal

What you want to achieve with outreach. Choose one:

- **`start_conversation`** — Your main goal is to get a response and open dialogue
- **`provide_value`** — You want to share useful insights, resources, or introductions
- **`soft_pitch`** — Introduce your solution gently without hard selling
- **`book_call`** — Schedule a meeting or call directly

Your goal influences how AutoReach personalizes DMs. For example:
- `start_conversation` → Friendly, low-pressure opener ("Quick question about...")
- `book_call` → Direct and specific ("Let's chat on Tuesday at 2pm")

### Optional but Recommended Fields

#### Pain Points

A list of 3–5 pain points your Offer solves. Use short phrases (3–7 words each).

**Examples**:
- "Security vulnerabilities going undetected"
- "Spending 20+ hours on financial forecasting"
- "Writing blog posts manually is too slow"
- "Sales cycles are taking too long"

Pain points help AutoReach find prospects who mention these issues on social media and personalize messages accordingly.

#### Competitors

3–6 companies or products you compete with. This helps AutoReach understand your market position and identify target prospects.

**Examples**:
- Slack (if you're a communication tool)
- Stripe (if you're a payment processor)
- HubSpot (if you're a CRM)

#### Preferred Locations

Geographic regions where you want to focus outreach. Use pipe-separated format:

```
San Francisco, CA | New York, NY | London, UK | Berlin, Germany
```

AutoReach will prioritize leads from these locations. Leave blank for global targeting.

#### Industry Focus

LinkedIn industry IDs for your target market. This helps AutoReach find prospects in specific sectors (e.g., Technology, Financial Services, Healthcare).

## Knowledge Base

Upload your strategy docs, case studies, and other context. AutoReach's AI uses these documents to generate personalized, contextual responses.

### What to Upload

Upload 1–5 documents (PDF, DOCX, or TXT) with:

- **Case studies**: How you solved problems for past clients
- **Playbooks**: Your outreach strategy, sales process, or methodology
- **Price sheets**: Pricing information (optional, for discovery calls)
- **Product guides**: Overview of your product or service
- **Strategy docs**: How your offer solves specific problems

### How to Upload

1. In your Offer, go to **Knowledge Base**
2. Click **Upload Documents**
3. Select 1–5 files (PDF, DOCX, TXT)
4. Click **Upload**

AutoReach will:
- Chunk your documents into sections
- Embed them using AI embeddings
- Index them for semantic search

When someone replies to your outreach, AutoReach's AI will search your knowledge base for relevant context and use it to generate smart, personalized responses.

{% hint style="info" %}
**Tip**: The more detailed your knowledge base, the better AutoReach's AI performs. Include real examples of your work, your problem-solving approach, and customer success stories.
{% endhint %}

### How Knowledge Base Powers AI Responses

When a prospect replies, AutoReach:

1. **Searches your knowledge base** for relevant sections (e.g., if they ask about pricing, it finds your price sheet)
2. **Includes the context** in the AI prompt
3. **Generates a response** that's personalized and grounded in your actual strategy

**Example**:
- Prospect asks: "How do you handle data security?"
- AutoReach searches your knowledge base and finds your security playbook
- AI generates a response citing your specific approach
- Response is sent automatically or queued for your review

## Tone Examples

Tone examples are conversation samples that teach AutoReach how you speak. They define your outreach voice and help the AI maintain consistency.

### Why Tone Matters

AutoReach generates 21 examples automatically:
- 11 examples for **conversation-building** (friendly, curious, low-pressure)
- 10 examples for **closing** (direct, specific, call-to-action)

These examples help AutoReach's AI understand your style so it generates messages that sound like you.

### Reviewing Tone Examples

1. Go to your Offer → **Tone Examples**
2. Review the 21 auto-generated examples
3. Edit any that don't match your voice (click the example to edit)
4. Add custom examples if you want to emphasize a specific style
5. Click **Save**

### Customizing Tone

If the auto-generated examples don't feel right:

1. Edit individual examples to better match your voice
2. Add custom examples from your best past outreach
3. Label them clearly (e.g., "Funny, irreverent opener" or "Enterprise closing line")

The more examples you provide, the better AutoReach learns your voice.

{% hint style="info" %}
**Tip**: Use tone examples from your own past successful outreach. If you have 5–10 DMs that got great responses, add them as custom tone examples. AutoReach will learn from your winners.
{% endhint %}

## How Your Offer Powers AutoReach

### 1. Lead Scoring

When you add a lead to a sequence, AutoReach scores them based on:
- Profile data (role, company, location)
- Social signals (recent posts, engagement)
- Match to your Offer's target audience

High scores = more likely to convert.

### 2. Keyword Generation

AutoReach extracts keywords from your Offer and uses them to:
- Search for relevant prospects on Twitter/LinkedIn
- Filter leads in Autopilot
- Identify trending topics in your space

### 3. DM Personalization

When sending DMs, AutoReach:
- Looks up the prospect's profile and recent activity
- References relevant pain points from your Offer
- Crafts a personalized opener based on your tone examples

### 4. AI Response Context

When prospects reply, AutoReach:
- Searches your knowledge base for context
- Uses your tone examples to match your voice
- Generates smart replies without losing your brand

## Best Practices

### Make Your Offer Description Detailed

The more specific your description, the better AutoReach's AI personalizes outreach.

**Weak**: "We help businesses with automation."
**Strong**: "We automate repetitive B2B workflows using AI. Save your team 20+ hours/week on email, data entry, and report generation."

### Be Clear About Your Target Audience

Vague ICPs lead to unfocused outreach.

**Weak**: "Marketing professionals"
**Strong**: "VP of Demand Gen at B2B SaaS companies with $10M+ ARR, focused on ABM strategy"

### Include Specific Pain Points

Prospects resonate with solutions that name their exact problems.

**Weak**: "Help with revenue"
**Strong**: "Reduce time to close deals", "Improve sales team visibility", "Decrease win-loss variance"

### Upload Real Case Studies to Knowledge Base

Real examples make your AI responses more credible.

**Upload**:
- A 1-page case study showing a client's problem, your solution, and results
- A screenshot of customer success (e.g., 40% improvement in conversion rate)
- Testimonial highlighting the specific value you deliver

### Review and Update Your Offer Regularly

As your business evolves, update your Offer:
- Quarterly: Review target audience and adjust based on who's converting
- Quarterly: Add new case studies to your knowledge base
- Monthly: Refine tone examples based on your best outreach

## Example: Complete Offer Setup

**Name**: SaaS Security Audits

**Description**: Automated security assessments that identify vulnerabilities in your SaaS stack. Our framework checks 200+ integrations and compliance requirements in 2 hours.

**Target Audience**: CTOs and Security leads at Series B–D tech companies (50–500 employees), managing cloud security and compliance.

**Goal**: Book Call

**Pain Points**:
- Security gaps in third-party integrations
- Compliance audits taking weeks
- No visibility into vendor risk
- Incident response preparation

**Competitors**: Vanta, Secureframe, Drata

**Preferred Locations**: San Francisco | New York | Boston | Seattle

**Knowledge Base Documents**:
1. Case Study: How Acme Corp reduced compliance audit time from 8 weeks to 2 weeks
2. Security Framework: Our 5-step assessment methodology
3. Compliance Checklist: SOC 2, ISO 27001, HIPAA requirements we check

**Tone Examples**: (Auto-generated, reviewed for accuracy)
- Friendly examples: "Just reviewed your security setup — 2 quick questions..."
- Closing examples: "Let's run a 30-min security audit next Tuesday?"

Now you're ready to use this Offer to build sequences, find leads, and automate outreach!

## Next Steps

1. **Connect a Social Account**: [Connecting X](connect-twitter.md) or [Connecting LinkedIn](connect-linkedin.md)
2. **Build a Sequence**: Create your first automation workflow
3. **Add Leads**: Find prospects who match your Offer
4. **Launch and Monitor**: Start outreach and track results

See [Quickstart](quickstart.md) for the full setup flow.
