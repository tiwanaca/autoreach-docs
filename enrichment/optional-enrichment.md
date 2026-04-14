# Email Finding and Website Finding

Email finding and website finding are **optional enrichment steps** that are not part of the standard pipeline. You trigger them explicitly from the Leads page.

---

## Website Finding

Website finding discovers company and personal websites for leads using AI-powered web search. Found websites improve email finding accuracy (providing a domain to search against) and give AI more context for outreach personalization.

### How It Works

Website finding uses AI web search to find a lead's company or personal website. It tries multiple approaches and returns the best match.

A lead must have at least one of:
- A LinkedIn profile URL
- A bio longer than 20 characters

Leads without either are skipped.

### What Gets Stored

| Field | Description |
|---|---|
| Website URL | The discovered website URL |
| Website Source | How it was found (LinkedIn company, bio, direct search) |

### Domain Filtering

Website finding filters out social media platforms, link aggregators, URL shorteners, scheduling tools, and other non-website domains. Only actual company or personal websites are accepted.

### How to Trigger

Select leads from the Leads page and enable the website finding option when triggering enrichment. You can also retry failed or skipped leads from the same interface.

---

## Email Finding

Email finding discovers work email addresses for leads using the Findymail API. It requires your own Findymail API key.

### How It Works

Email finding makes a single Findymail API call per lead, passing the lead's name and company domain (or company name as fallback). Findymail handles verification on their servers and returns a verified email address or null.

AutoReach validates the returned email's format and filters out generic/role-based addresses (info@, support@, sales@, etc.) before storing it.

### Preconditions

For email finding to run:

1. **User has a Findymail API key** configured in Settings
2. **Lead has a name** (first name is extracted and required)
3. **Lead has at least one of:**
 - A website URL (domain is extracted)
 - A LinkedIn profile URL (LinkedIn company website used)
 - A company name from LinkedIn data
 - A bio longer than 20 characters

### What Gets Stored

| Field | Description |
|---|---|
| Email | The discovered email address |
| Email Verified At | Timestamp if Findymail reports the email as verified |

### Setup

Go to **Settings > AI & Models** and enter your Findymail API key. Once saved, AutoReach will use Findymail's database to look up verified work email addresses for your leads.

If you do not have a Findymail account, you can sign up at findymail.com and add your key afterward.

### Cost

Email finding uses credits from your **Findymail account**, not from AutoReach. If credits are exhausted, Findymail returns an error and email finding stops until credits are replenished.

### How to Trigger

Select leads from the Leads page and enable the email finding option when triggering enrichment. You can also retry failed or skipped leads from the same interface.

---

## Running Website Finding Before Email Finding

Website finding feeds into email finding. The email finder uses the lead's website URL to extract a company domain, which is the preferred input for Findymail lookups. Running website finding before email finding improves email discovery rates by providing a verified domain.

This is not a strict dependency. Email finding can proceed without a website URL by falling back to LinkedIn company data or the lead's bio.

## Error Handling

For both services, transient errors (rate limits, network issues) are automatically retried. Permanent errors are recorded on the lead. Leads missing required data are skipped.

## Troubleshooting

**Email finding not working?**
- Verify your Findymail API key is configured correctly in Settings
- Check your Findymail credit balance

**No emails found for some leads?**
- Not every lead has a discoverable email. Success rates vary by industry and company size
- Ensure leads have a website URL or company name
- Run website finding first to populate website URLs for better domain coverage

## Next Steps

- **[Web Enrichment](web-enrichment.md)**: Gather additional company context from the web
- **[Enrichment Pipeline](pipeline.md)**: See how the standard enrichment pipeline works
