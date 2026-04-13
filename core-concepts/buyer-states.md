# Buyer States

Every lead in AutoReach has a **buyer state** that represents their current status in your pipeline. The state determines where they appear in the UI, whether they're eligible for outreach, and how AutoReach treats them.

## The Six Buyer States

### 1. Active (shown as "Ready" in the UI)

**Condition:** Buyer Score >= 60

**What it means:** This person is ready to buy. They meet your ICP, show buying intent, and the timing is right.

**Where it appears:** The **Buyers** page, **Ready** tab

**Outreach eligibility:** Fully eligible for sequence enrollment and immediate campaigns

**Next action:** Add to a sequence and start outreach

**Example:** A VP of Operations at a mid-market SaaS company just posted "evaluating project management tools" and has 5 years of tenure. Buyer Score = 72.

### 2. Monitor (shown as "Emerging" in the UI)

**Condition:** Buyer Score 30-59

**What it means:** This person has potential, but they're not quite ready yet. Maybe fit is strong but intent is weak, or the timing isn't quite there. You're keeping an eye on them.

**Where it appears:** The **Buyers** page, **Emerging** tab

**Outreach eligibility:** Can be enrolled in sequences, but not recommended. Better used for nurture or light-touch engagement.

**AutoReach behavior:** The resurfacing scheduler periodically rescores monitor leads (every 5-14 days depending on score). If new signals boost their score to 60+, they automatically promote to **active**.

**Next action:** Monitor for score movements, or manually enroll in a light-touch sequence if high strategic value

**Example:** A hiring manager at an ideal-fit company is active on LinkedIn but hasn't posted anything suggesting they're looking to buy. Buyer Score = 48.

### 3. Poor Fit (shown as "Low Priority" in the UI)

**Condition:** Buyer Score < 30, but fit score >= 15 or buyer score >= 15

**What it means:** This person doesn't match your ideal customer profile well. Whether it's a fit gap, wrong industry, or wrong seniority, something significant doesn't line up. Competitors flagged manually or detected during scoring also land here with zeroed scores.

**Where it appears:** The **Buyers** page, **Low Priority** tab

**Outreach eligibility:** Not recommended. Low ROI outreach.

**AutoReach behavior:** Still tracked and monitored. The resurfacing scheduler checks Poor Fit leads on a 21-day cycle and rescores them if new signals appear.

**Next action:** Generally ignore unless you're running experiments or doing account-based targeting on strategic accounts

**Example:** A junior IC at an enterprise Fortune 500 company (you target mid-market SMBs). Buyer Score = 22.

### 4. Disqualified

**Condition:** Fit score < 15 AND buyer score < 15

**What it means:** This person is so far outside your ICP that there is almost no chance of conversion. They remain in the database but are excluded from automatic processing.

**Where it appears:** The **Buyers** page, **Disqualified** tab

**Outreach eligibility:** Not eligible. Must be overridden to Manual Outreach first.

**AutoReach behavior:** Skipped by the resurfacing scheduler and automatic pipeline scoring. Can be force-rescored manually.

**Next action:** Generally ignore. If circumstances change (e.g., they switch companies), you can manually change their state or trigger a rescore.

**Example:** A student with no professional experience and no intent signals. Fit score = 8, buyer score = 6.

### 5. Manual Outreach (shown as "Manual" in the UI)

**Condition:** Manually set by user, regardless of score

**What it means:** You've decided this person is worth reaching out to, overriding the scoring system. This is a full buyer state, not just a flag.

**Where it appears:** The **Buyers** page, **Manual** tab

**Outreach eligibility:** Eligible for sequence enrollment, treated like active

**AutoReach behavior:** Protected from automatic pipeline rescoring. However, if you explicitly trigger a manual rescore, the state will be overwritten by whatever the new score produces.

**When to use:** VIP accounts, strategic partnerships, founder relationships, testing, or intentional lower-funnel experiments

**Example:** You want to reach the founder of a partner company. Their buyer score is 25, but you know the relationship is valuable. Set to Manual Outreach.

### 6. Not Scored (shown as "Analyzing" in the UI)

**Condition:** Lead hasn't completed initial enrichment/scoring

**What it means:** You just added this lead, but they haven't been fully enriched or scored yet. They're in progress.

