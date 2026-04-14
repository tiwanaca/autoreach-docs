# Signal Detection

AutoReach detects dozens of signals from a lead's social activity, profile history, and company information. These signals power your buyer intelligence scoring and help identify who's ready to buy.

## What Are Signals?

Signals are data points that indicate a lead is interested, actively buying, or urgently needs your solution. Think of them as breadcrumbs of intent: evidence that someone is thinking about, evaluating, or implementing a solution like yours.

**Examples:**

- Tweet: "Just switched from Salesforce to HubSpot - best decision ever"
- LinkedIn post: "We're hiring 10 salespeople this year"
- Career move: Started new job 3 weeks ago (recent hire)
- Profile mention: Lists experience with "Slack API integration"

## Explicit Intent Signals

These are direct mentions or statements showing buying intent:

### Asked for Recommendation

Lead explicitly asked for recommendations on a product/service category.

**Example:** "Anyone have a good recommendation for customer data platforms? We're evaluating options."

### Switching From Competitor

Lead mentioned they are switching away from a competitor. This is one of the strongest intent signals.

**Example:** "Finally ditching Mailchimp for Klaviyo. Should've done this years ago."

### Looking for Alternative

Lead is actively searching for an alternative to their current solution.

**Example:** "Looking for an alternative to our current project management tool. What are people using now?"

### Complained About Current Tool

Lead complained about their current tool or process (pain point expressed).

**Example:** "Our CRM is so slow. Takes 30 seconds just to load a contact. Killing our team's productivity."

### Tool Mention

Lead mentioned using or considering a competitor or similar tool.

**Example:** "Integrating with Zapier this week" or "Testing Stripe for payments"

## Company-Level Signals

These signals indicate something major is happening at the company level:

### Funding

Company announced a new funding round.

**Example:** "Proud to announce Series B funding: $25M led by Sequoia"

### Product Launch

Company launched a new product or major feature.

**Example:** "Today we're launching the beta of Product V2. Total redesign based on your feedback."

### Mergers and Acquisitions

Company acquired another company or was acquired.

**Example:** "Big news: We've acquired TechStartup to expand our platform capabilities"

### Cost Cutting

Company announced layoffs, consolidation, or cost reduction initiatives.

**Example:** "Streamlining our tech stack to focus on core tools. Consolidating vendors."

### IPO Filing

Company filed for IPO or public markets.

**Example:** "We're going public! S-1 filing effective today."

### Geographic Expansion

Company is expanding to a new geographic market.

**Example:** "Excited to announce our expansion into APAC. Opening offices in Singapore and Sydney."

## Engagement Signals

These signals show active engagement with your domain:

### Competitor Engagement

Lead engaged with (liked, commented on) content from competitor companies.

**Example:** Lead liked a post from your competitor about their product

### Engagement Pattern

Lead has high engagement on posts related to your category.

**Example:** Consistently comments on automation/AI posts, high like ratio

### Own Post Engagement

Lead engaged with YOUR posts — this is an inbound signal, they came to you. AutoReach detects different types of engagement on each platform:

**X (Twitter):** replies, likes, retweets, and new follows

**LinkedIn:** reactions, comments, mentions, connection requests, and profile views

Deeper engagement (replies, comments, mentions) and repeat engagement (interacting with multiple posts) are weighted more heavily than passive engagement like a single like.

**Example:** A lead replied to your thread about sales automation best practices

### Competitor Customer

Lead is a confirmed user of a competing product. Detected via LinkedIn job search matching companies that use competitor tools. These leads receive an intent boost because they already have budget for the category and understand the problem.

**Example:** Lead's company is listed as a customer of a competitor on their website

### Interaction Orbit

AutoReach tracks a lead's engagement orbit — the accounts they interact with on social media. When a lead suddenly starts engaging with multiple competitor or adjacent vendor accounts in a short time window, it signals active evaluation. These clusters receive significant intent and timing boosts because they indicate a lead is actively comparing solutions.

**Example:** A lead liked posts from three competing CRM vendors in the same week — they're evaluating options

## Hiring Signals

These indicate growth and scaling:

### Hiring Activity

Company is actively hiring.

**Example:** LinkedIn shows 5+ job openings, or lead posted "We're hiring!"

