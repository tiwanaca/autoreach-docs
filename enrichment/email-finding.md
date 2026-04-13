# Email Finding

Email finding discovers work email addresses for leads using the Findymail API. It is a **separate, optional enrichment** that is not part of the standard pipeline -- you must trigger it explicitly and provide your own Findymail API key.

## How It Works

Email finding makes a single Findymail API call per lead, passing the lead's name and company domain (or company name as fallback). Findymail handles pattern generation and verification on their servers and returns a single email address or null.

There is no local pattern matching, no waterfall of multiple providers, and no SMTP or MX record verification. AutoReach validates the returned email's format and filters out generic/role-based addresses before storing it.

### Preconditions

For email finding to run, the following must be true:

1. **User has a Findymail API key** configured in settings
2. **Lead has a name** (first name is extracted and required)
3. **Lead has at least one of:**
   - A website URL (domain is extracted)
   - A LinkedIn profile URL (LinkedIn company website used)
   - A company name from LinkedIn data
   - A bio longer than 20 characters

Last name is optional -- the service handles single-name leads gracefully.

### What Gets Passed to Findymail

| Field | Source |
|---|---|
| First name | Parsed from lead name |
| Last name | Parsed from lead name (optional) |
| Domain | Extracted from website URL or LinkedIn company website |
| Company name | Fallback when no domain available -- from LinkedIn role or company data |

## What Gets Stored

| Field | Description |
|---|---|
| Email | The discovered email address |
| Email Confidence | Confidence score (0.95 when found, 0 when not) |
| Email Verified At | Timestamp if Findymail reports the email as verified |
| Email Source | Source identifier (e.g., "findymail") |

### Confidence Scoring

Confidence is binary:
- **0.95** -- Findymail returned an email
- **0** -- No email found

There is no local scoring algorithm or confidence adjustment based on pattern quality.

## Email Validation

Every email returned by Findymail is validated locally before storage:

- **Format validation** -- regex check for standard email format
- **Generic address filtering** -- blocks 30+ role-based prefixes (`info@`, `support@`, `sales@`, `team@`, `help@`, `admin@`, etc.)
- **Sanitization** -- strips emojis and special characters

There is no SMTP verification, MX record check, or catch-all detection performed by AutoReach. The verified-at timestamp reflects Findymail's own verification status.

## How It's Triggered

Email finding does **not run automatically** when leads are added. It must be triggered explicitly:

| Trigger | Description |
|---|---|
| `POST /api/enrich` with `email: true` | Manual enrichment -- select leads and enable email finding |
| `POST /api/enrich/re-enrich-skipped` | Retry failed or skipped leads |

It does not re-run on leads that already have an email unless manually refreshed.

## Setup

Email finding requires your own Findymail API key. Add it in your AutoReach settings. Without a configured key, email finding jobs will skip.

## Cost

Email finding uses credits from your **Findymail account**, not from AutoReach.

Findymail pricing depends on your plan (approximately $0.05 per email lookup). Manage credits through Findymail's dashboard. If credits are exhausted, Findymail returns an error and email finding stops until credits are replenished.

## Error Handling

| Error | Behavior |
|---|---|
| Rate limit (429) | Retried with exponential backoff, up to 3 attempts |
| Invalid API key (401) | Not retried -- error recorded on the lead |
| Credits exhausted (402) | Not retried -- error recorded on the lead |
| Network errors | Retried with exponential backoff |
| Missing required data | Skipped -- no name or domain/company available |
| Invalid/generic email returned | Discarded -- lead marked as enriched with no email |

## Troubleshooting

**Email finding not working?**
- Verify your Findymail API key is configured correctly in settings
- Check your Findymail credit balance -- 402 errors mean credits are exhausted

**No emails found for some leads?**
- Not every lead has a discoverable email. Success rates vary by industry, company size, and region
- Ensure leads have a website URL or company name -- email finding needs a domain to search against
- Run website finding first to populate website URLs for better domain coverage

**Generic emails appearing?**
- The generic filter blocks 30+ role-based prefixes automatically
- If one slips through, manually update or remove the email from the lead profile

## Next Steps

- **[Website Finding](website-finding.md)**: Find company domains first to improve email discovery rates
- **[Web Enrichment](web-enrichment.md)**: Gather additional company context from the web
- **[Enrichment Pipeline](pipeline.md)**: See how the standard enrichment pipeline works