**Where it appears:** The **Buyers** page, **Analyzing** tab

**Outreach eligibility:** Not eligible until scoring completes. Wait for state transition.

**AutoReach behavior:** Background enrichment and scoring in progress

**Next action:** Wait for enrichment. You'll see their state update within minutes to hours depending on the source.

**Example:** You just added alice@example.com manually 2 minutes ago. Still enriching.

## State Transitions

Leads move between states based on:

### Automatic Score-Based Transitions

Once enrichment completes and the initial score is calculated, the lead is placed into the appropriate state based on their buyer score. Higher scores go to Active, moderate scores to Monitor, low scores to Poor Fit, and very low fit and intent leads are Disqualified.

### Score Movement Between States

Leads can move up or down as new signals appear. Active leads can be demoted to Monitor or Poor Fit on rescore if their signals weaken. Poor Fit leads can be promoted to Monitor or Active if they change jobs, start posting about relevant pain points, or show new timing signals.

The **resurfacing scheduler** automatically rescores Monitor and Poor Fit leads on a tiered cycle:

| Score Range | Recheck Frequency |
|---|---|
| 50-59 (high monitor) | Every 5 days |
| 40-49 (mid monitor) | Every 10 days |
| 30-39 (low monitor) | Every 14 days |
| 0-29 (poor fit) | Every 21 days |

Before rescoring, the scheduler checks for LinkedIn headline changes (job change detection) and refreshes company hiring signals if stale.

**Example:** A lead scored low because they worked in a tangential industry with no signals. Three weeks later, they post "just joined Acme Corp as Director of Sales" (your target industry + job change signal). The resurfacing scheduler detects the headline change, rescores them, and promotes them to Active.

### Manual Overrides

You can manually change any lead's state via the UI:

- **Manual Outreach** — overrides scoring, treated as active for enrollment
- **Any other state** — manually set via the Buyers page state control

> **Warning:** Manual Outreach is protected from automatic pipeline rescoring. But if you explicitly trigger a manual rescore on that lead, the state will be overwritten by the new calculated state.

> **Note:** Disqualified leads won't resurface automatically -- the resurfacing scheduler skips them. To re-evaluate a disqualified lead, change their state manually or trigger a force rescore.

## Where States Appear in the UI

### Buyers Page

The Buyers page has tabs for **all six states**: Ready, Emerging, Low Priority, Manual, Analyzing, and Disqualified. Each tab shows leads in that state.

**Filters:** Sort by score, signals, activity date, or search by name

### All Leads Page

Contains all leads across all states. All six buyer states are filterable.

**Filters:** Filter by state, score range, signal type, source, and more

### Dashboard

**Active count:** How many buyers you have this week

**Monitor count:** Potential deals in development

**Conversion funnel:** Active → Replied → Meeting Booked

## State Impact on Sequences

When you add a lead to a sequence:

| Lead State      | Auto-Enrollment | Manual Enrollment                              |
|-----------------|-----------------|--------------------------------------------------|
| Active          | Yes             | Immediate enrollment, outreach begins            |
| Manual Outreach | No              | Immediate enrollment, treated as Active          |
| Monitor         | No              | Allowed, but not recommended                     |
| Poor Fit        | No              | Allowed (manual override), low priority          |
| Not Scored      | No              | Enrollment queued, starts when scoring completes |
| Disqualified    | No              | Must override to Manual Outreach first           |

Only **active** leads are eligible for automatic enrollment by Autopilot. All other states require manual enrollment.

## Best Practices

> **Tip:** Your conversion rates will be highest with active leads. Spend 80% of your effort on this list.

> **Tip:** Your next batch of active leads comes from the monitor state. Check in weekly to see who got promoted.

> **Warning:** A lead might be Poor Fit today and Active tomorrow if they change jobs or companies. Keep monitoring.

> **Tip:** Use Manual Outreach strategically. It's powerful for high-value accounts, but don't overuse it. It bypasses the scoring logic for a reason.

## Next Steps

- **[Buyer Intelligence & Scoring](buyer-scoring.md)**: Understand how fit, intent, and timing scores are calculated
- **[Auto-Enrollment](../autopilot/auto-enrollment.md)**: See how active leads get enrolled into sequences automatically
