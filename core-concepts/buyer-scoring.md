# Buyer Intelligence & Scoring

AutoReach's **Buyer Intelligence** system is the heart of smart outreach. Instead of blasting everyone, it scores each lead across three dimensions (fit, intent, and timing) and uses that data to predict who is most likely to buy right now.

## The Intent-Led Scoring Model

AutoReach uses an **intent-led** scoring model: leads with active buying signals surface above cold ICP matches, while strong ICP fits still score well. The system scores three independent dimensions:

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

Intent is the primary driver of the composite score. It measures signals that show the lead is searching for, considering, or planning to buy something:

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

- **High fit + Low intent:** Someone in your target market who is not actively looking yet — they'll land in monitor, not active
- **Low fit + High intent:** Someone actively buying, but not the right persona — intent alone won't promote them without decent fit
- **High fit + High intent + High timing:** Your ideal buyer, ready to engage right now

The combination of all three dimensions determines whether a lead is worth reaching out to.

## The Composite Buyer Score

While fit, intent, and timing are independent, AutoReach combines them into a single **Buyer Score** (0-100) that appears on the Buyers page.

The balance between fit, intent, and timing adapts automatically based on your market. AutoReach analyzes your offer and determines how likely your target buyers are to post about their needs on social media. When buyers are active on social media, intent signals carry more weight. When buyers are quieter, ICP fit becomes the dominant factor.

### Smart Promotion

AutoReach ensures that high-signal leads are never buried by low scores in other dimensions. A lead with strong buying signals and reasonable ICP fit will always surface, even if their timing score is low. Similarly, a near-perfect ICP match stays visible even without active intent signals — they are worth monitoring.

## Scoring Rules

AutoReach applies rules that override normal scoring:

- **Industry mismatch:** If a lead is in the wrong industry, their fit score is capped regardless of other factors
- **Competitors:** If a lead works at a competitor company, they are automatically disqualified
- **Internal builders:** If a lead is building a competing product, they are automatically disqualified

> **Warning:** You can manually override scoring rules via the UI (set "Manual Outreach" state) if you want to reach someone despite these filters.

## Source-Aware Scoring

Different lead sources carry different baseline signals. A lead found by searching for your keywords on X or LinkedIn carries inherent intent, while a CSV import or follower extraction has no intent signal by default. AutoReach accounts for this automatically so that high-signal sources score appropriately higher.

## Rescoring

You can rescore leads at any time by selecting them and running **AI Analysis**. This performs a full AI-powered analysis that examines the lead's entire profile, signals, and context. Use it for initial scoring, manual rescoring, or when you want to understand exactly why a lead scored the way they did.

## Score Changes Over Time

Lead scores are not static. They update when:

1. **New signals detected** - Background activity fetch finds new posts/engagement
2. **Job changes detected** - Career moves update experience and timing
3. **Offer redefined** - You update your ICP, keywords, or signal weights
4. **Manual rescore triggered** - You explicitly request re-analysis
5. **Re-engagement** - Lead responds to your message (new engagement activity)

A lead could be Poor Fit at month 1, then jump to Active at month 3 because:

- They got promoted (role match improved)
- Started posting about your keywords (intent detected)
- Company announced funding (timing signal)
- Changed companies (potential new ICP match)

> **Tip:** Leads in the monitor state (30-59) are watched for these score movements. AutoReach automatically promotes them to active if scoring triggers are met.

## Score Feedback

If you disagree with a lead's score, you can correct it directly. Open a lead's detail view and click:

- **Should be a buyer** (thumbs up) — if the lead scored low but you believe they are a good fit
- **Should NOT be a buyer** (thumbs down) — if the lead scored high but is not actually relevant

This opens the **Offer Refinement** flow. AutoReach analyzes why the score is off and suggests changes to your offer definition — adjustments to your target audience description, pain points, or ICP criteria. You can review and edit the suggestions before applying them. Once applied, the offer is updated and the lead is rescored against the refined definition.

This feedback loop improves scoring accuracy over time by aligning your offer definition with your real-world judgment about who is and isn't a good prospect.

## Next Steps

- **[Buyer States](buyer-states.md)**: Understand how scores translate into lead states and pipeline visibility
- **[Signal Detection](signals.md)**: See the full list of signals that power scoring
- **[Auto-Enrollment](../autopilot/auto-enrollment.md)**: Learn how high-scoring leads get enrolled into sequences automatically
