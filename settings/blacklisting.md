# Blacklisting

Blacklist specific accounts to prevent AutoReach from discovering, enriching, or engaging with them. Useful for excluding competitors, existing customers, and contacts who have requested not to be contacted.

## How Blacklisting Works

Blacklisted accounts are stored by **normalized username** (lowercase, `@` stripped). The system also stores platform identifiers for precise cross-platform matching.

When you blacklist an account:

1. The account is added to the blacklist
2. All matching leads are found (case-insensitive username match)
3. All sequence enrollments for those leads are identified
4. All pending, queued, and deferred actions for those leads are **cancelled**
5. The leads are **removed** from all sequences

The response includes a count of removed sequence leads so you can see the impact.

## Adding to Blacklist

### Single Account

Go to **Settings > Blacklist**, click **Add Account**, and enter a username or profile URL.

### Bulk Import

Go to **Settings > Blacklist**, click **Bulk Import**, and paste up to **1,000 lead IDs** (one per line). The same cascade removal logic applies to each.

## What Blacklisting Prevents

- **Discovery**: Blacklisted accounts are excluded from search results
- **Enrichment**: Skipped during profile enrichment
- **Engagement**: Never receive messages, likes, follows, or comments
- **All sequences**: Applied globally across all sequences and offers

## Removing from Blacklist

Go to **Settings > Blacklist**, find the account, and click **Remove**. The account becomes discoverable and engageable again in future runs.

Removing from the blacklist does not restore previously deleted sequence leads or actions.

## Common Use Cases

- **Competitors** — avoid wasting enrichment costs on accounts you'll never contact
- **Existing customers** — prevent duplicate outreach
- **Do-not-contact requests** — comply with prospects who asked to stop receiving messages
- **Internal contacts** — exclude your own team, CEO, or board members

## Next Steps

- **[Account Safety](account-safety.md)**: How AutoReach protects your accounts
- **[Multi-Account Management](multi-account.md)**: Managing accounts and their settings
