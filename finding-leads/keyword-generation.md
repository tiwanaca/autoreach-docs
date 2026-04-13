# Keyword Generation

AutoReach uses AI to generate targeted search queries from your offer definition. Keywords power both one-time and recurring daily searches across X and LinkedIn, keeping your prospect pipeline full without manual effort.

## How It Works

Keyword generation is a multi-layered system. For X, it produces simple keywords, structured intent query clusters, competitor keywords, and niche jargon. For LinkedIn, it produces search queries organized by intent category. Each layer is optimized for the platform's search capabilities.

### Where Keywords Come From

AutoReach derives keywords from multiple elements of your offer:

- **Target audience** details like titles, roles, and industries
- **Pain points** described in your offer
- **Search signals** you provide as natural language phrases
- **Competitors** — competitor-specific keywords are generated and merged separately
- **Industry jargon** — niche terminology, insider terms, and community names

## X Keyword Generation

X keyword generation has four components:

### Simple Keywords (`generateKeywords`)

Generates **15-25 keywords** (capped at 25), plus a 6-8 term OR-joined search query string. Keywords are short conversational phrases:

- 2-3 words ideal, 4 words max
- First-person conversational style ("my X keeps breaking", "need a better X")
- Two-word phrases are auto-quoted for exact matching; 3+ word phrases are left unquoted to avoid over-restricting results

The AI draws from up to 8 categories: conversational first-person, pain points, solution-seeking, hiring/growth signals, tool evaluation, company growth signals, competitor alternatives, and professional identity. Categories 4-8 are conditional — skipped if they don't fit the offer.

### Intent Query Clusters (`generateIntentQueries`)

A separate AI call that generates **full Twitter search queries with operators** (`OR`, `"quoted phrases"`, `-exclusions`, `min_faves:2`). This is where search operators actually live — simple keywords do not contain operators.

The AI selects 3-6 relevant intent categories and generates 2-6 queries per cluster:

| Intent Category | What It Targets |
|---|---|
| `operational_pain` | Day-to-day frustrations and inefficiencies |
| `budget_pressure` | Cost concerns and budget constraints |
| `hiring_scaling` | Growth challenges and team scaling |
| `buying_evaluation` | Actively comparing or evaluating solutions |
| `competitor_switch` | Switching away from or frustrated with competitors |
| `growth_signals` | Expansion, new markets, scaling needs |
| `security_compliance` | Regulatory, security, or compliance concerns |
| `vertical_specific` | Industry-specific pain points |
| `professional_identity` | Role-based challenges and aspirations |

### Competitor Keywords (`generateCompetitorKeywords`)

A **synchronous function** (no AI call). For each competitor, generates 10 keyword variants:
- "switching from [competitor]"
- "[competitor] alternative"
- "replacing [competitor]"
- etc.

Plus a 5-clause OR search query with fully quoted phrases. The top 3 keywords per competitor are injected into the main keyword array.

### Niche Jargon (`generateNicheJargon`)

A separate AI call that generates insider terminology:
- **Insider terms** — tools, certifications, acronyms, conferences (5-10 items)
- **Headline keywords** — job titles (5-8)
- **Community names** — newsletters, Slack groups, communities (3-5)
- **Twitter search queries** — ready-to-use OR queries with operators (5-8)
- **LinkedIn title searches** — title filter terms for LinkedIn People Search (5-8)

## LinkedIn Keyword Generation

LinkedIn generates **up to 20 keywords** plus **10-15 search queries** organized by intent.

### Search Query Format

LinkedIn queries are short natural phrases (3-5 words) without search operators — LinkedIn's content search doesn't support them. Each query is a `SearchQuery` object with:
- `query` — the search text
- `intent` — the intent category it belongs to
- `description` — what the query is designed to surface

### LinkedIn Intent Categories

The AI generates queries across these intents (2-3 queries per category):

| Intent | Description |
|---|---|
| `pain_points` | Operational challenges and frustrations |
| `hiring_signals` | Recruiting, team expansion, skill gaps |
| `solution_seeking` | Evaluating tools, asking for recommendations |
| `buying_intent` | Budget allocation, vendor selection |
| `growth_signals` | Revenue growth, market expansion |
| `professional_identity` | Role-based challenges |
| `competitor_switching` | Moving away from competitors |
| `cost_pressure` | Cost reduction, budget constraints |
| `compliance_regulatory` | Regulatory and compliance needs |
| `tool_evaluation` | Comparing or testing tools |

