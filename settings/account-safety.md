# Account Safety

AutoReach protects your accounts using browser identity management, rate limiting, health monitoring, and human behavior simulation.

## Account Health Monitoring

AutoReach continuously monitors account health and classifies errors into actionable categories.

### Error Classification

AutoReach classifies errors into categories-  some are auto-recoverable (like rate limits and timeouts), while others require manual review (like bot detection or captcha challenges). Each category has an appropriate cooldown period before retrying.

Errors that are auto-recoverable resolve on their own after the cooldown. Serious issues like bot detection or IP blocks trigger an emergency pause and require you to manually resume the account after investigating.

### Email Notifications

You receive email alerts for significant account issues. Transient errors (like occasional rate limits or timeouts) do not generate emails-  only persistent or serious problems trigger notifications.

### Cascade Pause

When a serious error occurs, AutoReach pauses not just the account but all associated activity-  warmup, sequences, and pending actions. This prevents further issues while you investigate. After a cascade pause, manual resume is required.

## Emergency Pause

AutoReach automatically pauses an account when it detects severe issues (bot detection, IP blocks, captcha challenges). When emergency pause activates:

1. All pending actions are cancelled
2. Account shows paused status
3. You receive a notification
4. Manual resume required

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
