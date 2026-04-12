# Blacklisting Accounts

Blacklist specific X and LinkedIn accounts to prevent AutoReach from discovering, enriching, or engaging with them. This is useful for protecting competitors, existing customers, and personal contacts.

## How Blacklisting Works

When you blacklist an account:

1. **Discovery** - the account is excluded from search and prospect extraction
2. **Enrichment** - the account is skipped during profile enrichment
3. **Engagement** - the account will never receive messages, likes, follows, or comments
4. **All Offers & Sequences** - the blacklist applies globally across your workspace

Once blacklisted, an account remains blacklisted until you manually remove it.

## Common Use Cases

### Block Competitors
Prevent accidentally enriching or reaching out to competitor accounts. This saves enrichment costs and avoids awkward outreach.

```
Example competitors to blacklist:
- Salesforce, HubSpot, Pipedrive (if selling CRM)
- Deel, Guidepoint, Upland (if selling HR tools)
```

### Block Existing Customers
Do not re-engage customers who already use your product. Some customers may have free or trial accounts; blacklisting prevents repeated outreach.

```
Example: Blacklist @acme_corp and key decision-makers
if they are already a customer
```

### Block Personal Contacts
Prevent AutoReach from engaging with friends, family, or personal contacts who should not receive your sales messages.

```
Example: Blacklist your CEO, board members, or other
employees who might accidentally receive outreach
```

### Block Accounts Requesting "Do Not Contact"
If a prospect replies asking not to be contacted, add them to the blacklist immediately.

## Adding to Blacklist

### Method 1: From Account Card
1. Go to **Settings > Accounts**
2. Find the account you want to blacklist
3. Click the three-dot menu
4. Select **Add to Blacklist**

### Method 2: By Username or URL
1. Go to **Settings > Blacklist**
2. Click **Add Account**
3. Enter either:
   - **Username** (e.g., `@elon`, `john.smith.acme`)
   - **Profile URL** (e.g., `https://x.com/elon` or `https://linkedin.com/in/john-smith/`)
4. Click **Add to Blacklist**

### Method 3: Bulk Import
1. Go to **Settings > Blacklist**
2. Click **Bulk Import**
3. Paste usernames or URLs (one per line)
4. Click **Import**

{% hint style="info" %}
AutoReach automatically handles username variations and profile URL formats. You do not need to worry about exact formatting.
{% endhint %}

## Viewing Your Blacklist

Visit **Settings > Blacklist** to see all blacklisted accounts:

- **Account Name** - display name or username
- **Platform** - X or LinkedIn
- **Date Added** - when the account was blacklisted
- **Reason** - optional note you added (competitor, customer, personal, etc.)

## Removing from Blacklist

To unblacklist an account:

1. Go to **Settings > Blacklist**
2. Find the account in the list
3. Click the **Remove** button
4. Confirm removal

The account can now be discovered and engaged with again.

## Blacklist Best Practices

### Blacklist Competitors Early
Do not wait until you have enriched competitor accounts. Add them to your blacklist before starting discovery:

```
BEFORE: discovery runs, wastes $50 enriching competitors
AFTER:  competitors excluded from discovery, saves enrichment cost
```

### Use Notes for Context
Add a note when blacklisting to remember why later:

```
- "Acme Corp - competitor in data space"
- "Acme Corp - existing customer, enterprise plan"
```

### Separate Competitors from Do-Not-Contacts
Consider organizing your reasoning:

```
COMPETITORS (saves enrichment costs)
- Salesforce
- HubSpot

EXISTING CUSTOMERS (prevent re-engagement)
- Widget Corp
- TechCo Inc

DO-NOT-CONTACT (personal or explicit request)
- my-ceo@
- prospect-requested-removal@
```

### Do Not Over-Blacklist
Blacklist strategically. Over-blacklisting reduces your addressable market:

```
GOOD: Blacklist direct competitors only
BAD:  Blacklist entire industries or everyone who mentioned competitor
```

### Update Blacklist Quarterly
Review and update your blacklist quarterly:

- Remove customers who churned
- Add new competitors
- Remove "do not contact" requests after 6+ months (if appropriate)

## Impact on Enrichment Costs

Blacklisting saves money by avoiding enrichment of accounts you will never contact. By excluding competitors and other irrelevant accounts upfront, you reduce wasted enrichment and keep your pipeline focused on real prospects.

## Automation & Blacklist

### Sequences Respect Blacklist
If you have already enrolled someone in a sequence and then blacklist them:

- **Pending actions** are canceled
- **Active messages** are halted
- **They are removed** from the sequence

### Discovery Respects Blacklist
Future discovery runs automatically exclude blacklisted accounts from search results.

### Enrichment Respects Blacklist
Even if a blacklisted account gets added to your lead database through another source, enrichment is skipped.

{% hint style="warning" %}
Blacklisting is permanent until manually removed. If you blacklist someone by mistake, immediately go to Settings > Blacklist and remove them.
{% endhint %}

## Privacy & Compliance

Blacklisting supports your compliance efforts:

- **CAN-SPAM** - blacklist accounts that request removal
- **GDPR** - blacklist accounts from regions you do not operate in
- **Legal Holds** - blacklist accounts involved in legal disputes
- **Internal Policy** - blacklist employees, partners, friends

Maintain documentation of why accounts are blacklisted for compliance audits.

## Troubleshooting

### "I Can't Find the Account to Blacklist"
Ensure the account:
- **Exists on X or LinkedIn** (check manually first)
- **Is public** (private accounts may not be discoverable)
- **Username is spelled correctly**

Try pasting the full profile URL instead of the username.

### "Blacklist Isn't Preventing Discovery"
Blacklist applies to new discovery runs. If you have already discovered and enriched an account:

1. Remove the enriched lead from your database
2. Add the account to blacklist
3. Run discovery again

Blacklist does not retroactively remove already-enriched accounts.

### "I Blacklisted By Mistake"
Go to **Settings > Blacklist**, find the account, and click **Remove**. The account will be discoverable again in future runs.

## Next Steps

- **[Account Safety & Anti-Detection](account-safety.md)**: Learn how AutoReach keeps your accounts safe from platform detection
- **[Multi-Account Management](multi-account.md)**: Manage multiple accounts and their blacklist settings
