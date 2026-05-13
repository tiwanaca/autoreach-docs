# Meetings, Booking, and Call Briefs

AutoReach integrates with Calendly and Cal.com to detect when leads book meetings, and generates AI-powered call briefs to prepare you for every conversation.

## When to Set This Up

Set up meeting tracking **early — ideally during onboarding** — even if you don't think you need it yet. Two reasons:

- **Without a webhook, AutoReach can't know when a lead books.** It will still send your booking link in messages, and leads will still book meetings, but those bookings don't get marked in your pipeline automatically. You end up tracking meetings in your head or in a spreadsheet.
- **Meeting status feeds back into the system.** When a conversation reaches Meeting Booked, AutoReach extracts the winning exchanges as tone examples for future replies. Without webhook tracking, the AI doesn't learn from your wins.

If you don't have a paid Calendly plan, use **Cal.com** — it's free and webhook setup is one step. If you only have a custom booking URL, you can still inject it into messages via `{{booking_link}}`, but you'll need to track bookings manually.

---

## Booking Integration

### Supported Platforms

- **Calendly** - requires a paid subscription for webhook support
- **Cal.com** - free, no paid subscription required
- **Custom booking URLs** - any scheduling page (no automatic tracking)

Calendar configuration is **per-account**. Open an account from the **Accounts** page and use the Calendar section. The form has two parts: (1) the booking page (provider + URL), and (2) meeting tracking (provider-specific webhook setup, surfaced once the booking page is saved).

### Calendly Setup (Easier — No Form Field Required)

Calendly webhooks require a paid Calendly plan (Standard, Teams, or Enterprise).

AutoReach now uses an **invisible attribution** approach for Calendly. You no longer need to add a custom form field to your event — bookers see Calendly's default name and email fields only.

