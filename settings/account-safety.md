# Account Safety & Anti-Detection

AutoReach protects your accounts using browser identity management, rate limiting, health monitoring, and human behavior simulation.

## Account Health Monitoring

AutoReach continuously monitors account health and classifies errors into actionable categories.

### Error Types

| Error Type | Cooldown | Auto-Recoverable |
|---|---|---|
| Rate Limit | 24 hours | Yes |
| Authentication Error | 48 hours | Yes |
| Proxy Error | 24 hours | Yes |
| IP Blocked | 24 hours | No |
| Bot Detection | 7 days | No |
| Captcha Challenge | Manual intervention | No |
| Timeout | 2 hours | Yes |
| AI Provider Error | Manual | No (never pauses social account) |
| Duplicate Action | None | Skip |
| No Content Available | None | Skip |
| Daily Budget Exhausted | None | Skip |
| Unknown Error | 6 hours | Yes |

Errors are automatically classified based on the error response from each platform.

### Email Notifications

Not all errors trigger email alerts:
- Auto-recoverable types (Rate Limit, Timeout, Unknown Error) never send emails
- Proxy Error and IP Blocked only email after the 3rd occurrence within 24 hours

### Cascade Pause

When a pause-triggering error occurs, all associated resources are paused:

- Account warmup engagements, tweets, and strategies
- Sequences using the account
- Target users (X only) and link extractions

After a cascade pause, manual resume is required.

## Emergency Pause

AutoReach automatically pauses an account when it detects severe issues (bot detection, IP blocks, captcha challenges). When emergency pause activates:

1. All pending actions are cancelled
2. Account shows paused status
3. You receive a notification
4. Manual resume required

## Browser Identity Management

Each connected account is assigned a consistent browser identity that persists over time. This includes user agent rotation and platform-appropriate headers, making activity indistinguishable from normal browser use.

## Human Behavior Simulation

All actions include realistic timing:
- Randomized delays between interactions
- Session pattern variation
- Natural pacing that mimics real human browsing
- Time-of-day and day-of-week multipliers

## Negative Content Screening

Before engaging with a lead's post, content is checked for sensitive topics:

**Skipped topics**: Death, obituaries, serious illness, disasters, violence, self-harm

**Allowed topics**: Work frustrations, business failures, layoffs, industry criticism, competitive pressure

If the content check fails, the action proceeds rather than blocking.

## Best Practices

1. **Use dedicated proxies** — one proxy per account minimum
2. **Keep limits conservative** — especially on new accounts
3. **Monitor the Accounts page** — check error rates regularly
4. **Warm up new accounts** — use the Engagement Engine before launching outreach
5. **Pause proactively** — if you notice unusual behavior, pause before AutoReach triggers an emergency pause

## Next Steps

- **[Multi-Account Management](multi-account.md)**: Manage accounts, proxies, and limits
- **[Engagement Engine](../engagement-engine/overview.md)**: Warm up accounts safely
