# Buyer States

Every lead in AutoReach has a **buyer state** that represents their current status in your pipeline. The state determines where they appear in the UI, whether they're eligible for outreach, and how AutoReach treats them.

## The Five Buyer States

### 1. Active

**Condition:** Buyer Score >= 60

**What it means:** This person is ready to buy. They meet your ICP, show buying intent, and the timing is right.

**Where it appears:** The **Buyers** page (your hottest prospects)

**Outreach eligibility:** Fully eligible for sequence enrollment and immediate campaigns

**Next action:** Add to a sequence and start outreach

**Example:** A VP of Operations at a mid-market SaaS company just posted "evaluating project management tools" and has 5 years of tenure. Buyer Score = 72.

### 2. Monitor

**Condition:** Buyer Score 30-59

**What it means:** This person has potential, but they're not quite ready yet. Maybe fit is strong but intent is weak, or the timing isn't quite there. You're keeping an eye on them.

**Where it appears:** The **All Leads** page

**Outreach eligibility:** Can be enrolled in sequences, but not recommended. Better used for nurture or light-touch engagement.

**AutoReach behavior:** Continuous signal monitoring. If new signals appear that boost their score to 60+, they automatically promote to **active**.

**Next action:** Monitor for score movements, or manually enroll in a light-touch sequence if high strategic value

**Example:** A hiring manager at an ideal-fit company is active on LinkedIn but hasn't posted anything suggesting they're looking to buy. Buyer Score = 48.

### 3. Poor Fit

**Condition:** Buyer Score < 30

**What it means:** This person doesn't match your ideal customer profile well. Whether it's a fit gap, wrong industry, or wrong seniority, something significant doesn't line up.

**Where it appears:** The **All Leads** page (filtered by state or score range)

**Outreach eligibility:** Not recommended. Low ROI outreach.

**AutoReach behavior:** Still tracked and monitored, but deprioritized.

**Next action:** Generally ignore unless you're running experiments or doing account-based targeting on strategic accounts

**Example:** A junior IC at an enterprise Fortune 500 company (you target mid-market SMBs). Buyer Score = 22.

### 4. Disqualified

**Condition:** Both fit_score < 15 AND intent_score < 15

**What it means:** AutoReach has automatically removed this person from your database. They are so misaligned that there's no point tracking them further.

**Where it appears:** Not visible in normal UI (archived/deleted)

**Outreach eligibility:** Not eligible. Permanently disqualified.

**AutoReach behavior:** Removed from further processing

**Next action:** None. Move on.

**Example:** Someone working at a direct competitor, with zero intent signals. Permanently disqualified.

### 5. Not Scored

**Condition:** Lead hasn't completed initial enrichment/scoring

**What it means:** You just added this lead, but they haven't been fully enriched or scored yet. They're in progress.

**Where it appears:** The **All Leads** page (typically sorted to bottom)

**Outreach eligibility:** Not eligible until scoring completes. Wait for state transition.

**AutoReach behavior:** Background enrichment pipeline running (x_find, x_enrichment, linkedin_find, linkedin_enrichment, scoring)

**Next action:** Wait for enrichment. You'll see their state update within minutes to hours depending on the source.

**Example:** You just added alice@example.com manually 2 minutes ago. Still enriching.

## Manual Outreach Override

Beyond the five automatic states, you can set a lead to **Manual Outreach** regardless of their calculated buyer score.

**When to use:** VIP accounts, strategic partnerships, founder relationships, testing, or intentional lower-funnel experiments

**Behavior:** Treated as **active** for outreach purposes, even if their score is 15

**Example:** You want to reach the founder of a competitor (fit_score = 0) to explore a potential partnership. Set to Manual Outreach to override disqualification.

## State Transitions

Leads move between states based on:

### Automatic Score-Based Transitions

```
not_scored
  ↓ (enrichment completes, initial score calculated)
  ├→ active (score >= 60)
  ├→ monitor (30-59)
  ├→ poor_fit (< 30)
  └→ disqualified (fit < 15 AND intent < 15)
```

### Score Movement Within States

```
poor_fit (< 30)
  ↑ (new signal detected, intent jumps)
  └→ monitor (30-59)
      ↑ (timing signal + engagement)
      └→ active (>= 60)
```

Example: A lead was poor_fit (score 28) because they worked in a tangential industry with no signals. Three weeks later, they post "just joined Acme Corp as Director of Sales" (your target industry, job change signal). AutoReach rescores them to 62 and promotes to active.

### Manual Overrides

You can manually override any lead into:

- **Manual Outreach** (regardless of score)
- **Remove from platform** (delete permanently)

{% hint style="info" %}
**Resurfacing:** Disqualified leads won't resurface automatically. If someone was disqualified (worked at competitor) and then moves to a company in your ICP, you would need to manually re-add them or contact support to restore their profile.
{% endhint %}

## Where States Appear in the UI

### Buyers Page

Only **active** leads appear here. This is your hot list of people ready to buy.

**Filters:** Sort by score, signals, activity date, or search by name

### All Leads Page

Contains: **monitor**, **poor_fit**, **not_scored**, and **manual_outreach** leads

**Filters:** Filter by state, score range, signal type, source, and more

### Dashboard

**Active count:** How many buyers you have this week

**Monitor count:** Potential deals in development

**Conversion funnel:** active, replied, meeting_booked

## State Impact on Sequences

When you add a lead to a sequence:

| Lead State      | Behavior                                                    |
|-----------------|-------------------------------------------------------------|
| active          | Immediate enrollment, outreach begins                       |
| monitor         | Enrollment allowed, but marked as nurture                   |
| poor_fit        | Enrollment allowed (manual override), low priority          |
| disqualified    | Cannot enroll (must override to Manual Outreach first)      |
| not_scored      | Enrollment queued, starts when scoring completes            |
| manual_outreach | Enrollment immediate, treated as active                     |

## Best Practices

{% hint style="info" %}
**Focus on Active:** Your conversion rates will be highest with active leads. Spend 80% of your effort on this list.
{% endhint %}

{% hint style="info" %}
**Monitor is the Future:** Your next batch of active leads comes from the monitor state. Check in weekly to see who got promoted.
{% endhint %}

{% hint style="warning" %}
**Don't Ignore Timing:** A lead might be poor_fit today and active tomorrow if they change jobs or companies. Keep monitoring.
{% endhint %}

{% hint style="info" %}
**Use Manual Outreach Strategically:** It's powerful for high-value accounts, but don't overuse it. It bypasses the scoring logic for a reason.
{% endhint %}