1. In the account's Calendar section, choose **Calendly** and paste your booking URL
2. Generate a Personal Access Token in [Calendly API settings](https://calendly.com/integrations/api_webhooks) and paste it into AutoReach
3. Click **Auto-fetch** to populate your Organization URI (or paste it manually)
4. Click **Register webhook** - AutoReach creates the webhook for you via the Calendly API

Attribution happens invisibly: AutoReach appends `utm_content=<platform>:<username>` to the booking URL injected via `{{booking_link}}`, and the webhook handler reads it from the booking's tracking metadata. Bookers see no extra fields and there is no friction at the booking step.

> **Legacy events:** If you previously added a "Username" form question, you can leave it or remove it — AutoReach falls back to the first form answer when `utm_content` is not present.

### Cal.com Setup

Cal.com is free and does not require a paid plan. Setup is a two-step process:

**Step 1 — Register the webhook**

1. In the account's Calendar section, choose **Cal.com** and paste your booking URL
2. Copy the webhook URL AutoReach generates
3. In Cal.com, go to **Settings → Developer → Webhooks → New Webhook**
4. Paste the webhook URL, subscribe to the `BOOKING_CREATED` event, and save

**Step 2 — Add a hidden username field to each event type**

Bookings need a `username` identifier so AutoReach can match them to a lead. To keep the field invisible:

1. In Cal.com, open the event type → **Advanced → Booking Questions**
2. Click **Add a question** with type **Short Text** and identifier `username`
3. Check **Disable input if the URL identifier is prefilled** — this hides the field from bookers
4. Save

AutoReach prefills `username` via the `{{booking_link}}` URL, so the field is filled invisibly and bookers never see it. Repeat step 2 for every event type you want to track.

### Custom Booking URLs

You can use any booking URL without webhook integration. The `{{booking_link}}` variable still works for injecting your URL into messages, but AutoReach will not automatically detect bookings. You will need to update meeting status manually.

### How Lead Matching Works

When a booking webhook fires, AutoReach matches the attendee to a lead using the tracking parameter embedded in your booking URL via the `{{booking_link}}` template variable, or by matching the attendee's email address.

### What Happens When a Meeting Is Booked

When a lead is matched:

1. The lead's status is set to **Meeting Booked**
2. Any pending follow-up actions are cancelled
3. The meeting is recorded in the conversation thread
4. Meeting count is updated in sequence statistics
5. A winning tone example is auto-captured from the conversation

### Using `{{booking_link}}` in Templates

The `{{booking_link}}` template variable injects your calendar URL with lead-specific tracking:

```
Book a time that works: {{booking_link}}
```

This becomes a personalized booking link with the lead's identifier appended as a tracking parameter.

---

## Call Brief Generation

Call briefs are AI-generated pre-call preparation documents that combine lead data, conversation history, and buyer intelligence into actionable talking points.

### How to Generate a Call Brief

1. Open any conversation in your **Inbox**
2. Click the **Call Brief** button
3. The brief generates in a few seconds and appears inline

The brief is saved to the conversation's metadata for future reference.

### What's Included

Call briefs include sections tailored to the available data:

| Section | Content |
|---|---|
| Lead Snapshot | Current role, company, industry, size, location, buyer score and status |
| Company Intelligence | LinkedIn company data, funding, tech stack |
| Conversation Recap | Summary of all prior messages, key topics, commitments |
| Pain Points Identified | Specific challenges mentioned in the conversation |
| Talking Points and Agenda | Suggested discussion topics tailored to the lead |
| Recent Activity | Recent posts from the lead |
| Offer Alignment | How your offer maps to their situation |
| Objection Preparation | Anticipated pushback and counter-points |
| Competitive Intel | Competitive context from your offer |
| Recommended Next Steps | Stage-aware suggestions for what to propose |

Each section is only included if relevant data is available.

### Data Sources

The brief draws from:

- **Lead profile**: Bio, headline, location, email, website
- **Company data**: Industry, size, funding, tech stack
- **Career history**: Work experience, education, skills
- **Web enrichment**: Company technologies, enrichment summary
- **Conversation transcript**: Full message history
- **Buyer intelligence**: Fit, intent, timing, and composite scores
- **Recent posts**: Latest social activity
- **Offer context**: Your value proposition and pain points

### Stage-Aware Recommendations

The brief adapts its recommendations based on conversation status:

| Status | Brief Focus |
|---|---|
| Meeting Booked | Focuses on meeting preparation, never suggests booking |
| Replied | Focuses on advancing toward a booking |
| Pending | Focuses on follow-up strategies |

---

## Chrome Extension CRM Pipeline

The AutoReach Chrome Extension brings your CRM pipeline into your browser. It works on LinkedIn and X, providing lead management, pipeline tracking, and account connectivity.

### CRM Pipeline Stages

Leads move through a visual pipeline. The typical progression is **New → Requested → Accepted → Contacted → Replied → Meeting → Won**, but **On Hold**, **Won**, and **Lost** can be reached from any stage at any time.

| Stage | Description |
|---|---|
| New | Freshly added to AutoReach |
| On Hold | Temporarily paused |
| Requested | Connection request sent |
| Accepted | Connection request accepted |
| Contacted | Ongoing conversation started |
| Replied | Lead has engaged with your outreach |
| Meeting | Meeting booked |
| Won | Deal closed |
| Lost | Disqualified or no longer pursuing |

Leads auto-progress through stages as sequence activity occurs. You can manually drag leads between stages to override.

### Adding Leads

On both LinkedIn and X profile pages, the extension injects an **"Add to Leads"** button into the profile action row. Lead addition is manual: you identify prospects and add them via the extension panel.

The extension is a **CRM tool**, not an automated lead generator. It does not scan feeds or match ICPs automatically.

### Account Connection

The extension handles connecting your LinkedIn and X accounts to AutoReach. It connects your active browser sessions and detects the platform automatically based on the current page.

### LinkedIn Connection Tracking

When you send a connection request through AutoReach, the extension tracks the connection status and supports auto-withdrawal. The lead moves to the Requested stage automatically.

## Next Steps

- **[AI Response Engine](../conversations/ai-response-engine.md)**: How AutoReach handles conversation follow-ups
- **[Chrome Extension Setup](../getting-started/chrome-extension.md)**: Install and configure the extension
