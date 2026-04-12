# Multi-Account Management

Manage multiple X/Twitter and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own activity tracking, limits, and health status.

## Accessing Your Accounts

Go to **Settings > Accounts** to see all connected accounts. Each account displays as a card showing platform, username, current status, and key metrics.

## Account Status

Each account shows one of these statuses:

- **Active** - account is operating normally
- **Paused** - account is paused and will not take actions
- **Expired** - authentication has expired (re-connect required)
- **Suspended** - account has been flagged for review or violates platform rules

## Twitter/X Accounts

### Authentication
Twitter accounts use cookie-based authentication. AutoReach stores your session cookies securely and refreshes them automatically.

### Daily Limits
Configure how many actions your account can take per day:

- **Daily DM Limit** - default 20 DMs/day (configurable per account)
- **Daily Action Window** - time frame when actions are scheduled (e.g., 9am-6pm)
- **Automatic Daily Reset** - count resets at 00:00 UTC

{% hint style="info" %}
Twitter has soft rate limits on DMs. Starting with 20/day and increasing slowly (5-10/day per week) helps avoid detection. Aggressive limits often trigger temporary blocks.
{% endhint %}

### Proxy Configuration
Each Twitter account can route traffic through a dedicated proxy:

- **Proxy Type** - HTTP or SOCKS5
- **Host, Port, Username, Password** - your proxy credentials
- **Per-Account Routing** - each account uses its own proxy independently

### User-Agent Persistence
AutoReach rotates your account's user-agent string every 14-30 days:

- Maintains 40+ diverse user agent signatures (Chrome, Firefox, Safari, Edge)
- Per-account consistency between rotations (same device fingerprint)
- Auto-rotation timing is randomized per account to avoid patterns

### Trust Score
A proprietary metric (0-100) indicating platform trust:

- **90-100** - new accounts or excellent standing
- **70-89** - normal operating range
- **50-69** - minor rate limits detected
- **< 50** - account showing suspicious activity; consider pausing

### Health Tracking
24-hour rolling error window shows:

- **Rate Limits Triggered** - soft blocks (usually 15-60 min)
- **Bot Detection Flags** - unusual pattern warnings
- **Connection Errors** - network or auth issues
- **Action Abandonment Rate** - percentage of scheduled actions that failed

## LinkedIn Accounts

### Authentication
LinkedIn accounts require two credentials:

- **Cookies** - your session cookies (refreshed automatically)
- **li_at Token** - critical authentication token for API operations
- **Secure Storage** - both stored encrypted and never shared

### Connection Limits
LinkedIn imposes connection request limits. Configure based on your account type:

- **Free/Premium Account** - 100 connections/week default
- **Sales Navigator Account** - 200 connections/week default
- **Per-Account Tracking** - counts reset every Sunday at 00:00 UTC

{% hint style="warning" %}
LinkedIn actively monitors for bot behavior. Connecting faster than 20-30/day significantly increases suspension risk. AutoReach paces actions conservatively by default.
{% endhint %}

### Proxy Configuration
LinkedIn account security requires a dedicated proxy:

- **HTTP or SOCKS5** - choose your proxy protocol
- **Host, Port, Username, Password** - your proxy details
- **Required** - LinkedIn accounts must always have a proxy configured

### Engagement Phase Tracking
New LinkedIn accounts go through an engagement ramp-up phase:

- **Week 1** - limited actions, profile views, and light engagement
- **Week 2-3** - gradual increase in activity levels
- **Week 4+** - full capacity operations

AutoReach shows engagement phase progress on each LinkedIn account card. Do not rush this process. Accounts that respect the ramp-up pattern have 3-5x lower suspension rates.

### Connection Limit Detection
AutoReach monitors your weekly usage:

- **Soft Limit (80%)** - warning issued, slightly slower pacing applied
- **Hard Limit (100%)** - no more connections this week
- **Auto-Recovery** - limit resets automatically on Sunday

## Account Health Dashboard

Each account card displays:

- **Last Activity** - when the account last took an action
- **Daily Action Count** - actions taken today (resets at midnight)
- **Scheduled Actions** - number of actions waiting in queue
- **Error Rate** - percentage of actions that failed in last 24h

### Engagement Engine Status (LinkedIn only)
Shows engagement phase progress and daily engagement activity:

- **Engagement Week** - current phase (Week 1, 2, 3, or Complete)
- **Daily Activity Chart** - last 7 days of engagement actions
- **Inbound Engagement** - replies and connection acceptances tracked

## Pause or Resume an Account

**Pause:** Click the pause button on any account card. All pending actions are canceled and no new actions are scheduled.

**Resume:** Click resume. The account reconnects and resumes normal operations. Automation continues from where it left off.

## Remove an Account

Click the "Remove" option on an account card. This:

- Disconnects AutoReach from that account
- Cancels all pending actions for that account
- Does not modify the actual Twitter/LinkedIn account

## Activity Window Configuration

Set times when your accounts should be most active:

- **Default Window** - 9am-6pm (your local timezone)
- **Actions Outside Window** - still execute, but at randomized lower frequency
- **Time Zone** - configured per account or globally in settings

{% hint style="tip" %}
Set your activity window to match when you or your team are typically online. This creates more natural-looking patterns and helps avoid detection systems.
{% endhint %}

## Monitoring Account Health

Check the **Accounts** page regularly:

- **Trust Score < 70?** Reduce daily limits or pause for 24h
- **Error Rate > 10%?** Check your proxy, auth tokens, or reach out to support
- **Multiple Suspensions?** Consider adding more accounts to spread activity load

AutoReach automatically pauses accounts showing severe health issues (like IP blocks), but lighter issues (rate limits, bot detection) are surfaced as warnings for you to decide.
