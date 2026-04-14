# Buyer Intelligence

AutoReach's Buyer Intelligence system is the heart of smart outreach. Instead of blasting everyone, it scores each lead across three dimensions (fit, intent, and timing), assigns a buyer state, and uses dozens of signals to predict who is most likely to buy right now.

---

## The Three Scoring Dimensions

Each lead is scored independently on three dimensions, each on a 0-100 scale.

### Fit Score

"Is this person in my target market?"

Fit measures how well a lead matches your ideal customer profile (ICP):

- Right industry?
- Right company size?
- Right role/seniority?
- Geographic match?
- Skill/background match?

### Intent Score

"Is this person actively looking for a solution?"

Intent measures signals that show the lead is searching for, considering, or planning to buy something:

- Are they asking for recommendations?
- Have they mentioned switching tools?
- Are they complaining about current tools?
- Engaging with competitors?
- Posting about hiring/scaling challenges?

### Timing Score

"Is this the right moment to reach them?"

Timing measures how urgent or immediate their needs appear:

- Did they just change jobs?
- Recent company funding/expansion?
- New hiring initiative?
- Recent product launches?
- Active engagement with relevant content?

### Understanding the Scores

Each dimension is scored independently. You might have:

- **High fit + Low intent:** Someone in your target market who is not actively looking yet
- **Low fit + High intent:** Someone actively buying, but not the right persona
- **High fit + High intent + High timing:** Your ideal buyer, ready to engage right now

The combination of all three determines the lead's composite **Buyer Score** (0-100) and their buyer state.

---

## Buyer States

Every lead has a **buyer state** that represents their current status in your pipeline. The state determines where they appear in the UI, whether they are eligible for outreach, and how AutoReach treats them.

### Active (shown as "Ready" in the UI)

This person is ready to buy. They meet your ICP, show buying intent, and the timing is right.

- Appears on the **Buyers** page, **Ready** tab
- Fully eligible for sequence enrollment and auto-enrollment
- **Next action:** Add to a sequence and start outreach

### Monitor (shown as "Emerging" in the UI)

This person has potential, but is not quite ready yet. Maybe fit is strong but intent is weak, or the timing is not there yet.

- Appears on the **Buyers** page, **Emerging** tab
- Can be enrolled in sequences, but not recommended for aggressive outreach
- AutoReach periodically re-checks these leads for new buying signals and automatically promotes them to Active if they qualify

### Poor Fit (shown as "Low Priority" in the UI)

This person does not match your ideal customer profile well. Something significant does not line up - wrong industry, wrong seniority, or insufficient signals.

- Appears on the **Buyers** page, **Low Priority** tab
- Not recommended for outreach
- Still monitored on a longer cycle for signal changes

### Disqualified

This person is far outside your ICP with almost no chance of conversion. They remain in the database but are excluded from automatic processing.

- Appears on the **Buyers** page, **Disqualified** tab
- Must be overridden to Manual Outreach before enrollment
- Skipped by the resurfacing scheduler

### Manual Outreach (shown as "Manual" in the UI)

You have decided this person is worth reaching out to, overriding the scoring system.

- Appears on the **Buyers** page, **Manual** tab
- Eligible for sequence enrollment, treated like Active
- Protected from automatic pipeline rescoring (unless you explicitly trigger a manual rescore)
- **When to use:** VIP accounts, strategic partnerships, founder relationships, or intentional lower-funnel experiments

### Not Scored (shown as "Analyzing" in the UI)

Lead has not completed initial enrichment/scoring.

- Appears on the **Buyers** page, **Analyzing** tab
- Not eligible until scoring completes
- Background enrichment and scoring in progress

### State Transitions

Leads move between states based on their scores. Higher scores promote to Active, moderate scores land in Monitor, low scores go to Poor Fit, and very low fit leads are Disqualified.

Leads can move up or down as new signals appear. Active leads can be demoted on rescore if their signals weaken. Poor Fit leads can be promoted if they change jobs, start posting about relevant pain points, or show new timing signals.

You can manually change any lead's state via the UI. Manual Outreach overrides scoring and treats the lead as eligible for enrollment.

### State Impact on Sequences

| Lead State | Auto-Enrollment | Manual Enrollment |
|---|---|---|
| Active | Yes | Immediate enrollment, outreach begins |
| Manual Outreach | No | Immediate enrollment, treated as Active |
| Monitor | No | Allowed, but not recommended |
| Poor Fit | No | Allowed (manual override), low priority |
| Not Scored | No | Enrollment queued, starts when scoring completes |
| Disqualified | No | Must override to Manual Outreach first |

Only **Active** leads are eligible for automatic enrollment by Autopilot.

---

## Signals

Signals are data points that indicate a lead is interested, actively buying, or urgently needs your solution. They power buyer intelligence scoring and help identify who is ready to buy.

### Explicit Intent Signals

- **Asked for Recommendation** - Lead explicitly asked for product/service recommendations
- **Switching From Competitor** - Lead mentioned switching away from a competitor (one of the strongest signals)
- **Looking for Alternative** - Lead is actively searching for an alternative
- **Complained About Current Tool** - Lead complained about their current tool or process
- **Tool Mention** - Lead mentioned using or considering a competitor or similar tool

### Company-Level Signals

- **Funding** - Company announced a new funding round
- **Product Launch** - Company launched a new product or major feature
- **Mergers and Acquisitions** - Company acquired or was acquired
- **Cost Cutting** - Company announced layoffs, consolidation, or cost reduction
- **IPO Filing** - Company filed for IPO
- **Geographic Expansion** - Company expanding to a new geographic market

