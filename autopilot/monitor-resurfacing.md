# Monitor Resurfacing

Monitor Resurfacing is how Autopilot gives low-score leads a second chance. Instead of abandoning prospects who aren't ready yet, Autopilot re-checks them on a tiered schedule for new buying signals and moves them to active outreach the moment they become ready.

## Why Resurfacing Matters

A lead with a score of 45 today might have a score of 75 next month when:

- They post about your space
- They change jobs (headline updates)
- They start following competitors
- Their company hires your ICP roles

Without resurfacing, you'd miss them forever. With it, Autopilot catches the exact moment they become buyers.

## Tiered Check Frequency

Autopilot doesn't check all low-score leads equally. Instead, it uses a tiered approach:

| Tier       | Score Range | Re-check Frequency | Rationale                        |
| ---------- | ----------- | ------------------- | -------------------------------- |
| **Tier 1** | 50-59       | Every 5 days        | Warm prospects, may convert soon |
| **Tier 2** | 40-49       | Every 10 days       | Medium interest, worth monitoring |
| **Tier 3** | 30-39       | Every 14 days       | Some signals, but not urgent     |
| **Tier 4** | 0-29        | Every 21 days       | Very low intent, occasional checks |

This means your warmest prospects (Tier 1) get checked most frequently, while colder prospects are checked less often. This saves system resources while keeping them on your radar.

{% hint style="info" %}
**Smarter than batch scoring.** Resurfacing prioritizes warm leads, so you catch conversions faster while still monitoring the full pipeline.
{% endhint %}

## What Resurfacing Checks For

When Autopilot re-checks a lead, it looks for:

### LinkedIn Headline Changes

- **Job change detection**: If someone's headline changed (new company, new role)
- **Tenure reset**: Their "time in role" resets, indicating a transition
- **Score boost**: Job changes trigger a **+25 point scoring boost**

This is one of the highest-signal events. A job change often means new problems and new buying intent.

### Company Job Data Refresh

- **Stale data detection**: If company data hasn't been updated in 7+ days
- **Job board updates**: Recent hiring at their company
- **Growth indicators**: Company is scaling (hiring signals)

### Activity Patterns

- **Recent posts**: Are they posting about your space?
- **Following patterns**: Unfollowed competitors, followed thought leaders?
- **Engagement**: Likes, comments, reshares on relevant topics

### Social Signals

- **Follower growth**: Growing audience (influence indicator)
- **Industry signals**: Mentions, tags, and associations
- **Profile completeness**: More complete profiles often indicate active job search

## Resurfacing Budget and Pace

Autopilot budgets its resurfacing work to avoid overloading the system:

- **Time per lead:** 20 minutes maximum per user per window
- **Daily volume:** 40-60 leads/window, approximately **120-180 leads/day** per user

This means you can rescan your entire pipeline every 2-3 days without performance issues.

## Prioritization Logic

Leads are checked in priority order:

1. **Tier 1 (score 50-59)**: Checked first
2. **Overdue leads**: Any lead past its re-check window gets a priority boost
3. **Tier 2 (score 40-49)**: Checked after Tier 1
4. **Tier 3 and 4**: Checked as capacity allows

A Tier 4 lead that hasn't been checked in 25 days gets boosted in priority, ensuring nothing falls through the cracks.

## Score Improvement and Upgrade

When resurfacing finds positive signals, a lead's score can increase dramatically:

| Signal            | Score Impact   |
| ----------------- | -------------- |
| New headline      | +25 points     |
| Relevant activity | +5-10 points   |
| Matching new role | +15-20 points  |

Example: A lead at score 45 (Tier 2) posts about your space (+10) and changes jobs (+25) in the same window. New score: 80. They are automatically **upgraded to "active" and moved into sequences.**

{% hint style="success" %}
**Automatic upgrades.** When a lead hits 60+ during resurfacing, they're immediately notified and enrolled. There is no waiting for the next 5-minute auto-enrollment check.
{% endhint %}

## The Resurfacing Notification

When a lead scores high enough to activate during resurfacing:

1. **You're notified**: Dashboard alert or notification
2. **They're auto-enrolled**: Moved into the appropriate sequence
3. **Activity logged**: You can see the exact signals that triggered activation

Example notification: "Sarah Chen upgraded to Active (score 65). Headline change: VP to Director of Operations. Auto-enrolled in LinkedIn sequence."

## How Resurfacing Feeds Your Pipeline

```
Lead scores 35 (Tier 4)
         |
Re-checked every 21 days
         |
Posts about your keywords (+10 points -> score 45, Tier 2)
         |
Re-checked every 10 days
         |
Changes jobs (+25 points -> score 70, Active!)
         |
Auto-upgraded and enrolled into sequence
         |
First message reaches them at the right time
```

Resurfacing is how Autopilot catches leads at the moment they become buyers, not too early, not too late.

## Monitoring Resurfacing Activity

Check resurfacing stats:

1. Go to **Autopilot Dashboard > Monitor**
2. View:
   - Total leads in monitoring (all tiers)
   - Breakdown by tier (Tier 1, 2, 3, 4)
   - Leads upgraded to active (last 7 days)
   - Next resurfacing window (when tier checks run)
3. Check **Activity Log** to see recent resurfacing discoveries

## Can I Adjust Resurfacing?

You can customize:

- **Tier thresholds**: Change score ranges for each tier
- **Re-check frequency**: Speed up or slow down checks per tier
- **Signals to watch**: Prioritize headline changes, activity, or other signals
- **Pause monitoring**: Temporarily stop resurfacing for an Offer

Go to **Autopilot Settings > Monitoring** to adjust.

## Why Resurfacing Matters for ROI

Many deals are missed because timing is wrong. A lead at score 40 six months ago might be at score 75 today, but if you never checked again, you'd never know.

Resurfacing solves this by:

- Reducing sales cycle friction (reaching at the right time)
- Increasing close rates (higher intent at contact time)
- Maximizing lead value (getting second, third, or tenth chances)

## Common Questions

**Q: Why don't you check all leads every day?**
A: Cost and noise. Checking low-score leads daily wastes resources. Tiered frequency balances coverage with efficiency.

**Q: How accurate are score changes?**
A: LinkedIn headline changes are 100% accurate (we detect them). Other signals are probabilistic but high-confidence.

**Q: What if someone's score keeps bouncing around?**
A: Normal. Activity goes up and down. We wait for sustained signal before auto-enrolling.

**Q: Can I manually upgrade a lead?**
A: Yes. You can manually enroll any lead into a sequence anytime, regardless of score.

**Q: What happens to a lead after they're activated?**
A: They move into your sequence and are no longer resurfaced (they're active). If they don't convert and the sequence completes, they move back to monitoring.

---

Resurfacing is your safety net. It ensures no lead is left behind. They just have to earn their way back onto your active list.
