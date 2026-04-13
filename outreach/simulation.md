# Conversation Simulator

Before launching a sequence to hundreds of leads, test your messaging with the Conversation Simulator. Preview personalized DMs, see variable substitution in real-time, and experiment with follow-ups -- all without sending anything live.

For strategies on comparing message variants, see [A/B Testing](ab-testing.md).

## What Is Simulation?

The Conversation Simulator is a three-step wizard that lets you:

1. **Select a sequence** -- pick any active, paused, or draft sequence
2. **Choose a lead** -- pick a real lead from your database
3. **Select mode and persona** -- configure the simulation mode and persona settings

You can then compare variants side-by-side, edit either variant, reply as the lead to see how AI responds, and preview the full conversation flow. Nothing is sent.

## Starting the Simulator

Navigate to **Simulation** in the sidebar. The simulator is a standalone page at `/simulation`.

## Step 1: Select Sequence

Choose which sequence to simulate. Active, paused, and draft sequences are all available.

## Step 2: Choose Lead

Search or browse leads to simulate with. You can search by name, username, company, or email.

> **Tip:** Pick diverse leads -- simulate with 3-5 leads across different roles, industries, and company sizes. Include at least one lead with minimal enrichment data to ensure messages still read well when data is sparse.

Once selected, you see the lead's profile: name, role, company, followers, recent activity, and other enrichment data.

## Step 3: Select Mode and Persona

AutoReach generates 2 DM variants personalized to the selected lead. For example:

**Variant 1:**

```
Hi Alice,

I came across your profile and saw you're leading engineering at Stripe.
We help companies like Stripe improve developer productivity.

Worth a quick chat?
```

**Variant 2:**

```
Alice,

Stripe is doing awesome work in payments, and I've seen some of your posts
about scaling engineering teams. We've helped other financial services companies
reduce engineering friction during rapid growth.

Open to a 15-min conversation?
```

## Previewing Variants

The simulator shows both variants side-by-side so you can compare tone, check personalization, spot cliches, and evaluate length.

**Variable tooltips:** Hover over any variable (like `{{company}}`) to see the variable name, the actual value pulled for this lead, and the data source.

**Missing data warnings:** If a variable has no data for the selected lead, you see a warning. The phrase containing that variable is omitted in the final message.

## Editing Variants

Click **Edit** on either variant to reword sentences, change tone, adjust the ask, or remove cliches. Changes are preview-only and do not update your sequence template.

## Testing AI Responses

After previewing the DM, test how AI responds to different replies:

1. In the "Lead Reply" field, type a message as if you are the lead
2. AutoReach generates an AI response based on the lead's reply, your DM style, your knowledge base, and sequence AI settings
3. Try different reply types to stress-test your AI:
   - **Positive reply** ("This looks great!") -- does AI offer next steps?
   - **Objection** ("Too expensive.") -- does AI handle it gracefully?
   - **Question** ("How is this different from X?") -- does AI provide a credible comparison?
   - **Silence** (no reply after 3 days) -- does the sequence move to follow-up?

> **Tip:** If the AI tone feels off, edit your AI Prompt in Sequence Settings. See [Cold DM Generation](cold-dm-generation.md) for guidance on AI prompts.

## Sequence Settings Panel

While simulating, you can edit your actual sequence settings:

- **Edit Template** -- modify the message template for the entire sequence
- **Insert Variable** -- browse and insert variables without memorizing syntax
- **AI Prompt** -- adjust tone, instructions, and max responses per conversation

## Common Issues

**Variables showing as blank:** Check that the lead has the relevant data in their profile. Use the variable hover tooltip to see what data is available. Try a different lead with more complete data. See [Template Variables](template-variables.md) for troubleshooting.

**AI responses feel generic:** Check your AI Prompt in Sequence Settings. Provide more context in your knowledge base. Add tone examples to guide the AI voice.

**Simulation doesn't feel representative:** Search for leads that match your actual target audience in Step 2. Run multiple simulations with diverse leads.

## Next Steps

- **[A/B Testing](ab-testing.md)**: Strategies for comparing message variants
- **[Building Sequences](building-sequences.md)**: Apply simulations to real campaigns
- **[Template Variables](template-variables.md)**: All available personalization data
- **[Cold DM Generation](cold-dm-generation.md)**: AI generation best practices
