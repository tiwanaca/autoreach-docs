# Scheduling & Send Limits

AutoReach respects platform limits and maintains safe, natural-looking behavior to keep your accounts healthy. This page explains how scheduling, rate limiting, and activity windows work.

## Activity Window

The **Activity Window** defines when AutoReach sends messages and takes actions. It simulates real human work hours. You don't work at 3am, and neither should your automation.

### Setting Your Activity Window

1. Go to **Account Settings** > **Activity Window**
2. Set your preferred hours (e.g., 9am-9pm)
3. Choose your timezone

### How It Works

- **DMs, Replies, Follows, etc.** only execute during your Activity Window
- **Enrichment and lead qualification** can run 24/7 (see below)
- **Limits reset daily** at the start of your Activity Window

**Example:** If your Activity Window is 9am-9pm US Eastern:

- A DM scheduled for 8:30am ET is queued and sent at 9:01am ET
- Connection requests made at 11:30pm ET are queued for 9am ET the next day

{% hint style="info" %}
Your Activity Window is timezone-aware. If you travel, you can update it to stay aligned with your local time.
{% endhint %}

### 24/7 Pipeline Mode

Enable **24/7 Pipeline Mode** in settings to run enrichment and lead scoring around the clock while keeping outreach limited to your Activity Window:

- **Enrichment:** Runs 24/7 (finds tech stack, funding info, intent signals)
- **Lead Scoring:** Runs 24/7 (calculates buyer readiness)
- **Outreach:** Still respects Activity Window
- **Benefit:** Your leads are fully researched and scored when your Activity Window opens; you start sending immediately

Toggle this in **Account Settings** > **24/7 Pipeline Mode**.

---

## Daily Send Limits

Daily limits prevent your accounts from being flagged for suspicious behavior. All limits reset at the start of your Activity Window each day.

### DM Limits

Set a **Daily DM Limit** per sequence (e.g., 20, 30, 50 DMs/day):

- **Effect:** If you exceed the limit, excess DMs are queued for the next day
- **Default:** 20-30/day (depends on account age and history)
- **Why:** Platforms flag accounts sending 100+ DMs in a few hours as spam

Configure in **Sequence Settings** > **Daily Limits**.

### Action Limits

Set a **Combined Daily Action Limit** (all actions combined):

- **Example:** 50 total actions/day = 20 DMs + 15 Likes + 10 Follows + 5 Replies
- **Platform-specific limits:** Optionally set separate limits for X and LinkedIn
- **Effect:** Excess actions are queued for the next day

### Weekly Connection Limits (LinkedIn)

LinkedIn enforces hard weekly connection request limits:

| Account Type    | Weekly Limit       |
| --------------- | ------------------ |
| Free            | 100 requests/week  |
| Premium         | 150 requests/week  |
| Sales Navigator | 200 requests/week  |

- **Reset:** Every Monday at 12:01am PT
- **Effect:** Connection requests exceeding the limit go into **Deferred** state and auto-resume the following Monday
- **Lead status:** Leads stay in the sequence; they're not removed

### Example: Limit Configuration

You have 3 sequences running simultaneously:

| Sequence                   | Daily DM Limit | Daily Action Limit |
| -------------------------- | -------------- | ------------------ |
| Sequence A (Tech CTOs)     | 20             | 30                 |
| Sequence B (VP Sales)      | 15             | 25                 |
| Sequence C (Founders)      | 15             | 25                 |
| **Total**                  | **50**         | **80**             |

On a given day:

- Combined DM limit: 50/day across all sequences
- Combined action limit: 80/day across all sequences
- If Sequence A sends 20 DMs by 2pm, remaining sequences have 30 DMs left for the day

---

## Anti-Burst Protection

When you **resume a paused sequence** or restart a stopped sequence, AutoReach automatically spaces out re-activated actions gradually to avoid sudden spikes.

### Example

Your "Tech CTOs" sequence was paused for 3 days with 500 pending DMs.

- **Without anti-burst:** All 500 DMs would fire in the first hour, causing the platform to flag your account as spam
- **With anti-burst:** DMs are spread out gradually throughout the day, which looks natural

This protection activates automatically; you don't need to configure it.

{% hint style="warning" %}
Even with anti-burst protection, resuming a large paused sequence requires caution. Consider manually adjusting the daily limit down for a few days while the backlog clears.
{% endhint %}

---

## Deferred State

When a LinkedIn connection request hits the weekly limit, it enters **Deferred** state:

### What Happens

1. Action attempts to execute
2. LinkedIn says "You've hit your connection request limit this week"
3. AutoReach moves the action to **Deferred** state
4. The lead stays in the sequence
5. The action is automatically **retried the following Monday** when limits reset

### Lead Status

- Lead remains **Active** in the sequence
- Other actions continue normally (DMs, Likes, etc. still execute)
- Only the deferred connection request waits until Monday

