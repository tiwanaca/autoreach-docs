# Account Safety

AutoReach protects your accounts using browser identity management, rate limiting, health monitoring, and human behavior simulation.

## How to Stay Safe (the short version)

Most account issues come from a small set of avoidable mistakes. Three rules cover the majority of them:

1. **Start with low daily limits and ramp slowly.** Begin at 15-20 actions per day per account, then increase gradually over weeks, not days. Sudden jumps to 50+ on a fresh account are the #1 cause of bot detection.
2. **Run the [Engagement Engine](../engagement-engine/overview.md) for 1-2 weeks before launching sequences on new or inactive accounts.** Outreach from a silent account looks suspicious to the platform.
3. **Don't run AutoReach and manual mass-actions at the same time.** If you're manually liking 50 posts while AutoReach is also active, the combined activity can trigger rate limits.

The rest of this page covers what AutoReach does automatically when something goes wrong, and what requires your intervention. **You don't need to read it preemptively** — come back when you see an error status on an account or get a notification email.

## Account Health Monitoring

AutoReach continuously monitors account health and classifies errors into actionable categories.

### Error Classification

AutoReach classifies errors into categories-  some are auto-recoverable (like rate limits and timeouts), while others require manual review (like bot detection or captcha challenges). Each category has an appropriate cooldown period before retrying.

Errors that are auto-recoverable resolve on their own after the cooldown (rate limits, timeouts, expired auth, proxy errors, IP blocks). Bot detection, captcha challenges, and AI-provider credit exhaustion are flagged as manual-fix-required - the account stays paused until you address the root cause and resume it from the Accounts page.

### Email Notifications

You receive email alerts for significant account issues. Transient errors (like occasional rate limits or timeouts) do not generate emails-  only persistent or serious problems trigger notifications.

### Cascade Pause

When a serious error occurs, AutoReach pauses not just the account but all associated activity-  warmup, sequences, and pending actions. This prevents further issues while you investigate. After a cascade pause, manual resume is required.

## Emergency Pause

AutoReach automatically pauses an account when it detects severe issues (bot detection, captcha challenges, IP blocks). When emergency pause activates:

1. All pending actions are cancelled
2. Account shows paused status
3. You receive a notification (for bot detection, captcha, and AI-provider credit issues - which require manual review)
4. **Manual resume** is required for bot detection, captcha, and AI-provider issues. **Auto-resume** happens for IP blocks, expired auth, and proxy errors once their cooldown expires

## Browser Identity Management

Each connected account is assigned a consistent browser identity that persists over time, making activity appear as normal browser use rather than automated traffic.

## Human Behavior Simulation

All actions include realistic timing and pacing designed to mirror normal human browsing patterns rather than automated scripts.

## Negative Content Screening

Before engaging with a lead's post, content is checked for sensitive topics:

**Skipped topics**: Death, obituaries, serious illness, disasters, violence, self-harm

**Allowed topics**: Work frustrations, business failures, layoffs, industry criticism, competitive pressure

If the content check fails, the action proceeds rather than blocking.

## Best Practices

1. **Use dedicated proxies**-  one proxy per account minimum
2. **Keep limits conservative**-  especially on new accounts
3. **Monitor the Accounts page**-  check error rates regularly
4. **Warm up new accounts**-  use the Engagement Engine before launching outreach
5. **Pause proactively**-  if you notice unusual behavior, pause before AutoReach triggers an emergency pause

## Next Steps

- **[Multi-Account Management](multi-account.md)**: Manage accounts, proxies, and limits
- **[Engagement Engine](../engagement-engine/overview.md)**: Warm up accounts safely
