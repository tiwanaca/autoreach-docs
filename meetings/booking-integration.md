# Meeting Booking (Calendly / Cal.com)

AutoReach integrates with Calendly and Cal.com to automatically detect when leads book meetings and update their status in your sequences.

## Supported Platforms

- **Calendly** — requires a paid subscription for webhook support
- **Cal.com** — free, no paid subscription required
- **Custom booking URLs** — any scheduling page (no automatic tracking)

## Calendly Setup

1. Add your Calendly booking link in **Settings > Meeting & Calendar**
2. Follow the instructions to get the webhook **Personal Access Token**
3. Enable **all scopes** for permissions
4. Save — AutoReach will receive booking events automatically

AutoReach verifies every webhook event using HMAC-SHA256 signature validation.

## Cal.com Setup

1. Add your Cal.com booking URL in **Settings > Meeting & Calendar**
2. AutoReach generates a **webhook URL** for you
3. Copy the webhook URL into your Cal.com webhook settings
4. Save — bookings are tracked automatically

## How Lead Matching Works

When a booking webhook fires, AutoReach matches the attendee to a lead using this strategy:

1. **LinkedIn public identifier** — if the booking came from a LinkedIn lead (identified by a platform prefix in the tracking parameter)
2. **Username** — match by platform username
3. **Email** — match by attendee email address

The tracking parameter is embedded in your booking URL via the `{{booking_link}}` template variable. Calendly uses the `a1` parameter; Cal.com uses the `x_username` field.

## What Happens When a Meeting Is Booked

When a lead is matched:

1. The lead's status is set to **Meeting Booked**
2. Any pending follow-up actions are cancelled
3. The meeting is recorded in the conversation thread
4. Meeting count is updated in sequence statistics
5. A winning tone example is auto-captured from the conversation

## Using `{{booking_link}}` in Templates

The `{{booking_link}}` template variable injects your calendar URL with lead-specific tracking:

```
Book a time that works: {{booking_link}}
```

This becomes: `https://calendly.com/you?a1=john-doe` (Calendly) or `https://cal.com/you?x_username=johndoe` (Cal.com).

## Custom Booking URLs

You can use any booking URL without webhook integration. The `{{booking_link}}` variable still works for injecting your URL into messages, but AutoReach won't automatically detect bookings — you'll need to update meeting status manually.

## Next Steps

- **[Call Briefs](call-briefs.md)**: Prepare for booked meetings with AI-generated briefs
- **[Chrome Extension](chrome-extension-crm.md)**: Track meeting status from your browser