### Example Timeline

**Wednesday:**

- You have 5 pending connection requests on a Free LinkedIn account
- You've already sent 100 requests this week
- 3 requests execute successfully; 2 hit the limit and go to **Deferred**

**Monday (next week):**

- Weekly limits reset
- The 2 deferred requests auto-execute
- No action needed from you

---

## Max AI Responses Per Conversation

Limit how many times AI auto-replies in a single conversation:

- **Default:** 0 (AI disabled; you manually respond)
- **Common setting:** 2-3 (AI handles initial replies, you take over)
- **Maximum:** 10

Configure in **Sequence Settings** > **AI & Responses**.

**Example:** If set to 2:

1. Lead replies to your DM > AI auto-replies (count: 1)
2. Lead replies again > AI auto-replies (count: 2)
3. Lead replies a third time > **AI does not reply; your account goes silent**
   - (You can then manually jump in or let the conversation drop)

{% hint style="info" %}
For warm leads or high-value prospects, set this to 0 and handle replies manually. For cold outreach funnels, 2-3 auto-replies is common.
{% endhint %}

---

## Stale Action Cleanup

AutoReach automatically skips actions that are significantly outdated:

- **Reason:** A pending DM from several days ago feels out of context
- **Effect:** The action is marked **Skipped**; the lead moves to the next step
- **Benefit:** Prevents awkward delayed messages that confuse leads

---

## Scheduling Examples

### Example 1: Soft Engagement Sequence (Cold Outreach)

```
Day 1 (Monday 9am): [Like Post] - executes at 9:05am
Day 2 (Tuesday 9am): [Follow] - executes at 9:07am
Day 3 (Wednesday 9am): [Wait 2 Days]
Day 5 (Friday 9am): [Send DM] - executes at 9:12am
```

- All actions execute during Activity Window (9am-9pm)
- Daily limit: 50 actions/day (plenty of buffer)
- Lead receives 3 gentle touchpoints over 5 days

### Example 2: High-Volume Outreach with Rate Limiting

```
Sequence A: 20 DMs/day limit, 30 actions/day limit
Sequence B: 20 DMs/day limit, 30 actions/day limit
Sequence C: 10 DMs/day limit, 20 actions/day limit
```

- Total daily: 50 DMs, 80 actions
- If all 3 sequences queue DMs early in the day:
  - Sequence A sends 20 DMs (9am-11am)
  - Sequence B sends 20 DMs (11am-1pm)
  - Sequence C sends 10 DMs (1pm-3pm)
  - Remaining 30 DMs queued for next day

### Example 3: Resume After Pause (Anti-Burst)

```
Sequence paused with 1000 pending actions (Friday 5pm)
Resumed on Monday 9am

Monday 9am-12pm:
  - Actions are spread out gradually (anti-burst)
  - ~50 actions execute (spread across 3 hours)
  - Remaining actions queue for next day
```

- Without anti-burst: All 1000 would fire in first hour, triggering a spam flag
- With anti-burst: Actions are spread naturally throughout the day

---

## Best Practices

1. **Set Activity Window to your actual work hours** - Keeps messaging patterns realistic
2. **Leave buffer in daily limits** - If limit is 50, aim for 30-40 daily. Avoid hitting limits daily.
3. **Stagger sequence starts** - Don't launch 5 sequences on the same day; space them out
4. **Monitor limits on LinkedIn** - Weekly connection limits fill up fast; track weekly progress
5. **Resume paused sequences carefully** - If 1000+ pending actions, lower daily limit temporarily
6. **Test with small batches first** - Launch with 50 leads before scaling to 1000
7. **Respect weekends** - Consider disabling sequences Friday afternoon if you want human-like behavior

---

## Troubleshooting

### "Actions are getting queued, not executing"

**Cause:** Daily limit is too low or Activity Window has passed.

**Solution:**

- Check Activity Window is currently active (what time is it vs. your window?)
- Increase daily limit in Sequence Settings
- Verify account isn't rate-limited by platform

### "Connection requests went into Deferred state"

**Cause:** Hit LinkedIn's weekly connection limit.

**Solution:**

- Check how many requests you've sent this week
- Wait until next Monday for automatic retry
- Or lower your connection request frequency in future sequences

### "Messages are being sent too fast/slow"

**Cause:** Activity Window or delay timing issue.

**Solution:**

- Verify Activity Window is set correctly
- Check sequence step delays (should be 1-3 days apart)
- Review daily limits (too high = no spacing between actions)

---

## Next Steps

- Configure [Activity Window](../getting-started/quickstart.md) in Account Settings
- Learn [Building Sequences](building-sequences.md) to apply daily limits per sequence
- Explore [Supported Actions](supported-actions.md) to understand action-specific limits
