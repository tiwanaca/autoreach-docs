# Multi-Account Management

Manage multiple X and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own activity tracking, limits, and health status.

## Accessing Your Accounts

Go to **Settings > Accounts** to see all connected accounts. Each account displays as a card showing platform, username, current status, and key metrics.

## Account Status

Each account shows one of these statuses:

- **Active** - account is operating normally
- **Paused** - account is paused and will not take actions
- **Expired** - authentication has expired (re-connect required)
- **Suspended** - account has been flagged for review or violates platform rules

## X Accounts

### Authentication
X accounts connect securely through the AutoReach Chrome Extension, which handles authentication automatically.

### Daily Limits
Configure how many actions your account can take per day:

- **Daily DM Limit** - default 20 DMs/day (configurable per account)
- **Daily Action Window** - time frame when actions are scheduled (e.g., 9am-6pm)
- **Automatic Daily Reset** - count resets at 00:00 UTC

{% hint style="info" %}
Starting with 20 DMs/day and increasing gradually over time helps maintain good account health. Aggressive limits can trigger temporary blocks.
{% endhint %}

### Proxy Configuration
Each X account can route traffic through a dedicated proxy. Using dedicated proxies is recommended for best results.

### Account Health
AutoReach monitors the health of each X account and surfaces warnings when issues are detected. Check the Accounts page regularly and reduce daily limits or pause an account if you notice elevated error rates.

## LinkedIn Accounts

### Authentication
LinkedIn accounts connect securely through the AutoReach Chrome Extension, which handles authentication automatically.

### Connection Limits
LinkedIn imposes weekly connection request limits. AutoReach tracks your usage based on your account type:

- **Free Account** - 100 connections/week
- **Premium Account** - 150 connections/week
- **Sales Navigator Account** - 200 connections/week
- **Per-Account Tracking** - counts reset every Sunday at 00:00 UTC

{% hint style="warning" %}
LinkedIn actively monitors for bot behavior. AutoReach paces actions conservatively by default to protect your account.
{% endhint %}

### Proxy Configuration
A dedicated proxy is strongly recommended for LinkedIn accounts. Using a proxy helps protect your account and keeps your activity consistent.

### Engagement Phase Tracking
New LinkedIn accounts go through a gradual ramp-up phase before reaching full capacity. AutoReach tracks this automatically and shows progress on each account card. Allow the ramp-up to complete naturally for the best long-term account health.

### Connection Limit Monitoring
AutoReach monitors your weekly connection usage and automatically slows down activity as you approach your limit. Limits reset automatically each Sunday.

## Account Health Dashboard

Each account card displays:

- **Last Activity** - when the account last took an action
- **Daily Action Count** - actions taken today (resets at midnight)
- **Scheduled Actions** - number of actions waiting in queue
- **Error Rate** - percentage of actions that failed in last 24h

### Engagement Engine Status (LinkedIn only)
Shows engagement phase progress and daily engagement activity:

- **Engagement Phase** - current ramp-up progress
- **Daily Activity Chart** - last 7 days of engagement actions
- **Inbound Engagement** - replies and connection acceptances tracked

## Pause or Resume an Account

**Pause:** Click the pause button on any account card. All pending actions are canceled and no new actions are scheduled.

**Resume:** Click resume. The account reconnects and resumes normal operations. Automation continues from where it left off.

## Remove an Account

Click the "Remove" option on an account card. This:

- Disconnects AutoReach from that account
- Cancels all pending actions for that account
- Does not modify the actual X or LinkedIn account

## Activity Window Configuration

Set times when your accounts should be most active:

- **Default Window** - 9am-6pm (your local timezone)
- **Actions Outside Window** - still execute, but at randomized lower frequency
- **Time Zone** - configured per account or globally in settings

{% hint style="tip" %}
Set your activity window to match when you or your team are typically online. This creates more natural-looking patterns and improves account health.
{% endhint %}

## Monitoring Account Health

Check the **Accounts** page regularly:

- **High Error Rate?** Check your proxy configuration, re-authenticate via the Chrome Extension, or reach out to support
- **Multiple Suspensions?** Consider adding more accounts to spread activity load

AutoReach automatically pauses accounts showing severe health issues such as IP blocks. Lighter issues are surfaced as warnings for you to review and act on.

## Next Steps

- **[Account Safety & Anti-Detection](account-safety.md)**: Learn how AutoReach protects your accounts from detection
- **[Connecting LinkedIn](../getting-started/connect-linkedin.md)**: Add a new LinkedIn account to your workspace
