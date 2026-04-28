# Email Channel

Email is a first-class outreach channel in AutoReach alongside X and LinkedIn. You can add email steps to sequences, personalize subject and body with the same template variables and AI personalization used for DMs, and handle replies in the same unified Inbox.

> **Setup required:** Connect Gmail and/or Outlook before email steps are available. See [Connecting Email](../getting-started/connecting-email.md).

## Email as a Sequence Step

When building a sequence, **Email** appears as an action type when at least one email mailbox is connected.

### Configurable Fields

| Field | Description |
|---|---|
| Subject | Subject line template (supports `{{variable}}` placeholders) |
| Body | Body template (supports `{{variable}}` placeholders, multi-line) |
| AI Personalization | Toggle to have AI rewrite the body per lead using their context |
| Delay days / minutes | Wait time before this step executes |

### Personalization

Email steps use the **same template variable system** as DMs. All identity, network, profile, company, web enrichment, and special variables described in [DM Personalization](dm-personalization.md) work identically in email subject and body.

When **AI Personalization** is enabled, AutoReach:

1. Replaces known variables with lead data (`{{first_name}}`, `{{company_name}}`, etc.)
2. Sends the result plus the lead's profile and offer context to the AI
3. AI rewrites the email so it reads naturally and references specifics from the lead's profile

When AI Personalization is **off**, only direct variable substitution runs. Unknown placeholders are left literal.

### Booking Link

The `{{booking_link}}` variable works in email subject and body just like in DMs, with lead-specific tracking parameters appended to your calendar URL.

---

## Mailbox Routing

Each email step is sent from one of your connected mailboxes. The routing logic is automatic:

- `@gmail.com` and `@googlemail.com` recipients send from your Gmail account
- `@outlook.com`, `@hotmail.com`, `@live.com`, `@msn.com` (and regional variants) send from your Outlook account
- For other domains, AutoReach also checks the domain's MX records and routes Google Workspace and Microsoft 365 hosted domains accordingly
- Domains it cannot classify use your **Primary** mailbox

You set the primary mailbox from the **Email** card on the parent X or LinkedIn account's detail page by clicking **Make Primary** on the mailbox you want as default.

---

## Reply Detection

Connected mailboxes are polled every 15 minutes for new inbound messages. When a reply arrives:

- AutoReach matches it to the original outbound thread (by thread ID or `In-Reply-To` header)
- The lead's status is updated to **Replied**
- The full thread appears in the **Inbox** alongside X and LinkedIn conversations
- If AI auto-replies are enabled on the sequence, an AI response is queued

Email replies count toward your sequence's reply rate the same way DM replies do.

---

## Bounce Detection

Bounces are detected automatically on inbound traffic:

- Sender patterns (mailer-daemon, postmaster)
- Standardized bounce report formats
- Subject line indicators

When a bounce is detected:

1. The lead is marked with a bounced status
2. **All future email sends to that lead are skipped** automatically
3. The conversation card in the Inbox shows a bounce indicator

This prevents repeat sends to dead addresses and protects your sender reputation.

---

## Daily Limits

Email sends count toward the same per-sequence unified daily action limit that covers DMs, likes, comments, follows, and connection requests (default 20). When the limit is reached, remaining email sends are deferred to the next day along with any other queued actions. See [Scheduling & Send Limits](scheduling.md) for details.

In addition to the per-sequence limit, each mailbox is rate-paced at the provider level to keep delivery clean:

- **One in-flight send per mailbox** at a time (sends are serialized, not blasted in parallel)
- **Up to 10 sends per minute per mailbox** (token bucket)

Sends are spread across your activity window with natural gaps to avoid spam patterns.

---

## Inbound Auto-Replies

When a lead replies by email:

- An AI response is queued into the same auto-response system used for DMs
- Replies are sent with natural timing (delayed to feel human)
- The same **Max AI responses per conversation** limit applies
- The same per-conversation **AI ON / AI OFF** toggle in the Inbox controls whether AI replies for that thread

---

## Best Practices

1. **Start the sequence with engagement, not email.** A like or comment on LinkedIn before the email gives the lead context for who you are.
2. **Use AI personalization for the first email.** A first cold email referencing the lead's specific role and challenge outperforms a templated blast.
3. **Keep subject lines short and specific.** Avoid clickbait. Reference something concrete.
4. **Set a follow-up step.** Use a wait + email step to follow up if the first email goes unanswered.
5. **Check the Inbox.** Email replies often come hours later than DM replies. Glance at the Inbox each morning so you don't miss warm threads.
6. **Watch your bounce rate.** A spike in bounces usually means lead data quality is low. Run [website finding](../enrichment/optional-enrichment.md) before [email finding](../enrichment/optional-enrichment.md) to improve email accuracy.

---

## Email Channel vs Email Finding

Two related but separate features:

| Feature | Purpose |
|---|---|
| **Email Channel** (this page) | Sends and receives email through your connected mailboxes |
| **Email Finding** | Discovers email addresses for leads using a third-party service (Findymail) |

Email Finding prepares the data. The Email Channel delivers messages. See [Email and Website Finding](../enrichment/optional-enrichment.md) for the discovery side.

---

## Next Steps

- **[Connecting Email](../getting-started/connecting-email.md)**: Set up Gmail or Outlook
- **[DM Personalization](dm-personalization.md)**: Variables and AI personalization that also apply to email
- **[Inbox](../conversations/inbox.md)**: Where email replies show up
- **[Email Finding](../enrichment/optional-enrichment.md)**: Find email addresses for leads who don't have one yet
