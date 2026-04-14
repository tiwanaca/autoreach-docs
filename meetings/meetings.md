# Meetings, Booking, and Call Briefs

AutoReach integrates with Calendly and Cal.com to detect when leads book meetings, and generates AI-powered call briefs to prepare you for every conversation.

---

## Booking Integration

### Supported Platforms

- **Calendly** - requires a paid subscription for webhook support
- **Cal.com** - free, no paid subscription required
- **Custom booking URLs** - any scheduling page (no automatic tracking)

### Calendly Setup

1. Add your Calendly booking link in **Settings > Meeting & Calendar**
2. Follow the instructions to get the webhook **Personal Access Token**
3. Enable **all scopes** for permissions
4. Save. AutoReach will receive booking events automatically

### Cal.com Setup

1. Add your Cal.com booking URL in **Settings > Meeting & Calendar**
2. AutoReach generates a **webhook URL** for you
3. Copy the webhook URL into your Cal.com webhook settings
4. Save. Bookings are tracked automatically

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

Leads move through a visual pipeline:

**New > On Hold > Requested > Accepted > Contacted > Replied > Meeting > Won / Lost**

| Stage | Description |
|---|---|
| New | Freshly added to AutoReach |
| On Hold | Temporarily paused |
| Requested | Connection request or first message sent |
| Accepted | Connection accepted or first reply received |
| Contacted | Ongoing conversation started |
| Replied | Lead has engaged with your outreach |
| Meeting | Meeting booked |
| Won | Deal closed |
| Lost | Disqualified or no longer pursuing |

Leads auto-progress through stages as sequence activity occurs. You can manually drag leads between stages to override.

### Adding Leads

On LinkedIn profile pages, the extension injects an **"Add to Leads"** button. You can also add leads from posts and comments in the LinkedIn feed. Lead addition is manual: you identify prospects and add them via the extension panel.

The extension is a **CRM tool**, not an automated lead generator. It does not scan feeds or match ICPs automatically.

### Account Connection

The extension handles connecting your LinkedIn and X accounts to AutoReach. It connects your active browser sessions and detects the platform automatically based on the current page.

### LinkedIn Connection Tracking

When you send a connection request through AutoReach, the extension tracks the connection status and supports auto-withdrawal. The lead moves to the Requested stage automatically.

## Next Steps

- **[AI Response Engine](../conversations/ai-response-engine.md)**: How AutoReach handles conversation follow-ups
- **[Chrome Extension Setup](../getting-started/chrome-extension.md)**: Install and configure the extension
