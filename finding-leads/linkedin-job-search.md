# LinkedIn Job Search (Hiring Signals)

Find decision-makers at companies that are actively hiring. LinkedIn Job Search identifies growth-stage companies through job postings, resolves company profiles, and extracts the most senior decision-maker at each company.

## How It Works

Job search is not a standalone search type-  it is integrated into LinkedIn Content Search as the **Hiring Signals** intent category. When you include Hiring Signals in your selected intent categories, additional settings appear for configuring the job search.

### 1. AI-Generated Role Targets

AutoReach generates job title keywords tailored to your offer using AI, based on your offer description, name, and target audience. Additional niche titles are generated from industry-specific terminology.

**Example for a Sales Automation Platform:**
- "Sales operations manager"
- "Sales pipeline builder"
- "CRM implementation consultant"
- "VP of sales operations"

**Example for HR Analytics:**
- "People analytics lead"
- "HR metrics manager"
- "Head of people operations"

### 2. Job Listing Discovery

For each role target, AutoReach searches LinkedIn Jobs filtered by your offer's preferred locations. Job data includes the job title, company name, location, workplace type (Remote/Hybrid/On-site), and posting date.

### 3. Company Resolution

After collecting jobs across all role targets, AutoReach deduplicates by company and fetches full company profiles-  including industry, staff count, headquarters location, website, and specialties. The list is capped at your configured **Max Companies** limit.

### 4. Decision-Maker Discovery

For each company, AutoReach finds employees and selects the **most senior decision-maker**-  prioritizing C-suite, founders, and VPs. One decision-maker per company is extracted to ensure focused outreach.

### 5. Lead Enrichment and Scoring

Each discovered decision-maker is added to your lead database and queued for enrichment and scoring based on your enrichment settings.

## Competitor Customer Detection

When your offer has competitors configured, LinkedIn Job Search automatically discovers **competitor customers**-  companies posting jobs that require experience with competing products. Decision-makers at these companies are extracted and tagged with elevated priority.

This runs automatically as part of the content search pipeline when **Hiring Signals** is enabled and competitors are defined.

## Search Parameters

These are configured within the LinkedIn content search settings when the Hiring Signals intent category is selected:

| Parameter | Default | Description |
|---|---|---|
| **Max Jobs Per Role** | 100 | Max job postings to collect per role target (slider: 25–200) |
| **Max Companies** | 30 | Max companies to process (slider: 10–50) |

## Best Practices

1. **Rely on AI-generated titles.** The AI generates domain-specific role targets based on your offer. These yield higher-quality matches than generic titles.

2. **Combine with other intent categories.** Run **Hiring Signals** alongside **Pain Points** or **Solution Seeking** in a single content search to maximize coverage.

3. **Monitor company profiles.** The resolved company data (industry, staff count, funding) helps validate whether a company is in your ICP before outreach.

4. **Enable Buyer Expansion.** Turn on daily recurring to catch new job postings and hiring activity continuously.

5. **Leverage competitor customer detection.** If you have competitors defined in your offer, this feature automatically finds companies already paying for solutions like yours.

## Example Workflow

**Offer:** "People analytics and HR intelligence platform"

**AI generates role targets:**
- "Head of People Operations"
- "People Analytics Manager"
- "HR Technology Lead"

**Result:** Job search finds job postings across the roles, identifies the hiring companies, resolves their profiles (industry, size, HQ), and extracts the most senior decision-maker at each. Competitor customer detection also finds companies hiring for roles requiring experience with competing HR platforms.

## Troubleshooting

**Getting too many irrelevant job postings?**
- Reduce the Max Jobs per Role slider to limit volume
- Reduce the Max Companies slider to focus on the best matches

**Decision-makers don't seem relevant?**
- AutoReach prioritizes C-suite and VPs. Combine with [LinkedIn People Search](linkedin-people-search.md) to find specific roles at companies discovered through job search.

**Not finding enough companies?**
- Increase the Max Jobs per Role slider
- Check if your target industry actively posts on LinkedIn Jobs

## Next Steps

- **[LinkedIn People Search](linkedin-people-search.md)**: Find additional decision-makers at companies discovered through job search
- **[LinkedIn Content Search](linkedin-content-search.md)**: Discover professionals discussing challenges related to hiring activity
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile and company data
