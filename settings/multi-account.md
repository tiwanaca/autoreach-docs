# Multi-Account Management

Manage multiple X/Twitter and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own activity tracking, limits, and health status.

## Accessing Your Accounts

Go to **Settings > Accounts** to see all connected accounts. Each account displays as a card showing platform, username, current status, and key metrics.

## Account Status

Each account shows one of these statuses:

- **Active** — Account is operating normally
- **Paused** — Account is paused and won't take actions
- **Expired** — Authentication has expired (re-connect required)
- **Suspended** — Account has been flagged for review or violates platform rules

## Twitter/X Accounts

### Authentication
Twitter accounts use cookie-based authentication. AutoReach stores your session cookies securely and refreshes them automatically.

### Daily Limits
Configure how many actions your account can take per day:

- **Daily DM Limit** — Default 20 DMs/day (configurable per account)
- **Daily Action Window** — Time frame when actions are scheduled (e.g., 9am-6pm)
- **Automatic Daily Reset** — Count resets at 00:00 UTC

{% hint style="info" %}
Twitter has soft rate limits on DMs. Starting with 20/day and increasing slowly (5-10/day per week) helps avoid detection. Aggressive limits often trigger temporary blocks.
{% endhint %}

### Proxy Configuration
Each Twitter account can route traffic through a dedicated proxy:

- **Proxy Type** — HTTP or SOCKS5
- **Host, Port, Username, Password** — Your proxy credentials
- **Per-Account Routing** — Each account uses its own proxy independently

### User-Agent Persistence
AutoReach rotates your account's user-agent string every 14-30 days:

- Maintains 40+ diverse user agent signatures (Chrome, Firefox, Safari, Edge)
- Per-account consistency between rotations (same device fingerprint)
- Auto-rotation timing is randomized per account to avoid patterns

### Trust Score
A proprietary metric (0-100) indicating platform trust:

- **90-100** — New accounts or excellent standing
- **70-89** — Normal operating range
- **50-69** — Minor rate limits detected
- **< 50** — Account showing suspicious activity; consider pausing

### Health Tracking
24-hour rolling error window shows:

- **Rate Limits Triggered** — Soft blocks (usually 15-60 min)
- **Bot Detection Flags** — Unusual pattern warnings
- **Connection Errors** — Network or auth issues
- **Action Abandonment Rate** — % of scheduled actions that failed

## LinkedIn Accounts

### Authentication
LinkedIn accounts require two credentials:

- **Cookies** — Your session cookies (refreshed automatically)
- **li_at Token** — Critical authentication token for API operations
- **Secure Storage** — Both stored encrypted and never shared

### Connection Limits
LinkedIn imposes connection request limits. Configure based on your account type:

- **Free/Premium Account** — 100 connections/week default
- **Sales Navigator Account** — 200 connections/week default
- **Per-Account Tracking** — Counts reset every Sunday at 00:00 UTC

{% hint style="warning" %}
LinkedIn actively monitors for bot behavior. Connecting faster than 20-30/day significantly increases suspension risk. AutoReach paces actions conservatively by default.
{% endhint %}

### Proxy Configuration
LinkedIn account security requires a dedicated proxy:

- **HTTP or SOCKS5** — Choose your proxy protocol
- **Host, Port, Username, Password** — Your proxy details
- **Required** — LinkedIn accounts must always have a proxy configured

### Warmup Phase Tracking
New LinkedIn accounts go through a warmup phase:

- **Week 1** — Limited actions, profile views, and light engagement
- **Week 2-3** — Gradual increase in activity levels
- **Week 4+** — Full capacity operations

AutoReach shows warmup progress on each LinkedIn account card. Don't rush this—accounts that respect the warmup pattern have 3-5x lower suspension rates.

### Connection Limit Detection
AutoReach monitors your weekly usage:

- **Soft Limit (80%)** — Warning issued, slightly slower pacing applied
- **Hard Limit (100%)** — No more connections this week
- **Auto-Recovery** — Limit resets automatically on Sunday

## Account Health Dashboard

Each account card displays:

- **Last Activity** — When the account last took an action
- **Daily Action Count** — Actions taken today (resets at midnight)
- **Scheduled Actions** — Number of actions waiting in queue
- **Error Rate** — % of actions that failed in last 24h

### Engagement Engine Status (LinkedIn only)
Shows warmup progress and daily engagement activity:

- **Warmup Week** — Current phase (Week 1, 2, 3, or Complete)
- **Daily Activity Chart** — Last 7 days of engagement actions
- **Inbound Engagement** — Replies and connection acceptances tracked

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

- **Default Window** — 9am-6pm (your local timezone)
- **Actions Outside Window** — Still execute, but randomized lower frequency
- **Time Zone** — Configured per account or globally in settings

{% hint style="tip" %}
Set your activity window to match when you or your team are typically online. This creates more natural-looking patterns and helps avoid detection systems.
{% endhint %}

## Monitoring Account Health

Check the **Accounts** page regularly:

- **Trust Score < 70?** → Reduce daily limits or pause for 24h
- **Error Rate > 10%?** → Check your proxy, auth tokens, or reach out to support
- **Multiple Suspensions?** → Consider adding more accounts to spread activity load

AutoReach automatically pauses accounts showing severe health issues (like IP blocks), but lighter issues (rate limits, bot detection) are surfaced as warnings for you to decide.
