# Auto-Enrollment

Auto-Enrollment is the bridge between lead scoring and outreach sequences. It automatically moves leads from "scored" to "active outreach" without any manual intervention.

{% hint style="warning" %}
**When Autopilot is active**, auto-enroll is turned ON by default. This means all ready buyers are automatically added to sequences and will **not** appear on the Buyers page. The Buyers page only shows buyers before they are added to a sequence. If you want to review buyers before they are enrolled, you can disable auto-enroll in your settings.
{% endhint %}

## How Auto-Enrollment Works

**Every 5 minutes**, Autopilot runs its enrollment check:

1. Queries all leads with `buyer_score >= 60` in your Offer
2. Identifies leads that aren't already enrolled in a sequence
3. Selects the appropriate sequence (X/Twitter or LinkedIn) based on the lead's platform
4. Enrolls them with their next action scheduled
5. Respects your daily send limits to avoid over-sending

The whole process is automatic and instantaneous.

## Buyer Score Threshold

Only leads with **buyer_score >= 60** are enrolled. This threshold represents "active" buyer intent:

| Tier                   | Score Range | Action                              |
| ---------------------- | ----------- | ----------------------------------- |
| Monitor resurfacing    | 0-29        | Check again in 21 days              |
| Monitoring tier        | 30-39       | Check again in 14 days              |
| Monitoring tier        | 40-49       | Check again in 10 days              |
| Warm tier              | 50-59       | Not yet enrolled, check in 5 days   |
| **Active tier**        | **60+**     | **Auto-enroll immediately**         |

{% hint style="info" %}
**What creates a high score?** Buying signals like recent headline changes, posting about your space, following competitors, and matching your ICP criteria all boost the score.
{% endhint %}

## Platform-Specific Enrollment

Auto-Enrollment automatically picks the right sequence:

- **X/Twitter leads** are enrolled into your X sequence
- **LinkedIn leads** are enrolled into your LinkedIn sequence

This ensures the messaging, timing, and engagement match the platform behavior.

## Daily Send Limits

Auto-Enrollment respects your configured limits:

- If you've hit today's X limit (e.g., 40 messages/day), X leads queue for tomorrow
- If you've hit today's LinkedIn limit (e.g., 20 messages/day), LinkedIn leads queue for tomorrow
- This prevents over-sending and maintains platform health

Your Activity Window and daily limits are always honored.

{% hint style="warning" %}
**Limits protect your account.** Staying under platform rate limits reduces the risk of shadowbanning and keeps your account in good standing.
{% endhint %}

## Avoiding Double-Enrollment

Autopilot automatically skips:

- Leads already in an active sequence
- Leads in paused sequences
- Leads who have completed a sequence
- Leads who have replied and moved to manual review

Each lead is enrolled only once per sequence lifecycle.

## Activity Window

Auto-Enrollment happens within your configured **Activity Window**:

- If you've set your Activity Window to 9 AM-6 PM, enrollment starts then
- This prevents messages from being sent at odd hours
- First actions are scheduled relative to your timezone

{% hint style="success" %}
**Enrollment respects your schedule.** You choose when Autopilot operates, and it sticks to it.
{% endhint %}

## Viewing Enrolled Leads

See all auto-enrolled leads:

1. Go to **Sequences**
2. Click the sequence (X or LinkedIn)
3. View the **Leads** tab to see:
   - Lead name and profile
   - Enrollment date
   - Current step in the sequence
   - Next scheduled action

You can pause, remove, or manually adjust any lead's progress.

## What Triggers Re-Enrollment?

Once a lead completes a sequence, they won't be re-enrolled automatically. However:

- If a lead's score drops below 60 and later rises back to 60+, they can be re-enrolled in a different sequence
- Manually unenrolling a lead resets them for future auto-enrollment

## Enrollment Notifications

When leads auto-enroll, you'll see:

- Activity log entry with the lead name and sequence
- Dashboard update showing new active leads
- Message preview of their first outreach message

This gives you visibility into what Autopilot is doing without requiring approval for each lead.

## Common Questions

**Q: Can I prevent a specific lead from being auto-enrolled?**
A: Yes. Pause or remove them from the enrollment system, or adjust their score by marking them as "not a fit."

**Q: What if I hit my daily limit mid-day?**
A: Remaining leads queue for tomorrow and enroll first thing.

**Q: Can I manually enroll leads outside of Autopilot?**
A: Yes. You can manually add leads to sequences anytime, and Autopilot won't double-enroll them.

**Q: How long does a lead stay enrolled?**
A: It depends on your sequence length. Typical sequences run 7-21 days. After completion, the lead moves to your completed/archived list.

---

Auto-Enrollment is the heart of your automation. It's the reason you can run full B2B outreach without manually picking which leads to reach.

## Next Steps

- **[Buyer Expansion](buyer-expansion.md)**: See how Autopilot discovers new prospects to fill your pipeline
- **[Buyer States](../core-concepts/buyer-states.md)**: Understand the score thresholds that drive enrollment decisions