When you start a LinkedIn content search, you select which intent categories to include. Only queries matching your selected categories are used.

### Key Differences from X

- No search operators (LinkedIn doesn't support them)
- No competitor keyword injection
- Queries are professional/B2B-oriented phrases
- Filtered by user-selected intent categories at search time

## Previewing Keywords

You can preview generated keywords before running a search. The keyword generator is available when configuring X tweet searches and LinkedIn content searches. Previewing lets you review the AI-generated keywords and queries without starting a search, so you can adjust your offer description or search signals if needed.

## Keyword Overrides

For X searches, you can provide your own keywords and search query at search start time to skip AI generation entirely. There is no way to edit keywords on an already-saved search -- overrides are applied at search creation only.

LinkedIn searches always generate queries server-side. You cannot provide custom queries directly.

## Recurring Keyword Regeneration

When daily recurring searches are enabled, keywords are **regenerated fresh** on each run (not reused):

**X recurring regeneration:**
- Calls `regenerateKeywords()` with the previous keywords and query
- The AI prompt includes a "KEYWORD ROTATION" block listing all previous keywords, instructing it to avoid repeating them
- Falls back to existing keywords if regeneration fails
- The search record's keywords and query are updated automatically

**LinkedIn recurring regeneration:**
- Calls `regenerateLinkedInQueries()` with previous queries
- Same rotation pattern: prompt includes previous queries, instructs different angles
- Result is filtered by the search's configured intent categories
- Niche jargon queries (up to 5) are appended after regeneration
- Falls back to `generateLinkedInKeywords()` on error

The recurring search scheduler runs every hour. Searches re-trigger only when last run was 24+ hours ago.

## Best Practices

1. **Review AI-generated keywords.** AutoReach generates solid starting points, but you know your market best. Override where it makes sense.

2. **Include industry jargon in your offer.** Niche terminology in your offer description, pain points, and search signals produces better AI-generated keywords.

3. **Vary intent signals.** Mix pain-focused ("struggling with"), growth-focused ("scaling"), and evaluation-focused ("comparing") to cover different buyer stages.

4. **Let recurring searches regenerate.** Keyword rotation prevents stale results and captures different prospect segments over time.

5. **Combine with other discovery methods.** Keywords complement people search, lookalike audiences, and lead pool matching. Use them together for broader coverage.

## Example Workflow

**Your Offer:** "Financial planning and analysis (FP&A) software for growing SaaS companies"

**X Simple Keywords (15-25):**
- "financial planning SaaS"
- "FP&A forecasting"
- "budget cycle manual"
- "revenue forecast inaccurate"

**X Intent Clusters:**
- **operational_pain:** `"spreadsheet" OR "manual" "financial model" min_faves:2 -crypto`
- **buying_evaluation:** `"FP&A tool" OR "forecasting software" "evaluating" min_faves:2`
- **budget_pressure:** `"budget process" OR "budget cycle" "too slow" min_faves:2`

**X Competitor Keywords:**
- "switching from Anaplan"
- "Adaptive Insights alternative"

**LinkedIn Queries:**
- (pain_points) "financial planning manual process"
- (solution_seeking) "FP&A software recommendation"
- (growth_signals) "scaling finance team"
- (hiring_signals) "hiring FP&A analyst"

**Result:** Multi-layered queries across both platforms, running daily with fresh keyword rotation to surface CFOs, FP&A leaders, and finance operators.

## Troubleshooting

**Getting too many irrelevant results?**
- Your keywords may be too broad. Override with more specific terms.
- Add exclusion terms to the search (default exclusions are minimal: `giveaway`, `retweet`, `airdrop`).
- Focus on intent clusters rather than simple keywords for better precision.

**Not getting enough results?**
- Broaden search terms or include synonym variations.
- Increase the days back setting on the search to look further into the past.
- Verify that your target audience actively discusses these topics online.

**Keywords seem too generic?**
- The niche jargon generator adds insider terminology. Make sure your offer includes enough domain context for it to work with.
- Override with your own validated keywords at search start.

**How many keywords are generated?**
- X: 15-25 simple keywords + 3-6 intent clusters (2-6 queries each) + competitor keywords + niche jargon
- LinkedIn: up to 20 keywords + 10-15 search queries

## Next Steps

- **[X Tweet Search](tweet-search.md)**: Use your generated keywords to find high-intent prospects on X
- **[LinkedIn Content Search](linkedin-content-search.md)**: Apply keywords to discover decision-makers on LinkedIn
