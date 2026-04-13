# Chrome Extension CRM

The AutoReach Chrome Extension brings your CRM pipeline into your browser. It works on LinkedIn and X, providing lead management, pipeline tracking, and account connectivity.

## CRM Pipeline Stages

Leads move through a visual pipeline:

**new → requested → accepted → contacted → replied → meeting → won / lost**

| Stage | Description |
|---|---|
| `new` | Freshly added to AutoReach |
| `requested` | Connection request or first message sent |
| `accepted` | Connection accepted or first reply received |
| `contacted` | Ongoing conversation started |
| `replied` | Lead has engaged with your outreach |
| `meeting` | Meeting booked |
| `won` | Deal closed |
| `lost` | Disqualified or no longer pursuing |

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

The lead moves to `requested` stage and the `invitation_id` is stored for lifecycle management.

## Phishing Protection

The extension includes Cyrillic character detection that flags profiles using lookalike characters (Cyrillic letters that visually resemble Latin letters). Flagged profiles display a warning before you interact with them.

## Next Steps

- **[Call Briefs](call-briefs.md)**: Generate pre-call preparation from your pipeline
- **[Meeting Booking](booking-integration.md)**: Track bookings via Calendly or Cal.com
