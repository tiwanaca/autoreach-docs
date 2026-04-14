# Lookalike Audience Discovery

Find high-quality prospects by identifying influencers and accounts whose followers match your ICP. AutoReach uses AI-powered web search to discover seed accounts, then extracts and scores their followers as leads.

## How It Works

Lookalike Audience Discovery follows three steps:

### 1. Discover Seed Accounts

AutoReach uses AI-powered web search to find accounts whose audiences overlap with your target market. Based on your offer, it searches for relevant accounts, verifies them against live platform APIs, and returns a curated list of seed accounts.

Discovery works on both X and LinkedIn from the same interface.

**What it searches for:**

The AI searches across multiple audience categories:
- **Industry publications**-  newsletters, media outlets, trade publications
- **Professional communities**-  groups, forums, community accounts
- **Vendor/competitors**-  competitor accounts and adjacent vendors
- **Thought leaders**-  executives, analysts, and domain experts
- **Vertical-specific**-  niche accounts specific to your industry

If your offer specifies preferred locations, the AI prioritizes accounts with audiences in your target regions.

### 2. Extract Followers

Once seed accounts are saved, their followers are extracted through the standard extraction pipelines:

- **X seeds:** Followers are extracted and queued for enrichment
- **LinkedIn seeds:** A people search is created with a follower filter

In the **manual flow**, you discover seeds from the Lookalike Audiences page, save them to your library, then separately trigger extraction via the "From a Lookalike" option. Under **Autopilot**, extraction is fully automatic after discovery.

### 3. Score and Add Leads

Every extracted follower goes through the standard enrichment and scoring pipeline. All extracted followers are added as leads and scored by buyer intelligence like any other source.

## Search Options

When starting a lookalike search, you configure:

- **Offer**-  select the offer that provides ICP context, location, and competitors
- **Channel**-  choose X or LinkedIn
- **Platform account**-  select your connected X or LinkedIn account
- **Profile URL** (optional)-  enter a profile URL for profile-based discovery instead of offer-based

**Two discovery modes:**
- **By Offer:** Select an offer-  finds seeds matching your offer's ICP, domain, and audience
- **By Profile URL:** Enter a profile URL-  finds accounts similar to a specific person

## Available Actions

From the Lookalike Audiences page, you can:

- **Estimate cost**-  preview the estimated cost before running a search
- **Search for seeds**-  discover seed accounts with real-time progress updates
- **Save accounts**-  save one or more discovered accounts to your library
- **Browse saved accounts**-  view your saved accounts with pagination and filtering
- **Delete accounts**-  remove individual or multiple saved accounts

## Automatic Rotation Under Autopilot

When Autopilot is enabled, seed accounts rotate automatically:

1. When a seed is exhausted, Autopilot discovers **new** seed accounts via web search
2. New seeds are saved and extraction begins automatically
3. Previously used accounts are tracked to avoid duplicates
4. If the AI can't find new relevant accounts, it broadens its search to find lesser-known accounts
5. If discovery stalls, you receive a notification

This means Autopilot actively discovers fresh seed accounts-  it does not just re-extract from existing ones.

## Cost Estimation

Before running a search, use the cost estimation feature to preview estimated costs for the web search AI calls.

## Best Practices

1. **Mix account types.** Combining publications, communities, and individual thought leaders produces more diverse and well-rounded audiences.

2. **Prioritize engaged audiences.** Accounts with high engagement rates tend to have more active, reachable followers.

3. **Use both platforms.** Run lookalike discovery on both X and LinkedIn to maximize coverage. The extraction pipelines differ but both produce scored leads.

4. **Monitor lead quality.** Track response rates from lookalike-sourced leads. If quality drops, your seed accounts may need adjustment.

5. **Combine with other methods.** Lookalike audiences complement content search and people search. Use them together for best coverage.

6. **Let Autopilot handle rotation.** Manual seed management works, but Autopilot's automatic rotation with escalating diversity prompts keeps the pipeline flowing without intervention.

## Example Workflow

**Offer:** "API platform for payment processing"

**Step 1:** AutoReach web-searches for fintech publications, developer community accounts, API-focused thought leaders, and competitor ecosystems on X. Returns 10 verified seed accounts with 1,000+ followers each.

**Step 2:** You save the 6 most relevant seeds. Follower extraction begins-  200 followers per seed, totaling ~1,200 profiles.

**Step 3:** Each follower is enriched and scored. CTOs, engineering leaders, and technical founders who match your ICP surface as active leads. The rest land in Monitor or Poor Fit.

**Under Autopilot:** When the 6 seeds are exhausted, the scheduler automatically discovers 10 new seed accounts and creates fresh extractions. This repeats continuously.

## Troubleshooting

**Not finding relevant seed accounts?**
- Make sure your offer description includes relevant domain keywords
- Check that your target audience is active on the platform you are searching
- Broaden your offer's pain points or audience definition to give the AI more to work with
- Try profile-based discovery with a known relevant account

**Low ICP match rate on extracted followers?**
- Review whether the seed accounts truly align with your ICP
- Refine your ICP definition, particularly pain points and target audience
- Try targeting more niche, specialized accounts rather than very broad ones

**Seed accounts getting exhausted?**
- This is expected. Previously extracted followers are not re-extracted
- Under Autopilot, new seed accounts are discovered automatically
- You can also add seed accounts manually to increase flow

**Getting prospects with missing profiles?**
- Some followers do not maintain active profiles. These are filtered out during enrichment and are not counted against your lead totals

**Autopilot stall notification?**
- After 3+ consecutive misses finding new seeds, you'll receive a notification
- Review and update your offer description to give the AI fresh context
- Consider switching channels (X ↔ LinkedIn) if one platform is exhausted

## Next Steps

- **[Continuous Operations](../autopilot/continuous-operations.md)**: Automate lookalike discovery with Autopilot's daily expansion
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: Understand how extracted followers get enriched and scored
