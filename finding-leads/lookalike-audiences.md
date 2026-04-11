# Lookalike Audience Discovery

Find entire audiences of prospects by identifying influencers whose followers match your ICP. Scale rapidly by discovering thousands of relevant prospects through seed account selection.

## How It Works

Lookalike Audience Discovery works in three stages:

### Stage 1: Identify Relevant Seed Accounts

We search for influencers and thought leaders whose audiences match your target market:

**Search Categories:**

| Category | Examples |
|----------|----------|
| **Industry Publications** | TechCrunch, VentureBeat, Forbes, Harvard Business Review |
| **Professional Communities** | Y Combinator, Product Hunt, Indie Hackers |
| **Vendor/Competitors** | Salesforce, HubSpot, Zendesk (if they're in your market) |
| **Thought Leaders** | Known experts and influencers in your vertical |
| **Vertical-Specific Accounts** | Industry associations, niche publications, specialized communities |

Our AI generates targeted search queries to find seed accounts across X and LinkedIn.

### Stage 2: Account Type Classification

Each discovered account is automatically classified:

- **Publication:** Industry news, research, trends
- **Association:** Professional organizations, communities
- **Vendor:** Competitors, adjacent tools, ecosystem players
- **Analyst:** Research firms, analyst communities
- **Executive:** C-suite thought leaders, recognized experts
- **Community:** User groups, forums, discussion communities

Classification helps you understand audience composition and predict prospect quality.

### Stage 3: Follower Extraction and ICP Matching

We extract followers from seed accounts and:
- **Score each follower** against your ICP
- **Identify buyer intent signals** from their profile and activity
- **Enrich profiles** with company, role, and location data
- **Add qualified prospects** to your lead database

## Minimum Follower Thresholds

AutoReach requires seed accounts meet minimum audience size:

- **Minimum:** 1,000 followers (ensures real audience)
- **Preferred:** 10,000+ followers (stronger signal quality)
- **Sweet spot:** 5,000-50,000 followers (engaged, targeted audiences)

Accounts with smaller audiences are skipped. Very large accounts (100,000+) are used but may have more diverse, less targeted followers.

## Location-Aware Discovery

Your offer's **preferred_locations** setting automatically:
- Filters seed accounts by geographic relevance
- Prioritizes accounts with audiences in your target regions
- Weights location signals in follower matching

This ensures you're finding prospects in your target markets, not random global followers.

## AI-Generated Search Queries

AutoReach generates smart search queries for both platforms:

**X/Twitter searches might include:**
- "top analytics thought leaders"
- "sales operations experts"
- "B2B SaaS founders"
- "head of sales twitter accounts"

**LinkedIn searches might include:**
- "Head of operations communities"
- "SaaS industry associations"
- "Digital transformation thought leaders"
- "People analytics thought leaders"

These queries automatically adapt to your offer's domain.

## Follower Extraction Process

### For X/Twitter:
- Fetch up to 5,000 followers per seed account
- Extract profile information (bio, location, follower count)
- Identify mutual followers across seed accounts
- Score against ICP

### For LinkedIn:
- Extract connection/follower lists where available
- Identify company affiliations
- Extract role and seniority signals
- Score against ICP

## Best Practices

1. **Start with 5-10 seed accounts:** Too few limits your prospect pool. Too many creates noise.

2. **Mix account types:** Combine publications, communities, and thought leaders for diverse audiences.

3. **Prioritize engaged audiences:** Accounts with high engagement rates have more active followers.

4. **Review seed account alignment:** Manually check that seed accounts' audiences match your ICP before running extraction.

5. **Monitor follower quality:** Track response rates from lookalike audiences. If low, seed accounts may not align well.

6. **Refresh seed accounts monthly:** Audiences change over time. Update your seed account list quarterly.

7. **Combine with other methods:** Use lookalike audiences to complement content search and people search, not replace them.

## Automatic Rotation Under Autopilot

When AutoReach Autopilot is enabled, seed accounts automatically rotate:

- **Rotation interval:** Every 2 hours
- **Maximum extractions:** Prevents exhausting a single account's followers
- **New seed discovery:** Automatically identifies fresh seed accounts as previous ones saturate
- **Continuous scaling:** You get continuous prospect flow without manual intervention

This keeps your prospect pipeline flowing while maintaining quality and preventing rate limiting.

## Example Workflow

**Offer:** "API platform for payment processing"

**Seed accounts you might select:**
- [@TechCrunch](https://twitter.com/TechCrunch) - Tech news, startup audience
- [@a16z](https://twitter.com/a16z) - VC firm, growth-focused founder audience
- [@PaulGraham](https://twitter.com/paulgraham) - Y Combinator, technical founder audience
- [@StripesSupport](https://twitter.com/StripesSupport) - Competitor ecosystem
- Y Combinator Alumni network - Early-stage companies, technical founders

**Expected results:** Thousands of CTOs, VPs Engineering, and startup founders who follow payment/API thought leaders—perfect match for your ICP.

**Follower extraction:** 5,000 followers × 5 accounts = 25,000 prospects automatically scored and filtered down to 2,000-5,000 ICP matches.

## Troubleshooting

**Not finding relevant seed accounts?**
- Broaden your search categories (include competitors, not just thought leaders)
- Check if your target audience is active on the platform you're searching
- Verify your offer description includes relevant domain keywords

**Extracted followers have low ICP match rate?**
- Review your seed accounts—they may not align with your actual ICP
- Check your ICP definition (pain points, audience, search signals)
- Try different seed accounts that directly focus on your niche

**Seed accounts are getting exhausted quickly?**
- This is normal—followers extracted don't get re-extracted
- Automatic rotation finds new seed accounts (under Autopilot)
- Add more seed accounts manually to increase prospect flow

**Getting many prospects with no X/LinkedIn profile?**
- Some followers don't maintain active profiles
- These are filtered out during enrichment
- This is normal and expected

**Follower quality seems low?**
- Check seed account audience composition
- Verify seed accounts are engaged (not just large follow counts)
- Consider whether your target audience follows these accounts
- Try more niche, specific seed accounts rather than very large ones

## Advanced Strategies

**Tiered Seed Approach:**

1. **Tier 1 (High Priority):** 2-3 accounts with 100% audience alignment (niche publications)
2. **Tier 2 (Core):** 3-5 accounts with 80%+ alignment (vertical-specific thought leaders)
3. **Tier 3 (Expansion):** 2-3 accounts with 60%+ alignment (adjacent verticals, complementary tools)

This ensures high-quality core prospects while allowing for discovery of adjacent markets.

**Lookalike + People Search:**
- Find seed accounts using lookalike audience discovery
- Note the companies their followers work at
- Use LinkedIn People Search to find similar people at those companies
- Combines audience-based discovery with systematic targeting

**Competitor + Thought Leader Mix:**
- Extract followers from competitor accounts
- Extract followers from industry thought leaders
- Cross-reference overlapping followers (strongest ICP indicators)
