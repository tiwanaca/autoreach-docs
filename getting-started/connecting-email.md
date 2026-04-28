# Connecting Your Email Accounts

Connect Gmail and Outlook mailboxes to send cold emails, monitor replies, and keep email conversations in your unified Inbox alongside X and LinkedIn DMs.

You can connect one or both providers per workspace. AutoReach will route emails to the right mailbox based on the recipient's domain.

---

## Connecting Gmail

Gmail uses an **App Password** (not OAuth). This is faster to set up and works for both personal and Google Workspace accounts (subject to admin policy).

### Prerequisites

- Gmail or Google Workspace account
- 2-Step Verification enabled on the Google account
- IMAP enabled on the account

### Setup

1. **Enable 2-Step Verification** at [myaccount.google.com/security](https://myaccount.google.com/security)
2. **Generate an App Password**:
   - Visit [myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords)
   - Name it "AutoReach"
   - Copy the 16-character password
3. In AutoReach, go to **Accounts > Email** and click **Connect Gmail**
4. Enter your full Gmail address and the App Password
5. Click **Connect**

AutoReach validates SMTP and IMAP access before saving. If validation fails, the error will explain why (usually IMAP disabled, App Password rejected, or admin block on Workspace).

### Workspace (G Suite) Notes

Some Workspace admins block App Passwords or IMAP at the org level. If your admin has these locked down:

- Ask the admin to allow App Passwords for your account, **or**
- Ask the admin to enable IMAP for your account

Contact support if you need an alternative connection method.

---

## Connecting Outlook

Outlook uses Microsoft OAuth. AutoReach never sees your password.

### Setup

1. In AutoReach, go to **Accounts > Email** and click **Connect Outlook**
2. A popup opens to the Microsoft sign-in page
3. Sign in and grant the permissions AutoReach requests (read mail, send mail, manage profile)
4. The popup closes automatically once authorization succeeds

If your browser blocks the popup, allow popups for AutoReach and click **Connect Outlook** again. If the popup closes before the handshake completes, the connection list refreshes shortly after to detect any successful connection.

### Token Refresh

Outlook tokens are refreshed automatically in the background. If a token can no longer be refreshed (revoked permission, password changed, MFA reset), the account shows an **Expired** badge and you'll need to **Reconnect**.

---

## Managing Email Accounts

Open **Accounts > Email** to see all connected mailboxes. Each card shows:

- Email address and provider (Gmail / Outlook)
- Connection status (Active, Expired, Auth Failed, Revoked)
- Active / paused toggle (separate from connection status)
- Primary badge (when the account is the default for neutral domains)
- Last activity time

### Available Actions

| Action | Effect |
|---|---|
| **Pause** | Temporarily stops outbound sends from this mailbox without disconnecting |
| **Resume** | Re-enables sends |
| **Make Primary** | Sets this account as the default for recipients on neutral domains |
| **Reconnect** | Refresh credentials when a mailbox shows as expired |
| **Disconnect** | Permanently remove the mailbox; in-flight email actions on this mailbox stop |

### Multiple Mailboxes and Domain Routing

When you have **both Gmail and Outlook connected**, AutoReach picks which mailbox to send from based on the recipient's email domain:

- `@gmail.com` and `@googlemail.com` recipients use your Gmail account
- `@outlook.com`, `@hotmail.com`, `@live.com`, `@msn.com` (and regional variants) use your Outlook account
- For other domains, AutoReach also checks the domain's MX records to detect Google Workspace and Microsoft 365 hosting and routes accordingly
- Domains it cannot classify use your **Primary** mailbox

This makes outbound mail look more authentic and improves deliverability. Click **Make Primary** on any mailbox to change the default for unclassified domains.

---

## What Happens After Connecting

Once a mailbox is connected:

- **Email steps in your sequences become available** when you build or edit a sequence
- **AutoReach starts polling for replies** in the background
- **Bounce detection** runs automatically on every reply
- **Inbound emails appear in the unified Inbox** alongside X and LinkedIn conversations

You can connect mailboxes at any time. Existing sequences pick up the new mailbox automatically the next time an email step runs.

---

## Troubleshooting

**Gmail connection fails with "IMAP access disabled"**
- Visit Gmail settings > Forwarding and POP/IMAP and enable IMAP. For Workspace, your admin may need to enable it.

**Gmail connection fails with "Authentication failed"**
- Make sure 2-Step Verification is on and you used an App Password (not your regular password). Regenerate the App Password if needed.

**Outlook popup closes immediately**
- Check that popups are allowed for AutoReach. Try again. The page will reload to detect any successful connection.

**Mailbox shows "Expired" status**
- Click **Reconnect** on the mailbox card. For Gmail, regenerate the App Password if it was revoked. For Outlook, sign in again to renew the token.

**Replies aren't appearing in the Inbox**
- Confirm the mailbox is **Active** (not Paused or Expired)
- Replies are polled periodically, so allow a short delay
- Check that the original outbound email was actually sent (visible in the conversation timeline)

---

## Next Steps

- **[Email Channel and Email Steps](../outreach/email-channel.md)**: Add email steps to sequences and configure templates
- **[Inbox & Real-Time Messaging](../conversations/inbox.md)**: How email conversations show up alongside X and LinkedIn
- **[Email Finding](../enrichment/optional-enrichment.md)**: Discover work emails for leads who don't have one yet
