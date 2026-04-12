# Meeting Booking (Calendly / Cal.com)

AutoReach seamlessly integrates with your favorite meeting scheduling tools to automatically track and sync bookings with your outreach sequences.

## Supported Platforms

AutoReach connects with:
- **Calendly** - the most popular booking platform
- **Cal.com** - an open-source alternative
- **Custom booking URLs** - your own scheduling page or any other tool

## Setup & Configuration

Navigate to **Settings > Meeting & Calendar** to configure your booking integration.

{% hint style="info" %}
All meeting integrations require a one-time setup. Once connected, bookings sync automatically.
{% endhint %}

### Calendly Integration

{% hint style="warning" %}
**Calendly requires a paid subscription** to use webhooks. The free plan does not support webhook integrations.
{% endhint %}

The Calendly connection uses webhook events to detect new bookings in real-time.

**Setup steps:**
1. Add your Calendly booking link in AutoReach's Meeting & Calendar settings
2. Click **Next**
3. When prompted for the webhook, follow the instructions to get the **auth token**
4. Enable permissions for **all scopes**
5. Save. AutoReach will now receive booking events automatically

AutoReach verifies every webhook event signature using HMAC-SHA256 encryption for security.

### Cal.com Integration

Cal.com is a free alternative with **no paid subscription required**. The webhook setup is simpler than Calendly.

**Setup steps:**
1. In AutoReach's Meeting & Calendar settings, add your Cal.com booking URL
2. AutoReach will generate a **webhook link** for you
3. Copy that webhook link and paste it into your Cal.com webhook settings
4. Save. You are ready to start tracking meetings

### Calendar Form Field Requirement

{% hint style="warning" %}
**Required for meeting tracking**: If you use Calendly or Cal.com with a webhook, you must add **one extra form field as the first question** in your calendar event. AutoReach will auto-populate this field with the name of the person who booked the meeting. This is needed to track which lead booked the event.
{% endhint %}

### Custom Booking URLs

You can use any booking URL (Acuity Scheduling, HubSpot, or your own scheduling page). With a custom calendar link, **no webhook setup is needed**.

The `{% raw %}{{ cal_link }}{% endraw %}` template variable automatically inserts your booking URL into your DMs, making it easy for leads to book meetings directly from your outreach messages.

{% hint style="info" %}
**Webhooks are not mandatory** but they are needed for AutoReach to automatically track when a meeting has been booked. Without a webhook, you will need to update meeting status manually.
{% endhint %}

## Meeting Tracking & Recording

Once configured, AutoReach automatically captures:
- **Attendee** - email and name of the person who booked
- **Time** - scheduled meeting date and time
- **Duration** - length of the scheduled meeting
- **Status** - confirmed, rescheduled, or canceled

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

When this message is sent, `{% raw %}{{ cal_link }}{% endraw %}` is replaced with your actual Calendly or Cal.com URL, making it easy for leads to schedule without hunting for a link.

## Viewing Meetings

All booked meetings appear in:
- **Inbox** - conversations with booked meetings show a meeting badge
- **Sequence analytics** - meeting count tracked per sequence
- **Lead profile** - complete meeting history on the lead's detail page

{% hint style="info" %}
Meeting status updates happen in real-time. You will see bookings appear in AutoReach within seconds of the attendee confirming on Calendly or Cal.com.
{% endhint %}

## Next Steps

- **[Call Brief Generation](call-briefs.md)**: Prepare for booked meetings with AI-generated call briefs
- **[Chrome Extension CRM](chrome-extension-crm.md)**: Track meeting status and pipeline stages from your browser
