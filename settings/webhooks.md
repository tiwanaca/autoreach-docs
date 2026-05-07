# Webhooks

Webhooks let you receive real-time notifications when important events happen in AutoReach. Instead of checking your dashboard manually, AutoReach sends an HTTP request to a URL you specify whenever a lead is scored, a reply comes in, a message is sent, and more.

This is useful for connecting AutoReach to your CRM, Slack workspace, internal tools, or any custom workflow that can receive HTTP requests.

---

## Available Events

Each webhook subscribes to **one event**. To receive notifications for multiple events, create a separate webhook for each. The following events are available:

| Event | Description |
|---|---|
| **Lead Created** | A new lead has been added to your account (from any source) |
| **Lead Scored** | A lead has been scored by the buyer intelligence engine |
| **Reply Received** | A lead replied to your DM or message |
| **Message Sent** | An outreach message (DM) was sent to a lead |
| **AI Response Sent** | The AI auto-responder sent a follow-up message in a conversation |
| **Meeting Booked** | A lead booked a meeting through your calendar link |
| **Enrichment Completed** | A lead's profile enrichment has finished |

---

## Creating a Webhook

1. Go to **Settings > Webhooks**
2. Click **Add Webhook**
3. Enter a **name** for the webhook (e.g., "CRM Sync" or "Slack Alerts")
4. Enter the **URL** where you want to receive events (must use HTTPS)
5. Select which **event** you want to subscribe to
6. (Optional) Enter a **signing secret** for payload verification (minimum 16 characters)
7. Click **Create**

You can create up to **10 webhooks** per account.

> **Tip:** Start with just one or two events to verify your integration is working before subscribing to everything.

---

## Testing a Webhook

Before relying on a webhook in production, test it to make sure your endpoint is reachable and responding correctly.

1. Go to **Settings > Webhooks**
2. Click the edit icon on the webhook you want to test
3. In the edit dialog, select an event type and click **Send Test Payload**
4. AutoReach sends a sample payload to your URL and shows whether it succeeded or failed

---

## Editing and Deleting Webhooks

To **edit** a webhook, click the edit icon next to it and update any fields (URL, events, name, secret, or enabled/disabled status). Click **Save** to apply changes.

To **delete** a webhook, click the delete button next to it. Deleted webhooks stop receiving events immediately.

You can also **disable** a webhook without deleting it. Disabled webhooks are saved but do not receive any events until re-enabled.

---

## Payload Format

Every webhook delivery is a JSON payload with three fields:

- **Event name** - which event triggered this delivery
- **Timestamp** - when the event occurred (ISO 8601 format)
- **Data** - the event-specific information

### What data is included

The data varies by event type, but for lead-related events you can expect:

- **Lead identity**: name, username, bio, headline, location, email (if found), profile links for X and LinkedIn
- **Scoring**: overall buyer score, fit/intent/timing breakdown, buyer state, suggested outreach strategy, recommended channel
- **Source**: how the lead was discovered, the original content or post that surfaced them
- **Enrichment**: professional summary, work experience, education, skills, certifications, languages, company details, and recent posts
- **Web intelligence**: company website data and additional research findings

For message and reply events, the payload includes the message content and conversation context.

---

## Verifying Webhook Signatures

If you set a signing secret when creating your webhook, every delivery includes a signature header (`X-Webhook-Signature`) that you can use to verify the payload came from AutoReach and was not tampered with.

The signature is an HMAC-SHA256 hash of the raw JSON payload, prefixed with `sha256=`. To verify:

1. Read the raw request body (before parsing JSON)
2. Compute HMAC-SHA256 using your signing secret as the key
3. Compare your computed signature with the value in the `X-Webhook-Signature` header

> **Warning:** Always use a constant-time comparison function when verifying signatures to prevent timing attacks.

---

## Retry Behavior

If your endpoint is unreachable or returns an error, AutoReach retries the delivery up to **3 times** with increasing delays between attempts. If all retries fail, the webhook shows an error status in the dashboard with the failure reason.

You can check the last delivery status and any errors for each webhook in the webhooks list.

---

## Use Cases

### CRM Integration
Subscribe to **Lead Scored** and **Meeting Booked** events to automatically create or update contacts in your CRM (Salesforce, HubSpot, Pipedrive, etc.) whenever AutoReach identifies a qualified buyer or books a meeting.

### Slack Notifications
Subscribe to **Reply Received** and **Meeting Booked** events to get instant Slack alerts when a prospect responds or schedules a call. Use a Slack incoming webhook URL as your endpoint, or route through Zapier/Make.

### Custom Workflows
Subscribe to **Enrichment Completed** to trigger your own analysis pipeline when a lead's profile data is ready. Or use **Message Sent** to log outreach activity in a custom reporting system.

### Lead Routing
Subscribe to **Lead Created** and route new leads to different team members or tools based on the lead's location, industry, or score.

---

## Next Steps

- **[AI Model Configuration](ai-models.md)**: Customize which AI models power your scoring and messaging
- **[Account Safety](account-safety.md)**: Configure rate limits and safety settings for your connected accounts
- **[Cost Estimation](cost-estimation.md)**: Understand and estimate your pipeline costs
