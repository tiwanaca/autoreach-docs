# Multi-Account Management

Manage multiple X and LinkedIn accounts from a single AutoReach dashboard. Each account operates independently with its own proxy, limits, and health status.

## Account Status

Each account shows one of these statuses:

| Status | Description |
|---|---|
| Active | Operating normally |
| Paused | Paused - no actions scheduled |
| Suspended | Suspended due to safety issue - review required |
| Expired | Authentication expired - re-connect required |

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

LinkedIn connection requests have a daily limit tracked per-account. You can set the daily connection limit on each LinkedIn account to any whole number from 1 to 100 (default 15, which is the recommended starting point). See [Supported Actions](../outreach/supported-actions.md#connection-request) for deferral behavior.

### Proxy Configuration

Each LinkedIn account stores its own proxy configuration (host, port, credentials, and type). If no proxy is configured, a fallback proxy is used.

Using dedicated proxies is strongly recommended for LinkedIn accounts.

### Antidetect Browsers

If you run AutoReach inside an antidetect browser (SunBrowser, GoLogin, Multilogin, Dolphin Anty, Incogniton, Kameleo, AdsPower, and similar tools), you must configure your proxy inside the antidetect browser itself, not through the AutoReach extension.

These browsers manage proxies at the browser launch layer and block extensions from calling Chrome's proxy API. If the extension tries to apply proxy settings, the browser kills the popup process before any error can be caught, which looks like the extension crashing or closing instantly.

How AutoReach handles this:

- The extension tries to auto-detect antidetect browsers from the user agent and skips proxy API calls when it matches
- Detection is best-effort. Most antidetect browsers spoof their user agent to look like vanilla Chrome, which is the whole point of using one, so auto-detection will often miss them on first launch
- Your proxy still works normally because the antidetect browser routes traffic through it at the network layer

What you need to do before opening the extension on an antidetect browser:

1. Configure the proxy inside your antidetect browser profile first (this is the default workflow for these tools)
2. Do not configure a separate proxy in the extension popup. Leave proxy settings empty or set to "browser-managed"
3. If the popup closes instantly the first time you open it, that is the proxy API being called before detection kicks in. Set `__skip_proxy_api` to `true` in the extension's `chrome.storage.local`, then reopen the popup

If you hit this crash, contact support with your browser name and version so we can add it to the detection keyword list and prevent it for other users.

## Pausing and Resuming

**Pause**: All pending actions are cancelled and no new actions are scheduled. Associated warmup strategies and sequences are automatically paused.

**Resume**: Account reconnects and operations resume. Previously paused warmup strategies and sequences are reactivated.

## Account Health

Each account card displays:

- Last activity timestamp
- Current health or error status

Check the Accounts page regularly. Error indicators may signal proxy issues or authentication expiration.

## Deleting Accounts

From an account's detail page, click **Delete Account** to permanently remove it. Deletion is irreversible and removes:

- The account connection
- All associated conversations, sequence enrollments, and warmup state for that account
- The dedicated proxy assigned to the account (if one was configured), which is also canceled

You will see a confirmation modal listing the consequences before the delete proceeds. Active campaigns using the account are affected.

**Base account protection**-  the primary account on your workspace cannot be deleted. If you need to remove it, contact support. A separate modal blocks the action and explains this.

## Next Steps

- **[Account Safety](account-safety.md)**: Error handling, cooldowns, and cascade pause behavior
- **[Blacklisting](blacklisting.md)**: Exclude specific accounts from outreach
