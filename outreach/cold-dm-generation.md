# Cold DM Generation

AutoReach's Cold DM Generation feature creates **personalized, compelling first messages** tailored to each lead. Instead of writing one generic template, you describe your offer once, and AI generates unique variants for every lead.

## How It Works

When you request a DM generation:

1. You provide basic information about your offer and target
2. AutoReach analyzes the lead's profile, recent activity, and all available lead data
3. AI generates **2 unique DM variants** personalized to that specific lead
4. You preview both, edit if needed, and approve for sending

Each variant uses different framing and tone while following strict rules to feel authentic.

{% hint style="info" %}
DMs are generated at send-time, not template-time. This means every lead gets a message crafted specifically for them.
{% endhint %}

## Configuring DM Generation

When you add a "Send DM" step to your sequence or request ad-hoc generation, you'll configure:

### Offer (Required)

**Length:** 10-300 characters

Describe what you're offering in plain language. Be specific; don't be vague.

**Good examples:**

- "Help B2B SaaS companies reduce sales cycle by 40%"
- "Free audit of your data infrastructure"
- "Introduction to our VP of Sales if we're a fit"
- "Framework for hiring ML engineers in Southeast Asia"

**Bad examples:**

- "Our platform" (too vague)
- "Solutions" (meaningless)
- "Let's connect" (not an offer)

### Target (Required)

**Length:** 10-400 characters

Describe the ideal person you're reaching. Be specific about role, industry, company size, or challenge.

**Good examples:**

- "CTOs at Series B SaaS companies scaling from 50 to 200 people"
- "VP Sales at enterprise software companies"
- "Founders solving customer retention problems"
- "Data engineers working with Snowflake and struggling with data quality"

**Bad examples:**

- "Business professionals" (too broad)
- "Anyone interested in AI" (not specific)

### Goal (Required)

What is the conversation's objective? Choose one:

- **start_conversation** - Open dialogue; no hard ask yet
- **provide_value** - Share something useful (article, intro, tool)
- **soft_pitch** - Gentle suggestion to explore your offer
- **book_call** - Direct ask for a meeting

### Style (Optional)

Tone and length preference:

- **short/punchy** - Brief, snappy, direct (great for busy executives)
- **conversational** - Longer, friendly, storytelling approach (great for founders)

Default: Auto-detect based on lead's activity.

### Tweet Context (Optional)

If the lead has a recent viral post or announcement, paste the text here. AI will reference it naturally in the DM.

**Example:**

```
"Just announced we're expanding into APAC! So excited to build
out our team there and bring our product to new markets."
```

AI might then write:

```
Congrats on the APAC expansion! We've helped other SaaS companies
scale internationally while keeping sales cycles short. Worth a chat?
```

### Lead Name (Optional)

If you want to specify which lead this is for, enter their name or username. Used for personalization.

## DM Generation Rules

AutoReach enforces strict rules on all generated DMs to keep them authentic and effective:

### Structure

- **Max 3 SHORT sentences** - Get to the point
- **End with exactly ONE question** - Creates a natural call-to-action
- **No emojis** - Professional tone
- **No em dashes** - Use commas or periods instead

### Openers

AutoReach avoids overused openers that experienced professionals immediately recognize as automated outreach.

### Phrases

AutoReach avoids buzzwords and cliches that signal automated outreach and destroy credibility.

### Personalization Rules

- Reference specific data: company, role, recent post, or activity
- Avoid generic compliments ("great post!"; use specific insight instead)
- Make the DM feel one-to-one, even though it's generated

## Example: Full DM Generation

**You provide:**

- Offer: "Help Series A startups improve developer productivity by 30%"
- Target: "Engineering leaders at Series A startups in DevOps space"
- Goal: book_call
- Style: conversational
- Lead: @alice_eng (VPE at DataPlatformCo)

**AutoReach generates Variant 1:**

```
Hey Alice, I've been following DataPlatformCo's growth and
impressed by how you're scaling the eng team.

A lot of VPEs we work with are hitting the same wall, where dev productivity
suffers as the team grows. We've helped teams like [Example] fix this
in 30 days.

Would a quick 15-min chat help you see if we're a fit?
```

**AutoReach generates Variant 2:**

```
Alice, congrats on DataPlatformCo's recent funding round.
Series A is a great inflection point for scaling teams.

One thing we've seen: when teams go from 5 engineers to 15+,
developer velocity drops if you don't fix workflows early.
We've built a system that prevents this.

Open to a quick conversation about whether this applies to you?
```

**You:**

- Review both variants
- Pick one or edit it
- Approve for sending

---

## Tips for High Reply Rates

1. **Be specific** - Reference their company, role, or recent activity
2. **Lead with their benefit** - Not your product features
3. **Ask a real question** - Not a fake call-to-action
4. **Keep it short** - 3 sentences max
5. **Avoid flattery** - "Impressed by your company" feels hollow; instead use fact-based observation
6. **Test different goals** - Some leads respond to value/education; others want a direct ask
7. **Use their language** - If they talk about "DevOps," use that term; don't say "infrastructure automation"

---

## Troubleshooting

### "Generation failed"

- Check that Offer and Target are specific (not vague)
- Ensure Lead has sufficient enrichment data (name, company, title)
- Try again in a few seconds

### "Generated DMs feel generic"

- Provide more context in Tweet Context field
- Specify the Goal more clearly (book_call vs. provide_value)
- Add more detail to the Target field

---

## Next Steps

- Learn about [Template Variables](template-variables.md) for manual DM customization
- Explore [Simulation & A/B Testing](simulation.md) to preview DMs with real leads
- See [Building Sequences](building-sequences.md) to integrate DM generation into campaigns
- Review [Supported Actions](supported-actions.md) for when to use DM vs. other engagement types
