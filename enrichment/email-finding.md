# Email Finding

Email finding automatically discovers work email addresses for your leads using Findymail API integration. This is especially useful when you have an X/Twitter handle or LinkedIn profile but need to add email-based outreach to your workflow.

## How It Works

### Findymail Integration

AutoReach integrates with **Findymail**, a dedicated email discovery service. The flow works as follows:

1. You provide a LinkedIn profile URL or X/Twitter handle
2. AutoReach queries Findymail's API with the profile information
3. Findymail searches their database and web sources to find matching email addresses
4. Results are validated and returned to AutoReach
5. High-confidence emails are automatically populated on the lead profile

{% hint style="info" %}
**Your Own API Key:** Email finding requires your own Findymail API key. AutoReach does not provide one. You will need to sign up for Findymail separately and add your credentials to AutoReach.
{% endhint %}

### Setting Up Your Findymail API Key

To enable email discovery:

1. Go to **Settings > AI & Models**
2. Find the **Email Finding** section
3. Paste your Findymail API key in the field
4. Click **Test Connection** to verify it works
5. Save

Once configured, email finding automatically runs on all new leads.

## Email Validation

Discovered emails vary in reliability. AutoReach validates every email found:

### Format Validation

Strict regex patterns ensure emails match standard format:
- Must contain `@` symbol
- Must have a valid domain extension (.com, .io, .co.uk, etc.)
- Must not have unusual characters or spaces

### Generic Email Filtering

AutoReach automatically **excludes** generic email addresses:

- `info@` - Generic company inbox
- `contact@` - Generic contact form
- `support@` - Support department
- `sales@` - Generic sales email
- `hello@` - Generic greeting inbox

These low-confidence emails are filtered to keep your list focused on real people.

### Source Tracking

Every discovered email is tagged with its source for transparency:

| Source | Description |
|--------|-------------|
| **findymail** | Found via Findymail API lookup |
| **direct_search** | Discovered through direct web search |
| **pattern_detection** | Inferred from company domain patterns |
| **web_search** | Found on public web pages and directories |

You can view the source of each email on the lead profile to make your own judgment about confidence.

## Cost & Credit Usage

### Credit Consumption

Email finding uses your **Findymail API credits**, not AutoReach credits.

{% hint style="warning" %}
**Important:** Email discovery costs Findymail credits, which you manage separately from your AutoReach subscription. Make sure your Findymail account has sufficient credits to support your enrichment volume.
{% endhint %}

Each email lookup consumes:
- **1 Findymail credit** for a successful discovery
- **0 credits** if no email is found (no charge for attempts)

Monitor your Findymail dashboard to track credit usage.

### Cost Optimization

To use email credits efficiently:

- **Only enable for leads you'll actually contact** - Don't enrich every lead if you only plan to DM a few
- **Prioritize high-ICP leads** - Focus email discovery on your best-fit prospects
- **Use with intent data** - Combine email discovery with intent signals for best ROI
- **Batch enrichment** - Process leads in cohorts rather than one-by-one

## When Email Finding Runs

Email finding automatically triggers when:

- A new lead is added to AutoReach
- Your Findymail API key is configured
- The lead has a LinkedIn profile URL or X/Twitter handle
- No email is already populated on the profile

It does NOT re-run on already-enriched leads unless manually refreshed.

## Best Practices

### Set Realistic Expectations

Not all leads have discoverable emails. Success rates vary by:
- **Company size** - Larger companies have more online presence and are easier to find
- **Geographic region** - US/UK/Western Europe have better coverage
- **Industry** - Tech/SaaS has higher success rates than other sectors

Expect 30-70% discovery success rates depending on your lead list.

### Quality Over Quantity

{% hint style="success" %}
**Pro Tip:** Combine email discovery with your ICP targeting. High-ICP leads with discovered emails are more likely to respond to cold outreach. Don't just blast emails to every discovered address.
{% endhint %}

### Verify When Uncertain

If you're uncertain about an email address:

1. Check the **source** - Findymail direct API results are more reliable than pattern detection
2. Test small volumes - Send to 5-10 leads first and monitor bounce rates
3. Use list validation tools - Third-party tools like ZeroBounce can pre-validate your list

### Monitor Bounce Rates

If you're using email in your outreach sequences:
- Track bounce and invalid email rates in your **Activity Log**
- If bounce rate exceeds 5%, review the source of discovered emails
- Consider filtering out low-confidence sources (pattern_detection, web_search)

## Troubleshooting

### Email Finding Not Working

**Check your API key:**
1. Go to **Settings > AI & Models**
2. Verify your Findymail API key is entered correctly
3. Click **Test Connection** and look for success message

**Check your credit balance:**
1. Log in to your Findymail dashboard
2. Verify you have remaining API credits
3. If depleted, purchase more credits through Findymail

### No Emails Found

This is normal and expected. Not every lead has a discoverable email:
- Try manually searching LinkedIn/company website as backup
- Add emails manually from your own research
- Consider whether the lead is a better fit for X/LinkedIn-only outreach

### Too Many Generic Emails

If you're seeing info@, contact@, etc. in results:
- Verify your Findymail API key configuration
- Generic email filtering should auto-exclude these
- If they're still appearing, manually remove them from the lead profile