### Engagement Signals

- **Competitor Engagement** - Lead engaged with content from competitor companies
- **Engagement Pattern** - Lead has high engagement on posts related to your category
- **Own Post Engagement** - Lead engaged with YOUR posts (inbound signal). AutoReach detects replies, likes, retweets, new follows (X) and reactions, comments, mentions, connection requests, profile views (LinkedIn)
- **Competitor Customer** - Lead is a confirmed user of a competing product
- **Interaction Orbit** - Lead suddenly starts engaging with multiple competitor or adjacent vendor accounts in a short time window, indicating active evaluation. See [Account Signals](../settings/account-signals.md) for details

### Hiring Signals

- **Hiring Activity** - Company is actively hiring
- **Hiring Roles** - Specific roles being hired for
- **Job Change Detected** - Lead recently changed jobs (strong timing signal)
- **Role Tenure** - How long the lead has been in their current role
- **New Hire** - Lead started their current role recently

### Custom Intent Signals

Beyond built-in signals, your **Offer** can define custom intent signals specific to your product. Specify keywords and phrases that your buyers use, and AutoReach monitors for mentions and factors them into scoring.

### Offer Pain Match

AutoReach automatically checks if a lead's content matches your offer's pain points. If a lead posts about challenges you solve, it is detected as a pain match signal and boosts their intent score.

### Industry and Classification

- **Industry Classification** - Compared against your offer's target industries. A match increases fit
- **Competitor Employee** - Lead works at a competing company. Scored as Poor Fit

### Location Match

Lead's location compared against your preferred locations. The check method depends on your offer's **location filter type**: "lead" matches the lead's own location; "company_hq" matches the company's headquarters location.

### How Signals Feed Scoring

Signals feed into the three scoring dimensions:

- **Fit:** Industry match, role match, company size, location
- **Intent:** Asking for recommendations, switching tools, complaints, pain point matches, competitor engagement, competitor customer status, interaction orbit clusters, custom intent signals
- **Timing:** Job changes, new hires, funding, IPO filings, product launches, hiring activity

The more signals a lead has, and the stronger those signals are, the higher their scores.

### Signal Recency

AutoReach continuously monitors for new signals. It periodically rechecks leads for job changes, new posts, and company activity. Recent signals carry more weight than older ones.

### Viewing Lead Signals

In the lead profile, you can see:

- All detected signals in the lead's signal summary
- Intent strength (high/medium/low/none) - an overall AI-assessed rating of buying intent
- Account-level signals with individual strength ratings and dates
- Raw activity (posts, comments, job changes)

---

## Scoring Rules

AutoReach applies rules that override normal scoring:

- **Industry mismatch:** If a lead is in the wrong industry, their fit score is reduced
- **Competitors:** If a lead works at a competitor company, they are automatically disqualified
- **Internal builders:** If a lead is building a competing product, they are automatically disqualified

> **Note:** You can manually override scoring rules via the UI (set "Manual Outreach" state) if you want to reach someone despite these filters.

## Lead Source Context

AutoReach automatically considers how a lead was discovered when scoring. A lead found by searching for your keywords carries inherent intent signal, while a CSV import or follower extraction starts with no intent signal. This happens automatically - no configuration needed.

## Rescoring

You can rescore leads at any time by selecting them and running **AI Analysis**. This performs a full AI-powered analysis that examines the lead's entire profile, signals, and context. Use it for initial scoring, manual rescoring, or when you want to understand exactly why a lead scored the way they did.

## Score Feedback

If you disagree with a lead's score, you can correct it directly. Open a lead's detail view and click:

- **Should be a buyer** (thumbs up) - if the lead scored low but you believe they are a good fit
- **Should NOT be a buyer** (thumbs down) - if the lead scored high but is not actually relevant

This opens the **Offer Refinement** flow. AutoReach analyzes why the score is off and suggests changes to your offer definition - adjustments to your target audience description, pain points, or ICP criteria. You can review and edit the suggestions before applying them. Once applied, the offer is updated and the lead is rescored.

This feedback loop improves scoring accuracy over time by aligning your offer definition with your real-world judgment.

## Score Changes Over Time

Lead scores are not static. They update when:

1. **New signals detected** - Background activity fetch finds new posts/engagement
2. **Job changes detected** - Career moves update experience and timing
3. **Offer redefined** - You update your ICP, keywords, or signal weights
4. **Manual rescore triggered** - You explicitly request re-analysis
5. **Re-engagement** - Lead responds to your message

## Best Practices

> **Tip:** Your conversion rates will be highest with Active leads. Spend 80% of your effort on this list.

> **Tip:** Your next batch of Active leads comes from the Emerging (Monitor) state. Check in weekly to see who got promoted.

> **Warning:** A lead might be Poor Fit today and Active tomorrow if they change jobs or companies. Keep monitoring.

> **Tip:** Use Manual Outreach strategically. It is powerful for high-value accounts, but do not overuse it.

> **Tip:** Leads actively asking for recommendations or evaluating tools are significantly more likely to reply than those with no intent signal.

> **Tip:** If you notice a certain phrase or pattern in conversations with buyers, add it as a custom signal. AutoReach will find more people with that pattern.

## Next Steps

- **[Account Signals](../settings/account-signals.md)**: Interaction Orbit and company-level heat scoring
- **[Auto-Enrollment](../autopilot/continuous-operations.md)**: How Active leads get enrolled into sequences automatically
- **[Finding Leads](../finding-leads/overview.md)**: Discover leads showing the signals that matter most