### Hiring Roles

Specific roles being hired for.

**Example:** "Hiring: VP Sales, Sales Manager, Sales Dev Rep"

### Job Change Detected

Lead recently changed jobs (career move). New hires often evaluate tools at new companies, making this a strong timing signal. Fit may also shift if they changed to your target industry.

### Role Tenure

How long the lead has been in their current role. Early tenure is a positive timing signal.

### New Hire

Indicates the lead started their current role within the last 6 months.

**Example:** Started new job as "Director of Product" 45 days ago

## Custom Intent Signals

Beyond built-in signals, your **Offer** can define custom intent signals specific to your product. In your offer definition, specify keywords and phrases that your buyers use. AutoReach monitors for mentions of those phrases and factors them into scoring.

**Example for a staffing/recruitment offer:**

- "hiring freeze" (negative signal)
- "hiring blitz" (strong positive signal)
- "talent acquisition is hard" (positive signal)
- "recruiting pipeline weak" (positive signal)

## Offer Pain Match

AutoReach automatically checks if a lead's content matches your **offer's pain points**.

If you defined pain points as:

- "Workflow automation is manual and error-prone"
- "Team productivity is too low"
- "Tool switching is too expensive"

And a lead posted: "Our workflow is so manual, we're spending 20 hours/week on administrative tasks"

AutoReach detects this as a pain match signal and boosts the lead's intent score.

## Industry & Classification

These signals are classification data rather than intent signals, but they impact scoring:

### Industry Classification

Lead's industry classification. Compared against your offer's target industries. A match increases fit, while a mismatch caps the fit score.

### Competitor Employee

Lead works at a competing company. Scored as **Poor Fit** with all scores zeroed out. Despite the scoring reason label saying "disqualified," the actual buyer state is Poor Fit, not Disqualified.

## Location & Geographic Signals

### Location Match

Lead's location matches your preferred locations. The check method depends on your offer's **location filter type**: when set to "lead," it matches the lead's own location; when set to "company_hq," it matches the company's headquarters location. A mismatch results in a Poor Fit score.

## How Signals Affect Scoring

Signals feed into the three scoring dimensions:

- **Fit:** Industry match, role match, company size, location
- **Intent:** Asking for recommendations, switching tools, complaints, pain point matches, competitor engagement, competitor customer status, interaction orbit clusters, custom intent signals
- **Timing:** Job changes, new hires, funding, IPO filings, product launches, hiring activity

The more signals a lead has, and the stronger those signals are, the higher their scores. Each signal contributes to the relevant dimension, and the composite buyer score reflects all three.

> **Note:** Even the strongest intent signal will not guarantee active status on its own. An ideal lead needs fit, intent, AND timing signals together.

## Signal Detection & Recency

AutoReach continuously monitors for new signals. It periodically rechecks leads for job changes, new posts, and company activity. Recent signals carry more weight — a funding announcement from last week is more relevant than one from six months ago.

A lead could be at monitor, and then:

- Their post about your keywords gets traction (+intent)
- They announce a new job in a target role (+timing)
- Their company announces funding (+timing)
- Their score jumps and they promote to active

## Viewing Lead Signals

In the lead profile, you can see:

- All detected signals as boolean flags in the lead's signal summary
- Intent strength (high/medium/low/none) — an overall LLM-assessed rating of buying intent
- Account-level signals with individual strength ratings (high/medium/low) and dates
- Raw activity (posts, comments, job changes)

## Best Practices

> **Tip:** Leads with recent job changes (< 60 days) or recent company signals (funding, hiring, expansion) are hottest. They're actively evaluating.

> **Tip:** Leads actively asking for recommendations or evaluating tools are significantly more likely to reply than those with no intent signal.

> **Warning:** A lead with one strong signal but poor fit is still a poor prospect. Signals work together.

> **Tip:** If you notice a certain phrase or pattern in conversations with buyers, add it as a custom signal. AutoReach will find more people with that pattern.

## Next Steps

- **[Buyer Intelligence & Scoring](buyer-scoring.md)**: See how signals feed into fit, intent, and timing scores
- **[Finding Leads Overview](../finding-leads/overview.md)**: Discover leads showing the signals that matter most
