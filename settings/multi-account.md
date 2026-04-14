# Multi-Account Management

Manage multiple X and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own proxy, limits, and health status.

## Account Status

Each account shows one of these statuses:

| Status | Description |
|---|---|
| Active | Operating normally |
| Paused | Paused-  no actions scheduled |
| Suspended | Suspended due to safety issue-  review required |
| Expired | Authentication expired-  re-connect required |

## X Accounts

### Authentication

X accounts connect through the AutoReach Chrome Extension, which links your active browser session to AutoReach.

### Configuration

- **Daily action limits**-  configurable per account
- **Activity window**-  time frame when actions execute (default 9:00–21:00)
- **Proxy**-  dedicated proxy per account (recommended)

## LinkedIn Accounts

### Authentication

LinkedIn accounts connect through the Chrome Extension, same as X.

### Connection Limits

LinkedIn connection requests have a weekly limit tracked per-account. Set the weekly connection limit on each LinkedIn account to match your account type (Free, Premium, or Sales Navigator). See [Supported Actions](../outreach/supported-actions.md#connection-request) for the full limits table and deferral behavior.

### Proxy Configuration

Each LinkedIn account stores its own proxy configuration (host, port, credentials, and type). If no proxy is configured, a fallback proxy is used.

Using dedicated proxies is strongly recommended for LinkedIn accounts.

## Pausing and Resuming

**Pause**: All pending actions are cancelled and no new actions are scheduled. Associated warmup strategies and sequences are automatically paused.

**Resume**: Account reconnects and operations resume. Previously paused warmup strategies and sequences are reactivated.

## Account Health

Each account card displays:

- Last activity timestamp
- Current health or error status

Check the Accounts page regularly. Error indicators may signal proxy issues or authentication expiration.

## Next Steps

- **[Account Safety](account-safety.md)**: Error handling, cooldowns, and cascade pause behavior
- **[Blacklisting](blacklisting.md)**: Exclude specific accounts from outreach
