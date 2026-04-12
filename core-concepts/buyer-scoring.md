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

## Understanding the Scores

Each dimension is scored independently on a 0-100 scale. A higher score means a stronger signal in that dimension. You might have:

- **High fit + Low intent:** Someone in your target market who is not actively looking yet
- **Low fit + High intent:** Someone actively buying, but not the right persona
- **High fit + High intent + High timing:** Your ideal buyer, ready to engage right now

The combination of all three dimensions determines whether a lead is worth reaching out to.

## The Composite Buyer Score

While fit, intent, and timing are independent, AutoReach combines them into a single **Buyer Score** (0-100) that appears on the Buyers page.

The weights between fit, intent, and timing are dynamic based on your Offer's **signal likelihood** setting. When your buyers frequently post about their needs on social media (high likelihood), intent signals carry more weight. When they rarely post (low likelihood), fit becomes the dominant factor.

AutoReach also applies intelligent safety rails so that strong ICP matches and high-intent leads are never missed, even if one dimension scores lower.

## Scoring Rules

AutoReach applies rules that override normal scoring:

- **Industry mismatch:** If a lead is in the wrong industry, their fit score is capped regardless of other factors
- **Competitors:** If a lead works at a competitor company, they are automatically disqualified
- **Internal builders:** If a lead is building a competing product, they are automatically disqualified

{% hint style="warning" %}
**Override Available:** You can manually override scoring rules via the UI (set "Manual Outreach" state) if you want to reach someone despite these filters.
{% endhint %}

## Source-Aware Scoring

Different lead sources carry different baseline signals. A lead found by searching for your keywords on X or LinkedIn carries inherent intent, while a CSV import or follower extraction has no intent signal by default. AutoReach accounts for this automatically so that high-signal sources score appropriately higher.

## Rescoring

AutoReach supports two ways to rescore leads:

- **Deep Analysis:** A full AI-powered analysis that examines the lead's entire profile, signals, and context. Use this for initial scoring, manual rescoring, or when you want to understand exactly why a lead scored the way they did.
- **Fast Rescore:** A lightweight recalculation based on existing signal data. Use this to quickly refresh scores after updating your offer definition or when new signals are detected.

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

## Next Steps

- **[Buyer States](buyer-states.md)**: Understand how scores translate into lead states and pipeline visibility
- **[Signal Detection](signals.md)**: See the full list of signals that power scoring
- **[Auto-Enrollment](../autopilot/auto-enrollment.md)**: Learn how high-scoring leads get enrolled into sequences automatically
