# LinkedIn Job Search

Find decision-makers at companies that are actively hiring. LinkedIn Job Search identifies growth-stage companies through job postings, resolves company profiles, and extracts the most senior decision-maker at each company.

## How It Works

Job search is not a standalone search type — it is integrated into LinkedIn Content Search and triggers when you include **hiring_signals** in your selected intent categories.

### Stage 1: AI-Generated Role Targets

AutoReach generates 3-5 job title keywords tailored to your offer using AI. The prompt analyzes your offer description, name, and target audience to produce domain-specific titles.

Additionally, niche targets are generated from insider terminology — LinkedIn title searches and insider terms from your offer's jargon profile (up to 5 + 3 additional niche terms). All targets are deduplicated before searching.

**Example for a Sales Automation Platform:**
- "Sales operations manager"
- "Sales pipeline builder"
- "CRM implementation consultant"
- "VP of sales operations"

**Example for HR Analytics:**
- "People analytics lead"
- "HR metrics manager"
- "Head of people operations"

### Stage 2: Job Listing Discovery

For each role target, AutoReach searches LinkedIn Jobs via LinkedIn's API.

**Search parameters:**
- **Keywords:** The AI-generated role targets
- **Location:** Resolved from your offer's preferred locations (geo IDs)
- **Time filter:** Controls posting recency

**Time filter options:**

| Filter | Value | Description |
|---|---|---|
| 24 hours | `r86400` | Very fresh postings |
| 1 week | `r604800` | Last week's postings |
| 1 month *(default)* | `r2592000` | Past 30 days |
| Any time | no filter | All postings |

**Data extracted per job posting:**
- Job ID and title
- Company name
- Location and workplace type (Remote/Hybrid/On-site — parsed from location string)
- Posted timestamp and relative time
- Easy Apply flag

### Stage 3: Company Deduplication

After collecting jobs across all role targets, AutoReach deduplicates by company name (case-insensitive). When multiple job postings exist for the same company, the most recently posted one is kept. The list is then capped at the maximum companies limit (default: 30).

### Stage 4: Company Profile Resolution

For each deduplicated company, AutoReach fetches the full company profile from LinkedIn's API (trying up to 3 URL variants for resilience). Extracted data:

- Company name, description, and tagline
- Industry classification and company type
- Headquarters location and confirmed office locations
- Staff count and staff count range
- Website URL and founding year
- Specialties, logo, and follower count

### Stage 5: Decision-Maker Discovery

For each company, AutoReach searches for employees using LinkedIn's API (with a `currentCompany` filter) and returns up to 10 employees. These are ranked by **seniority scoring**:

| Role | Score |
|---|---|
| Founder / Co-Founder | 100 |
| CEO | 95 |
| CTO, CFO, COO, CMO, CRO | 90 |
| Owner | 85 |
| Partner | 80 |
| VP, SVP, EVP | 75 |
| Director | 60 |
| Head | 55 |
| Manager | 40 |
| Lead | 35 |

The **single highest-scoring person** is selected as the decision-maker for that company. One decision-maker per company, not multiple.

**Experience verification:** For the top 3 candidates, AutoReach fetches their full profile and verifies they currently work at the company. If all 3 fail verification, the top-ranked unverified candidate is used as a fallback — the company filter is reliable, so verification is a safety net.

### Stage 6: Lead Enrichment and Scoring

Each discovered decision-maker is added to your lead database and queued for enrichment and scoring based on your enrichment settings.

## Competitor Customer Detection

When your offer has competitors configured, LinkedIn Job Search is also used to discover **competitor customers** automatically. The flow:

1. Each competitor name is used as a job search keyword
2. Companies posting jobs requiring experience with the competitor are identified as likely customers of that competitor
3. Companies that ARE the competitor are filtered out
4. Decision-makers at these companies are extracted and tagged as a competitor's customer with elevated priority
5. Capped at 5 competitors searched, 15 companies per competitor

This runs automatically as part of the content search pipeline when **Hiring Signals** is enabled and competitors are defined.

## Search Parameters

| Parameter | Default | Description |
|---|---|---|
| **Max Jobs Per Role** | 100 | Max job postings to collect per role target |
| **Max Companies** | 30 | Max deduplicated companies to process |
| **Daily Recurring** | disabled | Enable automatic daily re-runs |

These are configured via the LinkedIn content search settings alongside the hiring signals intent category.

## Best Practices

1. **Rely on AI-generated titles.** The AI generates domain-specific role targets based on your offer. These yield higher-quality matches than generic titles.

2. **Use recent time filters.** Fresh postings (24h or 1 week) indicate active hiring and receptive decision-makers.

3. **Combine with other intent categories.** Run **Hiring Signals** alongside **Pain Points** or **Solution Seeking** in a single content search to maximize coverage.

4. **Monitor company profiles.** The resolved company data (industry, staff count, funding) helps validate whether a company is in your ICP before outreach.

5. **Enable recurring searches.** Turn on daily recurring to catch new job postings and hiring activity continuously.

6. **Leverage competitor customer detection.** If you have competitors defined in your offer, this feature automatically finds companies already paying for solutions like yours.

## Example Workflow

**Offer:** "People analytics and HR intelligence platform"

**AI generates role targets:**
- "Head of People Operations"
- "People Analytics Manager"
- "HR Technology Lead"

**Time filter:** 1 week

**Result:** Job search finds 85 job postings across the 3 roles, deduplicates to 30 companies, resolves their profiles (industry, size, HQ), and extracts the most senior decision-maker at each. Competitor customer detection also finds 12 companies hiring for roles requiring experience with competing HR platforms.

## Troubleshooting

**Getting too many irrelevant job postings?**
- The AI generates niche titles, but you can reduce the max jobs per role to limit volume
- Use 24-hour or 7-day time filters instead of 1 month
- Reduce the max companies to focus on the best matches

**Decision-makers extracted don't seem relevant?**
- Seniority scoring prioritizes C-suite and VPs. If you want mid-level contacts, the scoring may not match your needs.
- Experience verification ensures the person actually works at the company, but the search may return people in tangential roles.
- Combine with [LinkedIn People Search](linkedin-people-search.md) to find specific roles at companies discovered through job search.

**Not finding enough companies?**
- Increase the max jobs per role to collect more postings
- Use "any time" filter to search all historical postings
- Check if your target industry actively posts on LinkedIn Jobs

## Next Steps

- **[LinkedIn People Search](linkedin-people-search.md)**: Find additional decision-makers at companies discovered through job search
- **[LinkedIn Content Search](linkedin-content-search.md)**: Discover professionals discussing challenges related to hiring activity
- **[Enrichment Pipeline](../enrichment/pipeline.md)**: See how discovered leads get enriched with full profile and company data
