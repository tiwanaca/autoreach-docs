# Multi-Account Management

Manage multiple X and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own proxy, limits, and health status.

## Account Status

Each account shows one of these statuses:

| Status | Description |
|---|---|
| Active | Operating normally |
| Paused | Paused — no actions scheduled |
| Expired | Authentication expired — re-connect required |

## X Accounts

### Authentication

X accounts connect through the AutoReach Chrome Extension, which extracts session cookies from your browser.

### Configuration

- **Daily action limits** — configurable per account
- **Activity window** — time frame when actions execute (default 9:00–21:00)
- **Proxy** — dedicated proxy per account (recommended)

## LinkedIn Accounts

### Authentication

LinkedIn accounts connect through the Chrome Extension, same as X.

### Connection Limits

LinkedIn connection requests have a **weekly limit** tracked per-account:

| Account Type | Default Weekly Limit |
|---|---|
| Free | 100 |
| Premium | 150 |
| Sales Navigator | 200 |

Set the weekly connection limit on each LinkedIn account to match your account type.

**Weekly reset**: Monday 00:00 UTC. The counter resets automatically at the start of each week.

When the weekly limit is reached, pending connection request actions are deferred to **next Monday** at a random time between 09:00–12:59 UTC.

### Proxy Configuration

Each LinkedIn account stores its own proxy configuration (host, port, credentials, and type). If no proxy is configured, a fallback proxy is used.

Using dedicated proxies is strongly recommended for LinkedIn accounts.

## Pausing and Resuming

**Pause**: All pending actions are cancelled and no new actions are scheduled. Associated warmup strategies and sequences are paused (marked `paused_by_account: true`).

**Resume**: Account reconnects and operations resume. Resources marked `paused_by_account` are reactivated.

## Account Health

Each account card displays:

- Last activity timestamp
- Daily action count (resets at midnight)
- Scheduled actions in queue
- Error rate (last 24 hours)

Check the Accounts page regularly. Elevated error rates may indicate proxy issues or authentication expiration.

## Next Steps

- **[Account Safety](account-safety.md)**: Error handling, cooldowns, and cascade pause behavior
- **[Blacklisting](blacklisting.md)**: Exclude specific accounts from outreach
