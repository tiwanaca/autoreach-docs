# Chrome Extension CRM

The AutoReach Chrome Extension brings your CRM pipeline into your browser. It works on LinkedIn and X, providing lead management, pipeline tracking, and account connectivity.

## CRM Pipeline Stages

Leads move through a visual pipeline:

**New → On Hold → Requested → Accepted → Contacted → Replied → Meeting → Won / Lost**

| Stage | Description |
|---|---|
| New | Freshly added to AutoReach |
| On Hold | Temporarily paused (e.g., cooldown after withdrawal) |
| Requested | Connection request or first message sent |
| Accepted | Connection accepted or first reply received |
| Contacted | Ongoing conversation started |
| Replied | Lead has engaged with your outreach |
| Meeting | Meeting booked |
| Won | Deal closed |
| Lost | Disqualified or no longer pursuing |

Leads auto-progress through stages as sequence activity occurs. You can manually drag leads between stages to override.

## Adding Leads

On LinkedIn profile pages, the extension injects an **"Add to Leads"** button. You can also add leads from posts and comments in the LinkedIn feed. Lead addition is manual — you identify prospects and add them via the extension panel.

The extension is a **CRM tool**, not an automated lead generator. It does not scan feeds or match ICPs automatically.

## Account Connection

The extension handles connecting your LinkedIn and X accounts to AutoReach:

- Extracts authentication cookies from your active browser sessions
- Registers accounts with the AutoReach backend
- Detects the platform automatically (LinkedIn vs X) based on the current page

## LinkedIn Connection Tracking

When you send a connection request through AutoReach, the extension captures the **invitation URN** via an interceptor script that monitors LinkedIn network requests. This allows the system to track the connection status and support auto-withdrawal.

The lead moves to the Requested stage and the connection request is tracked for lifecycle management.

## Name Normalization

Names with special characters are normalized for accurate matching.

## Next Steps

- **[Call Briefs](call-briefs.md)**: Generate pre-call preparation from your pipeline
- **[Meeting Booking](booking-integration.md)**: Track bookings via Calendly or Cal.com
