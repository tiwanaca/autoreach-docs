# Buyer Intelligence & Scoring

AutoReach's **Buyer Intelligence** system is the heart of smart outreach. Instead of blasting everyone, it scores each lead across three dimensions (fit, intent, and timing) and uses that data to predict who is most likely to buy right now.

## The FIT-FIRST Model

Our proprietary scoring system operates on three independent dimensions:

### Fit Score (0-100)

"Is this person even in my target market?"

Fit measures how well a lead matches your ideal customer profile (ICP). It answers:

- Right industry?
- Right company size?
- Right role/seniority?
- Geographic match?
- Skill/background match?

### Intent Score (0-100)

"Is this person actively looking for a solution?"

Intent measures signals that show the lead is searching for, considering, or planning to buy something. It answers:

- Are they asking for recommendations?
- Have they mentioned switching tools?
- Are they complaining about current tools?
- Engaging with competitors?
- Posting about hiring/scaling challenges?

### Timing Score (0-100)

"Is this the right moment to reach them?"

Timing measures how urgent or immediate their needs appear. It answers:

- Did they just change jobs?
- Recent company funding/expansion?
- New hiring initiative?
- Recent product launches?
- Active engagement with relevant content?

## Understanding Score Ranges

Each score operates independently on a 0-100 scale. Here's what different ranges mean:

| Range  | Interpretation | What It Means                        |
|--------|----------------|--------------------------------------|
| 0-15   | Disqualified   | Poor fit or no interest signals      |
| 20-35  | Low            | Weak match, minimal intent detected  |
| 35-55  | Moderate       | Decent potential, but gaps remain    |
| 60-79  | Strong         | Clear alignment with your offer      |
| 80-100 | Ideal          | Perfect match, high intent, ready to buy |

Each dimension is scored independently. You might have:

- High fit (80) + Low intent (25) + High timing (85) = Someone in your market at the right moment, but not actively looking
- Low fit (30) + High intent (90) + High timing (75) = Someone actively buying, but the wrong persona

## The Composite Buyer Score

While fit, intent, and timing are independent, AutoReach combines them into a single **Buyer Score** (0-100) that appears on the Buyers page.

### The Formula

```
buyer_score = (fit × weight_fit) + (intent × weight_intent) + (timing × weight_timing)
```

The weights are dynamic based on your Offer's **signal likelihood**. When creating an offer, you set how likely it is that your target buyers post about this topic on social media:

- **High likelihood** - Intent signals weighted 50% (very relevant)
- **Medium likelihood** - Intent signals weighted 30% (somewhat relevant)
- **Low likelihood** - Intent signals weighted 20% (rare to post about)

### Example Calculation

Let's say you're selling a workflow automation tool with high signal likelihood (lots of people tweet about workflow automation):

```
Lead A: fit=75, intent=65, timing=55
→ (75 × 0.25) + (65 × 0.50) + (55 × 0.25)
→ 18.75 + 32.5 + 13.75
→ Buyer Score = 65 (ACTIVE)

Lead B: fit=85, intent=30, timing=80
→ (85 × 0.25) + (30 × 0.50) + (80 × 0.25)
→ 21.25 + 15 + 20
→ Buyer Score = 56 (MONITOR)
```

## Fit-Gated Promotion

AutoReach has a critical rule: **Fit >= 75 guarantees a minimum buyer_score of 60**.

This ensures that even if timing and intent are lower, someone who is a perfect ICP match gets flagged as ACTIVE. Strategic account penetration often requires reaching perfect-fit personas even if they are not actively buying right now.

```
If fit >= 75 AND buyer_score < 60:
  → buyer_score = 60 (automatically promoted)
```

## Critical Scoring Rules

AutoReach has immutable rules that override normal scoring:

### Rule 1: Industry Fit is Mandatory

If a lead's industry doesn't match your target industries, fit_score is capped at 40, regardless of other factors. You can't score someone as a great fit if they're in the wrong industry.

### Rule 2: Competitors Get Zero Fit

If a lead works at a competitor company, fit_score = 0 (disqualified). They are your customer's customer, not your customer.

### Rule 3: Internal Builders Aren't Buyers

If a lead is building a competing product (detected via signals, LinkedIn background, or custom rules), they are automatically disqualified. They are your competitor, not your prospect.

{% hint style="warning" %}
**Override Available:** You can manually override scoring rules via the UI (set "Manual Outreach" state) if you want to reach someone despite these filters.
{% endhint %}

## Source-Aware Intent Baselines

Different lead sources come with different intent baselines:

- **LinkedIn Job Search** (recent hire) - +15 intent boost (timing signal)
- **LinkedIn Content Search** (active posting) - +10 intent boost
- **Tweet Search** (keyword match) - +15 intent boost (explicit keyword matching)
- **Follower Extraction** - +0 (no intent signal, just awareness)
- **CSV Import** - +0 (no intent signal)

These baselines apply before the full scoring calculation to account for source bias. A CSV import of someone with no social signals shouldn't score the same as someone found actively tweeting about your keywords.

## Two Scoring Paths

AutoReach can score leads in two different ways, depending on when and how much compute you need:

### Path 1: Deep Analysis

Full LLM analysis that examines:

- Entire lead profile
- All enriched signals
- Custom offer-specific intent prompts
- Knowledge base context (if provided)

**When used:** Initial scoring, manual re-scoring, Buyer Intelligence dashboard deep dives

**Cost:** Higher compute, slower (30-90 seconds per lead)

**Accuracy:** Highest (captures nuanced context)

### Path 2: Fast Rescore

Recomputes the score from previously stored signal data without re-analyzing content. Uses:

- Cached signals from prior enrichment
- Signal weights from your offer
- Updated weights if you changed the offer definition

**When used:** Continuous background rescoring, new signal detection, daily scoring refreshes

**Cost:** Lower compute, fast (< 1 second)

**Accuracy:** Good (uses same signals, no new context)

{% hint style="info" %}
**Pro Tip:** Enable daily "Fast Rescore" to keep scores fresh as new signals appear on social media. Use "Deep Analysis" sparingly for high-value accounts or when troubleshooting why someone isn't scoring high.
{% endhint %}

## Score Changes Over Time

Lead scores are not static. They update when:

1. **New signals detected** - Background activity fetch finds new posts/engagement
2. **Job changes detected** - Career moves update experience and timing
3. **Offer redefined** - You update your ICP, keywords, or signal weights
4. **Manual rescore triggered** - You explicitly request re-analysis
5. **Re-engagement** - Lead responds to your message (new engagement activity)

A lead could be a poor_fit at month 1, then jump to active at month 3 because:

- They got promoted (role match improved)
- Started posting about your keywords (intent detected)
- Company announced funding (timing signal)
- Changed companies (potential new ICP match)

{% hint style="info" %}
**Monitor is Your Friend:** Leads in the monitor state (30-59) are watched for these score movements. AutoReach automatically promotes them to active if scoring triggers are met.
{% endhint %}

## Debugging a Low Score

If someone you think should score high is coming in low, check:

1. **Fit dimension** - Does their industry, company size, and role match your ICP?
2. **Intent dimension** - Are they posting/engaging about your keywords on social media?
3. **Timing dimension** - Are they showing urgency signals (new job, hiring activity)?
4. **Data completeness** - Has enrichment finished? Partial profiles score lower.
5. **Offer definition** - Is your target audience/keywords specific enough?

Request a **Deep Analysis** rescore and review the scoring breakdown in the Buyer Intelligence dashboard to see exactly why they scored where they did.
