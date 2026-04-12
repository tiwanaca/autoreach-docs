# Template Variables

Template variables allow you to personalize messages at scale. Instead of writing individual messages, you write once with placeholders that AutoReach fills in with real lead data at send time.

## Using Variables in Templates

When writing a message template, use double curly braces: `{{variable_name}}`

AutoReach will replace each variable with actual data from the lead's profile:

**Your template:**

```
Hi {{first_name}},

I saw you're working at {{company}} as a {{role}}.
We help companies like {{company}} in {{industry}} improve {{pain_point}}.

Worth a chat?
```

**What a lead sees:**

```
Hi Alice,

I saw you're working at Stripe as a VPE.
We help companies like Stripe in FinTech improve developer productivity.

Worth a chat?
```

{% hint style="info" %}
If a variable has no data for a lead, the entire phrase containing it is gracefully removed. For example, if we don't have {{company}}, the sentence "We help companies like {{company}}" is omitted.
{% endhint %}

## Lead Information Variables

These variables pull from the lead's profile and enrichment data. AutoReach automatically populates variables from lead profiles and enrichment data.

### Basic Identity

- `{{name}}` - Full name
- `{{first_name}}` - First name only
- `{{last_name}}` - Last name only
- `{{username}}` - X or LinkedIn username
- `{{email}}` - Email address (if found)

### Professional Profile

- `{{role}}` - Job title (e.g., "VP Sales", "Head of Product")
- `{{headline}}` - LinkedIn headline/current position
- `{{company}}` - Current company name
- `{{company_size}}` - Company size bracket (e.g., "50-200 employees", "1000+")
- `{{industry}}` - Primary industry (e.g., "SaaS", "FinTech", "Insurance")
- `{{location}}` - Geographic location
- `{{bio}}` - X or LinkedIn bio

### Enrichment & Intelligence

- `{{pain_point}}` - Inferred challenge/pain point (e.g., "customer retention", "developer productivity")
- `{{funding_stage}}` - Company funding stage (e.g., "Series B", "Late Stage")
- `{{tech_stack}}` - Key technologies used by company
- `{{followers}}` - Number of followers on X or LinkedIn
- `{{podcasts}}` - Podcasts the lead hosts or appears on

### Contact & Web

- `{{website}}` - Company website URL
- `{{linkedin_url}}` - LinkedIn profile URL
- `{{enrichment_summary}}` - AI-generated brief profile summary

## Your Information Variables

These reference your own profile and business info:

- `{{user_name}}` - Your name (from account settings)
- `{{company_name}}` - Your company name
- `{{offer_name}}` - The name of the offer/product being pitched

## How Variables Get Populated

AutoReach automatically populates variables from lead profiles and enrichment data. If a variable has no data, it's handled gracefully:

| Scenario                              | Result                                                                                                     |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Single variable is empty              | Variable replaced with empty string; text flows naturally                                                  |
| Phrase contains empty variable        | Entire phrase is omitted (e.g., "We help {{company}} in {{industry}}" omitted if {{industry}} is missing)  |
| Multiple variables in one sentence    | If any is empty, sentence is removed                                                                       |

{% hint style="info" %}
Always test templates with a few different leads using the Simulator before sending to ensure variables populate correctly.
{% endhint %}

## Example Templates

### Soft Pitch (Book a Call)

```
Hi {{first_name}},

Saw your post about {{pain_point}}. Great insight.
{{company}} is doing some interesting work there.

I help {{company_size}} {{industry}} companies solve this exact problem.
Would love to share what we've learned. 20 min?

- {{user_name}}
```

### Value First (Education)

```
{{first_name}},

I came across your profile and saw you're tackling {{pain_point}} at {{company}}.

I just published a framework that {{industry}} teams have found helpful.
Thought you'd find it valuable: [link]

No ask, just good stuff to learn from.
```

### Introduction (Connecting)

```
Hey {{first_name}},

Quick ask: I'm building my network of {{role}}s in {{industry}}.

Our {{user_name}} (CEO of {{company_name}}) would love to connect.
She's in the same space and I think you'd both find it valuable.

Open to an intro?
```

### Social Proof (Credibility)

```
{{first_name}},

{{company}} just shipped something we help with at scale, helping
{{company_size}} companies improve {{pain_point}}.

One of your competitors, {{example_company}}, cut time-to-value by 40%.
Curious if you'd benefit from the same approach?

Worth a quick conversation?
```

## Tips for Effective Personalization

1. **Use specific variables** - `{{role}}` and `{{pain_point}}` work better than generic compliments
2. **Combine 2-3 variables max per message** - Too many looks spammy
3. **Test edge cases** - Preview with leads missing data to ensure graceful fallback
4. **Reference recent activity** - Paste a tweet or post in the Simulator context for more relevant mentions
5. **Keep sentences short** - When variables are removed, longer sentences become awkward
6. **Use Insert Variable UI** - Don't memorize syntax; use the dropdown in the Sequence Settings panel

## Finding Available Variables

In the Sequence Builder, click the **Insert Variable** button in the message template panel. A dropdown shows all available variables for the current lead, along with their current values.

{% hint style="info" %}
The Insert Variable dropdown is the easiest way to browse and select variables without memorizing syntax.
{% endhint %}

## Dynamic Content Based on Variables

Some sequences use multiple templates and branch based on variable values. For example:

```
[Condition: Has {{tech_stack}} includes "Salesforce"?]
  |-- YES --> Send DM about Salesforce integration
  |-- NO  --> Send DM about generic CRM tools
```

This isn't supported in core AutoReach, but you can achieve similar effects by:

1. Creating separate sequences for different target segments
2. Using Offers/ICPs to pre-filter leads
3. Manually crafting templates that gracefully handle missing data

## Common Issues

### Variable Not Populating

**Problem:** You use `{{company}}` but it shows as blank.

**Solution:**

- Check that the lead has company data in their profile
- Verify the variable name is spelled correctly (case-sensitive)
- Use the Insert Variable dropdown to confirm available variables for this lead

### Sentence Reads Awkwardly

**Problem:** "We help {{company}} improve {{pain_point}}." renders as "We help  improve ." when data is missing.

**Solution:**

- Rewrite to include the variable within a larger phrase: "If you're working on {{pain_point}}, I'd love to chat."
- This way, the entire sentence is omitted if the variable is empty

### Too Many Variables

**Problem:** Message looks spammy or robotic.

**Solution:**

- Limit to 1-2 variables per message
- Prioritize {{first_name}} and one key data point ({{role}}, {{company}}, {{pain_point}})
- Use rich context instead of multiple variables

---

## Next Steps

- See [Building Sequences](building-sequences.md) to write templates in the Flow Builder
- Explore [Simulation & A/B Testing](simulation.md) to preview variable substitution with real leads
- Learn [Cold DM Generation](cold-dm-generation.md) for AI-powered personalized messages
- Review [Supported Actions](supported-actions.md) to understand which actions support templates
