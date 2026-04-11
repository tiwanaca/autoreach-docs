# Meeting Booking (Calendly / Cal.com)

AutoReach seamlessly integrates with your favorite meeting scheduling tools to automatically track and sync bookings with your outreach sequences.

## Supported Platforms

AutoReach connects with:
- **Calendly** — most popular booking platform
- **Cal.com** — open-source alternative
- **Custom booking URLs** — your own scheduling page or any other tool

## Setup & Configuration

Navigate to **Settings > Meeting & Calendar** to configure your booking integration.

{% hint style="info" %}
All meeting integrations require a one-time setup. Once connected, bookings sync automatically.
{% endhint %}

### Calendly Integration

The Calendly connection uses webhook events to detect new bookings in real-time.

**How it works:**
1. AutoReach registers a secure webhook endpoint that receives Calendly events
2. When someone books a meeting on your Calendly link, the `invitee.created` event fires
3. AutoReach verifies the event signature using HMAC-SHA256 encryption for security
4. The system extracts the attendee's email address and matches it to an existing lead
5. A meeting record is created and linked to that lead automatically

**Setup steps:**
1. Go to your Calendly settings and locate the **Webhooks** section
2. Add AutoReach's webhook URL (provided in Settings)
3. Select the `invitee.created` event
4. Save — you're ready to start tracking meetings

{% hint style="success" %}
Calendly webhooks are encrypted with HMAC-SHA256. AutoReach verifies every signature to ensure security and prevent spoofed events.
{% endhint %}

### Cal.com Integration

Cal.com integrations use token-based authentication with booking URL endpoints.

**Setup steps:**
1. Generate an API token in your Cal.com account settings
2. Paste the token in AutoReach's Meeting & Calendar settings
3. Provide your Cal.com booking URL
4. AutoReach will begin monitoring for new bookings

### Custom Booking URLs

Already using a scheduling tool that isn't Calendly or Cal.com? No problem.

You can use any booking URL:
- Your own custom scheduling page
- Acuity Scheduling, HubSpot, or any other platform
- The `{% raw %}{{ cal_link }}{% endraw %}` template variable automatically inserts your booking URL into your DMs

This way, leads can book meetings directly from your outreach messages.

## Meeting Tracking & Recording

Once configured, AutoReach automatically captures:
- **Attendee** — email and name of the person who booked
- **Time** — scheduled meeting date and time
- **Duration** — length of the scheduled meeting
- **Status** — confirmed, rescheduled, or canceled

## Automatic Lead Status Updates

When a lead books a meeting through your integration:

1. The lead's status in the sequence automatically updates to **"meeting"**
2. The meeting is recorded in the lead's conversation thread
3. A `meeting.booked` webhook event is triggered for downstream integrations
4. Meeting count is updated in sequence statistics

{% hint style="tip" %}
Monitor your sequence performance by checking the **Meeting booked** metric in the sequence dashboard.
{% endhint %}

## Using cal_link in Your Messages

The `{% raw %}{{ cal_link }}{% endraw %}` template variable inserts your booking URL directly into DMs and automated messages.

**Example:**
```
Hey {{firstName}}, let's sync up this week. 
Book a time that works: {{cal_link}}
```

When this message is sent, `{% raw %}{{ cal_link }}{% endraw %}` is replaced with your actual Calendly or Cal.com URL—making it easy for leads to schedule without hunting for a link.

## Viewing Meetings

All booked meetings appear in:
- **Inbox** — conversations with booked meetings show a meeting badge
- **Sequence analytics** — meeting count tracked per sequence
- **Lead profile** — complete meeting history on the lead's detail page

{% hint style="info" %}
Meeting status updates happen in real-time. You'll see bookings appear in AutoReach within seconds of the attendee confirming on Calendly or Cal.com.
{% endhint %}
