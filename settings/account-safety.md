# Account Safety & Anti-Detection

AutoReach is built to protect your accounts while automating outreach. It uses a range of techniques to mimic real user behavior across X and LinkedIn.

## Browser Identity Management

AutoReach maintains realistic browser identities for each connected account. Each account is assigned a consistent identity that persists over time and matches expected browser characteristics, helping your activity look indistinguishable from normal use.

## Rate Limiting & Request Management

### X

X has rate limits on DMs and actions. AutoReach respects these by:

- **Daily Caps** - configurable limits per account
- **Exponential Backoff** - automatic retry with increasing delays on failures
- **Activity Windows** - actions scheduled during configured hours (default 9am-6pm)

### LinkedIn

AutoReach manages request rates to stay within safe limits for LinkedIn. This includes controlling how many operations run at one time, smoothing out request frequency, and enforcing daily caps to prevent over-activity.

## Emergency Pause

AutoReach automatically detects platform warnings and pauses automation in response. When an emergency pause activates:

1. All pending actions are canceled
2. The account shows "Safety Pause" status
3. You receive a notification
4. Manual resume is required before automation restarts

## Human Behavior Simulation

AutoReach simulates human-like behavior between actions. This includes realistic timing between interactions, variation in session patterns, and natural pacing that matches how a real person would move through the platform.

{% hint style="tip" %}
These delays genuinely protect your account. They slow down automation slightly, but significantly reduce suspension risk. The impact on campaign performance is usually minimal.
{% endhint %}

## Account Health Monitoring

AutoReach continuously monitors account health and takes appropriate action automatically. It watches for:

- **Rate limits** - reduces activity and waits before resuming
- **Authentication issues** - flags the account for re-authentication
- **Platform warnings** - triggers an emergency pause for manual review
- **Connectivity issues** - retries automatically before escalating

Severe issues (such as bot detection or IP blocks) trigger an automatic emergency pause and require manual review before automation resumes.

## Negative Content Screening

AutoReach skips leads posting about certain topics to protect account reputation:

### Skipped Topics
- Death and obituaries
- Serious illness or injury
- Disasters and emergencies
- Graphic violence or injury
- Self-harm

### Allowed (Usually Safe)
- Work frustrations and complaints
- Business failures and layoffs
- Industry criticism or problems
- Competitive pressure

{% hint style="info" %}
Engaging with people posting about death, illness, or disasters damages account trust. Engaging with people complaining about work or layoffs is acceptable and normal professional networking.
{% endhint %}

## Browser Extension Security

AutoReach's Chrome extension provides:

- **Secure Cookie Storage** - session credentials are encrypted and never sent to AutoReach servers
- **Local-Only Operation** - session management happens on your machine
- **No Password Storage** - you input credentials once per session

## Best Practices for Account Safety

1. **Use Dedicated Proxies** - one proxy per account minimum
2. **Spread Activity** - use multiple accounts if running high-volume outreach
3. **Respect Daily Limits** - keep limits conservative, especially on new accounts
4. **Monitor Health** - check the Accounts dashboard regularly
5. **Warm Up New Accounts** - use the Engagement Engine and respect the ramp-up period on LinkedIn before launching outreach
6. **Pause Proactively** - if you notice unusual account behavior, pause before AutoReach triggers an emergency pause
7. **Refresh Proxies Periodically** - replace proxies if you notice degraded performance or increased errors

{% hint style="warning" %}
No anti-detection technique is 100% foolproof. Platform detection systems are constantly evolving. AutoReach's safety measures significantly reduce risk, but automation always carries some suspension risk.
{% endhint %}

## Next Steps

- **[Multi-Account Management](multi-account.md)**: Manage multiple accounts and spread activity across them
- **[Engagement Engine Overview](../engagement-engine/overview.md)**: Warm up accounts safely before launching outreach
