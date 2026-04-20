# Keyword Generation

AutoReach uses AI to generate targeted search queries from your offer definition. Keywords power both one-time and recurring daily searches across X and LinkedIn, keeping your prospect pipeline full without manual effort.

## How It Works

Keyword generation is a multi-layered system. For X, it produces simple keywords, structured intent query clusters, competitor keywords, and niche jargon. For LinkedIn, it produces search queries organized by intent category. Each layer is optimized for the platform's search capabilities.

### Where Keywords Come From

AutoReach derives keywords from multiple elements of your offer:

- **Target audience** details like titles, roles, and industries
- **Pain points** described in your offer
- **Competitors**-  competitor-specific keywords are generated and merged separately
- **Industry jargon**-  niche terminology, insider terms, and community names

## X Keyword Generation

X keyword generation has four components:

### Simple Keywords

Short conversational phrases in first-person style ("my X keeps breaking", "need a better X") designed to match how real people talk about their problems on X.

### Intent Query Clusters

Structured search queries organized by intent category. The AI selects the most relevant categories for your offer:

| Intent Category | What It Targets |
|---|---|
| Operational Pain | Day-to-day frustrations and inefficiencies |
| Budget Pressure | Cost concerns and budget constraints |
| Hiring & Scaling | Growth challenges and team scaling |
| Buying Evaluation | Actively comparing or evaluating solutions |
| Competitor Switch | Switching away from or frustrated with competitors |
| Growth Signals | Expansion, new markets, scaling needs |
| Security & Compliance | Regulatory, security, or compliance concerns |
| Vertical Specific | Industry-specific pain points |

### Competitor Keywords

For each competitor in your offer, AutoReach generates keywords like "switching from [competitor]", "[competitor] alternative", and similar variations.

### Niche Jargon

Industry-specific insider terminology-  tools, certifications, acronyms, conferences, job titles, and community names that your target audience uses.

## LinkedIn Keyword Generation

LinkedIn queries are short professional phrases without search operators-  optimized for LinkedIn's content search.

### LinkedIn Intent Categories

The AI generates queries across these intents:

| Intent | Description |
|---|---|
| Pain Points | Operational challenges and frustrations |
| Hiring Signals | Recruiting, team expansion, skill gaps |
| Solution Seeking | Evaluating tools, asking for recommendations |
| Buying Intent | Budget allocation, vendor selection |
| Growth Signals | Revenue growth, market expansion |

All intent categories are searched automatically when you start a LinkedIn content search.

### Key Differences from X

- Queries are professional/B2B-oriented phrases without search operators
- All intent categories are searched automatically

## Previewing Keywords

You can preview generated keywords before running a search. The keyword generator is available when configuring X tweet searches and LinkedIn content searches. Previewing lets you review the AI-generated keywords and queries without starting a search, so you can adjust your offer description or pain points if needed.

## Keyword Overrides

For X searches, you can provide your own keywords and search query at search start time to skip AI generation entirely.

LinkedIn searches always generate queries server-side. You cannot provide custom queries directly.

## Recurring Keyword Regeneration

When Buyer Expansion is enabled, keywords are **regenerated fresh** on each daily run-  not reused. The AI references previous keywords to ensure variation and avoid repeating the same searches. If regeneration fails, existing keywords are used as a fallback.

## Best Practices

1. **Review AI-generated keywords.** AutoReach generates solid starting points, but you know your market best. Override where it makes sense.

2. **Include industry jargon in your offer.** Niche terminology in your offer description and pain points produces better AI-generated keywords.

3. **Vary intent signals.** Mix pain-focused ("struggling with"), growth-focused ("scaling"), and evaluation-focused ("comparing") to cover different buyer stages.

4. **Let recurring searches regenerate.** Keyword rotation prevents stale results and captures different prospect segments over time.

5. **Combine with other discovery methods.** Keywords complement people search, lookalike audiences, and lead pool matching. Use them together for broader coverage.

## Example Workflow

**Your Offer:** "Financial planning and analysis (FP&A) software for growing SaaS companies"

**X Keywords might include:**
- "financial planning SaaS"
- "FP&A forecasting"
- "budget cycle manual"
- "revenue forecast inaccurate"
- "switching from Anaplan"
- "Adaptive Insights alternative"

**X Intent Clusters might include:**
- **Operational Pain:** queries about manual spreadsheet processes
- **Buying Evaluation:** queries about evaluating FP&A tools
- **Budget Pressure:** queries about slow budget cycles

**LinkedIn Queries might include:**
- (Pain Points) "financial planning manual process"
- (Solution Seeking) "FP&A software recommendation"
- (Growth Signals) "scaling finance team"
- (Hiring Signals) "hiring FP&A analyst"

**Result:** Multi-layered queries across both platforms, running daily with fresh keyword rotation to surface CFOs, FP&A leaders, and finance operators.

## Troubleshooting

**Getting too many irrelevant results?**
- Your keywords may be too broad. Override with more specific terms on X.
- Add exclusion terms to the search.
- Focus on intent clusters rather than simple keywords for better precision.

**Not getting enough results?**
- Broaden search terms or include synonym variations.
- Increase the days back setting on the search to look further into the past.
- Verify that your target audience actively discusses these topics online.

**Keywords seem too generic?**
- Make sure your offer includes enough domain context-  industry jargon, specific pain points, and competitor names help the AI generate more targeted keywords.
- Override with your own validated keywords at search start (X only).

## Next Steps

- **[X Tweet Search](tweet-search.md)**: Use your generated keywords to find high-intent prospects on X
- **[LinkedIn Content Search](linkedin-content-search.md)**: Apply keywords to discover decision-makers on LinkedIn
