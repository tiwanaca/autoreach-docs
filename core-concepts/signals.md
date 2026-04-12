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

### asked_recommendation

Lead explicitly asked for recommendations on a product/service category.

**Example:** "Anyone have a good recommendation for customer data platforms? We're evaluating options."

### switching_from

Lead mentioned they are switching away from a competitor. This is one of the strongest intent signals.

**Example:** "Finally ditching Mailchimp for Klaviyo. Should've done this years ago."

### looking_for_alternative

Lead is actively searching for an alternative to their current solution.

**Example:** "Looking for an alternative to our current project management tool. What are people using now?"

### complained

Lead complained about their current tool or process (pain point expressed).

**Example:** "Our CRM is so slow. Takes 30 seconds just to load a contact. Killing our team's productivity."

### tool_mention

Lead mentioned using or considering a competitor or similar tool.

**Example:** "Integrating with Zapier this week" or "Testing Stripe for payments"

## Company-Level Signals

These signals indicate something major is happening at the company level:

### funding

Company announced a new funding round.

**Example:** "Proud to announce Series B funding: $25M led by Sequoia"

### product_launch

Company launched a new product or major feature.

**Example:** "Today we're launching the beta of Product V2. Total redesign based on your feedback."

### mergers_acquisitions

Company acquired another company or was acquired.

**Example:** "Big news: We've acquired TechStartup to expand our platform capabilities"

### strategic_partnership

Company announced a partnership with another company.

**Example:** "Excited to partner with AWS to bring enterprise-grade security"

### cost_cutting

Company announced layoffs, consolidation, or cost reduction initiatives.

**Example:** "Streamlining our tech stack to focus on core tools. Consolidating vendors."

### ipo_filing

Company filed for IPO or public markets.

**Example:** "We're going public! S-1 filing effective today."

### geographic_expansion

Company is expanding to a new geographic market.

**Example:** "Excited to announce our expansion into APAC. Opening offices in Singapore and Sydney."

## Engagement Signals

These signals show active engagement with your domain:

### competitor_engagement

Lead engaged with (liked, commented on) content from competitor companies.

**Example:** Lead liked a post from your competitor about their product

### engagement_pattern

Lead has high engagement on posts related to your category.

**Example:** Consistently comments on automation/AI posts, high like ratio

### own_post_engagement

Lead posted content about your space and got significant engagement (inbound signal).

**Example:** Lead posted "Evaluating workflow tools" and got 50+ comments/engagement

## Hiring Signals

These indicate growth and scaling:

### hiring

Company is actively hiring.

**Example:** LinkedIn shows 5+ job openings, or lead posted "We're hiring!"

### hiring_roles

Specific roles being hired for.

**Example:** "Hiring: VP Sales, Sales Manager, Sales Dev Rep"

### job_change_detected

Lead recently changed jobs (career move). New hires often evaluate tools at new companies, making this a strong timing signal. Fit may also shift if they changed to your target industry.

### role_tenure_days

How long the lead has been in their current role. Early tenure is a positive timing signal.

### is_new_hire

Flag indicating the lead just changed jobs recently.

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

### industry

Lead's industry classification. Compared against your offer's target industries. A match increases fit, while a mismatch caps the fit score.

### is_competitor

Lead works at a competing company. Automatically disqualified.

### is_internal_builder

Lead is building a competing product. Automatically disqualified.

## Location & Geographic Signals

### location_match

Lead's location matches your preferred locations. Matching locations increase fit, while excluded locations decrease it.

### timezone_alignment

Lead's timezone overlaps with your sales hours. Used for scheduling outreach at the right time.

## How Signals Affect Scoring

Signals feed into the three scoring dimensions:

- **Fit:** Industry match, role match, company size, location
- **Intent:** Asking for recommendations, switching tools, complaints, pain point matches, competitor engagement, custom intent signals
- **Timing:** Job changes, new hires, funding, IPO filings, product launches, hiring activity

The more signals a lead has, and the stronger those signals are, the higher their scores. Each signal contributes to the relevant dimension, and the composite buyer score reflects all three.

{% hint style="info" %}
**No Single Signal Wins:** Even the strongest intent signal will not guarantee active status on its own. An ideal lead needs fit, intent, AND timing signals together.
{% endhint %}

## Signal Detection & Recency

AutoReach continuously monitors for new signals:

- **Activity fetches** run daily to check for new posts, engagement, job changes
- **New signals** detected in the last 7 days boost a lead's score
- **Old signals** (> 30 days) decay slightly in weight
- **Job changes** are weighted heavily regardless of age (can be a few weeks old)

A lead could be at monitor (40 score), and then:

- Their post about your keywords gets 100 reactions (+intent)
- They announce a new job in a target role (+timing)
- Their company announces funding (+timing)
- Their score jumps to 65 and they promote to active

## Viewing Lead Signals

In the lead profile, you can see:

- All detected signals (with dates)
- Signal strength (high/medium/low)
- Which signals contributed most to their score
- Raw activity (posts, comments, job changes)

## Best Practices

{% hint style="info" %}
**Focus on Timing:** Leads with recent job changes (< 60 days) or recent company signals (funding, hiring, expansion) are hottest. They're actively evaluating.
{% endhint %}

{% hint style="info" %}
**Intent is Predictive:** A lead asking "looking for recommendations" is 2-3x more likely to reply than someone with no intent signal. Weight intent signals heavily in your mental model.
{% endhint %}

{% hint style="warning" %}
**Don't Over-Weight Single Signals:** A lead with one strong signal but poor fit is still a poor prospect. Signals work together.
{% endhint %}

{% hint style="info" %}
**Custom Signals are Powerful:** If you notice a certain phrase or pattern in conversations with buyers, add it as a custom signal. AutoReach will find more people with that pattern.
{% endhint %}

## Next Steps

- **[Buyer Intelligence & Scoring](buyer-scoring.md)**: See how signals feed into fit, intent, and timing scores
- **[Finding Leads Overview](../finding-leads/overview.md)**: Discover leads showing the signals that matter most
