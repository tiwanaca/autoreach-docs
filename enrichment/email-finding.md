# Email Finding

Email finding automatically discovers work email addresses for your leads. When you have an X handle or LinkedIn profile for a prospect, AutoReach can look up their professional email to enable multi-channel outreach.

## How It Works

AutoReach integrates with a third-party email discovery service to find work emails for your leads. The process is straightforward:

1. You provide a LinkedIn profile URL or X handle for a lead
2. AutoReach queries the email discovery service with the profile information
3. Results are validated and filtered before being added to the lead profile
4. Verified emails are automatically populated on the lead record

{% hint style="info" %}
**Your Own API Key Required:** Email finding requires your own API key for the third-party email discovery service. AutoReach does not provide one. Sign up for the service separately and add your credentials in AutoReach.
{% endhint %}

## Setup

To enable email discovery:

1. Go to **Settings > AI & Models**
2. Find the **Email Finding** section
3. Paste your API key in the field
4. Click **Test Connection** to verify it works
5. Save

Once configured, email finding automatically runs on all new leads.

## Email Validation

Every discovered email goes through validation before it is added to a lead profile:

- **Format validation** ensures emails match standard formatting (valid domain, no unusual characters)
- **Generic address filtering** automatically excludes non-personal addresses like company inboxes, support departments, and generic contact emails
- **Deduplication** prevents the same email from being added to multiple leads incorrectly

This filtering keeps your lead list focused on real, reachable people.

## When Email Finding Runs

Email finding automatically triggers when:

- A new lead is added to AutoReach
- Your API key is configured and active
- The lead has a LinkedIn profile URL or X handle
- No email is already populated on the lead profile

It does not re-run on already-enriched leads unless manually refreshed.

## Cost and Credit Usage

Email discovery uses credits from your **third-party email service account**, not from AutoReach. You manage and purchase those credits separately through the email discovery provider.

{% hint style="warning" %}
Make sure your email discovery account has sufficient credits to support your enrichment volume. If credits are depleted, email finding will stop working until you add more.
{% endhint %}

To use credits efficiently:

- **Only enable for leads you plan to contact** rather than enriching every lead
- **Prioritize high-ICP leads** to focus discovery on your best-fit prospects
- **Combine with intent signals** for the best return on your credits

## Best Practices

### Quality Over Quantity

{% hint style="success" %}
**Pro Tip:** Combine email discovery with your ICP targeting. High-ICP leads with discovered emails are more likely to respond to outreach. Avoid blasting emails to every discovered address.
{% endhint %}

### Set Realistic Expectations

Not all leads have discoverable emails. Success rates vary by company size, geographic region, and industry. Tech and SaaS companies tend to have better coverage than other sectors.

### Monitor Bounce Rates

If you are using email in your outreach sequences:

- Track bounce and invalid email rates in your **Activity Log**
- If bounce rates climb above acceptable levels, pause and review your lead sources
- Test with small volumes first (5 to 10 leads) before scaling up

## Troubleshooting

### Email Finding Not Working

**Check your API key:**
1. Go to **Settings > AI & Models**
2. Verify your API key is entered correctly
3. Click **Test Connection** and look for a success message

**Check your credit balance:**
1. Log in to your email discovery service dashboard
2. Verify you have remaining API credits
3. If depleted, purchase more credits through the provider

### No Emails Found

This is normal and expected. Not every lead has a discoverable email.

- Try manually searching LinkedIn or the company website as a backup
- Add emails manually from your own research
- Consider whether the lead is a better fit for X or LinkedIn-only outreach

### Generic Emails Appearing

If you are seeing non-personal addresses in results:

- Verify your API key configuration is correct
- Generic email filtering should exclude these automatically
- If they persist, manually remove them from the lead profile

## Next Steps

- **[Website Finding](website-finding.md)**: Discover professional websites to enrich lead profiles further
- **[Template Variables](../outreach/template-variables.md)**: Use discovered emails and data in personalized outreach messages
