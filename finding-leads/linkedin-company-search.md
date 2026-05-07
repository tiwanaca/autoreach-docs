# LinkedIn Company Search (By Company)

Find decision-makers by searching for companies that match a description, then extracting one top-ranked decision-maker from each. Use **By Company** when you know the *type* of company you want to reach, but not the specific people yet.

## How It Works

LinkedIn Company Search is a two-step pipeline:

1. **Find companies** matching your descriptors (e.g., "Lead Generation Agency", "B2B SaaS Sales Tooling", "Boutique Recruiting Firm")
2. **Find the top decision-maker at each company** based on seniority and offer-relevance

The result is a focused list of one prospect per company, not dozens of irrelevant employees.

## Where to Start a Search

1. Go to **Leads** and click **Add Lead**
2. Choose **LinkedIn** as the platform
3. Select your account and offer
4. Click **By Company**

## Configuring the Search

### Company Descriptors

Descriptors are short phrases that describe the *type* of company you want to reach. Examples:

- "Lead Generation Agency"
- "B2B SaaS Sales Tooling"
- "Outbound Sales Consultancy"
- "Mid-Market Recruiting Firm"

Two ways to add descriptors:

- **Generate from offer**: Click **Regenerate from offer** to have AI suggest descriptors based on your offer's description, target audience, and pain points. You can refine the suggestions before running the search.
- **Add manually**: Type a descriptor and press Enter (or click the + button) to add it.

> **Tip:** Mix broad descriptors ("B2B SaaS") with niche ones ("PLG analytics startup") to balance volume and precision.

### Max Companies

Use the slider to set how many companies to process. Each company contributes one decision-maker, so this is also the maximum number of leads you'll add from the search.

| Setting | Range | Default |
|---|---|---|
| Max Companies | 10-100 | 50 |

### Buyer Expansion (Daily Autopilot)

Toggle **Buyer Expansion** to re-run each descriptor daily. New companies that appear over time (newly-listed, recently-funded, expanded into the territory) are automatically discovered and turned into leads.

When enabled, AutoReach:

1. Re-runs each descriptor every 24 hours
2. Adds the top decision-maker from each newly-discovered company
3. Marks descriptors as exhausted when they stop returning fresh companies
4. Auto-disables Buyer Expansion once all descriptors are exhausted

### Cost Estimation

Before running, the cost estimator shows expected AI and search costs for your settings.

## What Gets Returned

For each matched company, the top-ranked decision-maker is added as a lead with:

- Name, headline, profile URL, location
- Company name and basic company data
- The descriptor that matched the company (visible on the lead's source data)

Leads are queued for enrichment and scoring like any other source.

## How "Top Decision-Maker" Is Picked

For each company, AutoReach pulls the employee list and ranks people by seniority. Founders, co-founders, and C-suite rank highest, followed by VPs, Directors, Heads of, and Managers. The single highest-ranked match is added as the lead.

This is fully automatic. You do not configure roles directly for By Company search. To target specific roles at the same companies later, layer a [LinkedIn People Search](linkedin-people-search.md) on top.

## Best Practices

1. **Use specific descriptors.** "B2B SaaS sales analytics platform vendor" produces sharper matches than "software company."
2. **Mix tiers.** A handful of broad descriptors plus a handful of niche ones gives you both reach and precision.
3. **Write a detailed offer.** AI descriptor generation pulls from your offer's description, target audience, and pain points. Vague offers produce vague descriptors.
4. **Enable Buyer Expansion for ongoing discovery.** New companies pop up constantly. Daily re-runs catch them without manual effort.
5. **Combine with By Role.** By Company finds one person per company. By Role finds many people across many companies. Use them together to cover both axes.

## Example Workflow

**Offer:** "Outbound infrastructure for B2B SaaS RevOps teams"

**AI-generated descriptors:**
- "B2B SaaS RevOps consultancy"
- "Outbound sales agency"
- "Mid-market sales tooling vendor"
- "PLG analytics startup"

**Result:** AutoReach finds 30 companies across these descriptors, picks the top RevOps or Sales leader at each, and adds them as leads. Buyer Expansion re-runs daily, surfacing newly-active firms.

## Hiring Signals vs By Company

By Company and **Hiring Signals** (inside [LinkedIn Content Search](linkedin-content-search.md)) both produce one decision-maker per company, but they use different selection methods:

| Feature | Selection Method | When to Use |
|---|---|---|
| **By Company** | Match company by descriptor, pick best-fit decision-maker | You know the type of company you want |
| **Hiring Signals** | Find companies hiring for relevant roles, pick best-fit decision-maker | You want timing-driven leads at growth-stage companies |

Use them together. By Company gives you a steady base; Hiring Signals adds time-sensitive opportunities.

## Troubleshooting

**Few or no companies returned?**
- Descriptors may be too narrow. Add broader synonyms.
- Your geo filter may be limiting matches. Try widening the offer's preferred locations.
- LinkedIn may have throttled the account briefly. Wait and retry.

**Decision-makers don't look right?**
- AutoReach picks the most senior person at each company. If you need a specific role (e.g., RevOps Manager), run [LinkedIn People Search](linkedin-people-search.md) on the discovered companies instead.

**Companies look duplicated within a single search?**
- Each search execution deduplicates companies as it processes them. The same company will not be added twice within one run.

## Next Steps

- **[LinkedIn People Search](linkedin-people-search.md)**: Find multiple roles per company once you've identified the right targets
- **[LinkedIn Job Search (Hiring Signals)](linkedin-job-search.md)**: Time-sensitive company discovery from job postings
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: How discovered leads get enriched and scored
