# Simulation & A/B Testing

Before launching a sequence to hundreds of leads, test your messaging with the **Conversation Simulator**. Preview personalized DMs, see variable substitution in real-time, and experiment with follow-ups—all without sending anything live.

## What is Simulation?

The **Conversation Simulator** is a three-step wizard that lets you:

1. **Select a sequence** – Pick any active or draft sequence
2. **Choose a lead** – Pick a real lead from your database
3. **Generate and preview DMs** – See 2 personalized variants with actual lead data

You can then:
- Compare variants (side-by-side)
- Edit either variant
- Reply as the lead and see how AI responds
- Preview the full conversation flow

All in a safe preview environment—nothing is sent.

## Starting the Simulator

### Option 1: From Sequence Builder
1. Open a sequence in edit mode
2. Click **Simulate** button (top right or in-flow)
3. Follow the 3-step wizard

### Option 2: From Sequences List
1. Go to **Outreach** → **Sequences**
2. Click the **Simulate** icon next to any sequence
3. Start the wizard

## Step-by-Step: Running a Simulation

### Step 1: Select Sequence

Choose which sequence to simulate:

- **Active sequences** (running now)
- **Paused sequences** (can simulate, won't send)
- **Draft sequences** (test before launching)

Pick the sequence you want to preview.

### Step 2: Choose Lead

Search or browse leads to simulate with:

**Search by:**
- Name (e.g., "Alice")
- Username (e.g., "@alice_eng")
- Company (e.g., "Stripe")
- Email

**Tips:**
- **Pick diverse leads** – Simulate with 3–5 leads with different roles/companies
- **Test edge cases** – Include a lead with minimal enrichment data (no company, bio, etc.)
- **Use high-value leads** – If you're reaching VPs, simulate with a VP to see how the DM feels

Once selected, you see the lead's profile: name, role, company, followers, recent activity, etc.

### Step 3: Generate DM

AutoReach generates **2 DM variants** personalized to the selected lead:

**Variant 1:**
```
Hi Alice,

I came across your profile and saw you're leading engineering at Stripe. 
We help companies like Stripe improve developer productivity.

Worth a quick chat?

–{{user_name}}
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

### Side-by-Side Comparison

The simulator shows both variants so you can:

- **Compare tone** – Is one too salesy? Too casual?
- **Check personalization** – Are variables substituted correctly?
- **Spot clichés** – Does either feel robotic or overused?
- **Evaluate length** – Which length gets better response rates for this audience?

### Variable Substitution Display

Hover over any variable (like `{{company}}`) to see:
- The variable name
- The actual value pulled for this lead
- The data source (enrichment, profile, etc.)

**Example:**
```
{{company}} = Stripe (from LinkedIn profile)
{{role}} = VP Engineering (from enrichment data)
{{pain_point}} = developer productivity (inferred from recent posts)
```

### Check for Missing Data

If a variable has no data, you'll see a warning:

```
⚠️ {{tech_stack}} has no data for this lead.
```

The full phrase containing the variable is omitted in the final message.

{% hint style="info" %}
Test simulations with a few leads who have incomplete data to ensure messages still read well.
{% endhint %}

## Editing Variants

Don't like either variant? **Edit them directly.**

Click **Edit** on either variant and modify:
- Reword sentences
- Change tone
- Adjust the ask
- Remove clichés

Changes are **preview-only**—they don't update your sequence template. Use these edits to inform your actual template in the Sequence Settings.

## Testing AI Responses

After previewing the DM, test how AI responds to replies:

### Step 1: Type a Lead Reply

In the "Lead Reply" field, type a message as if you're the lead:

**Example replies:**
```
"Looks interesting, but we're not hiring right now."

"This is perfect! When are you free?"

"I'm not sure what you're offering. Can you explain more?"
```

### Step 2: See AI Response

AutoReach generates an AI response based on:
- The lead's reply
- Your DM style
- Your knowledge base
- Sequence AI settings

**Example:**

**Your DM:**
```
Hi Alice,

I saw you're leading engineering at Stripe. 
We help companies improve developer productivity.

Worth a quick chat?
```

**Lead replies:**
```
"What exactly do you do? Not clear from your message."
```

**AI responds:**
```
Great question! We help high-growth engineering teams reduce 
the time it takes to ship features—from weeks to days. 

We've worked with companies like Stripe to streamline developer workflows. 
Would a 15-min call to explore if we're a fit make sense?
```

{% hint style="info" %}
This is a preview of what your AI would actually say if this sequence were live. Edit your AI prompt in **Sequence Settings** if the tone feels off.
{% endhint %}

### Step 3: Iterate

Try different replies to stress-test your AI:

- **Positive reply:** "This looks great!"
  - → Does AI offer next steps (calendar link, call time)?
- **Objection:** "Too expensive."
  - → Does AI handle the objection gracefully?
- **Question:** "How is this different from X?"
  - → Does AI provide a credible comparison?
- **Silence:** No reply after 3 days
  - → Does sequence move to follow-up or stop?

---

## Research Integration

The simulator uses **enrichment context** to make DMs smarter:

### Lead Profile Data
- Company, role, location, followers
- Tech stack, funding stage, company size
- Recent posts and engagement

### Recent Social Activity
- Last 5–10 posts (X or LinkedIn)
- Topics they're discussing
- Industry and role-specific signals

### Knowledge Base Context
- Your company info and value propositions
- Past successful messages (from sent conversations)
- Tone examples you've approved

This context helps generate messages that feel specific and informed.

{% hint style="info" %}
The more enrichment data you have on a lead, the more personalized their simulated message will be.
{% endhint %}

## RAG (Retrieval-Augmented Generation)

The simulator uses **RAG (Retrieval-Augmented Generation)** to fetch relevant context:

1. **Lead query:** Alice, VP at Stripe, interested in developer productivity
2. **Retrieval:** Looks up:
   - Similar high-value prospects in your past conversations
   - Successful messages sent to VPs at fintech companies
   - Messages that mentioned "developer productivity"
3. **Generation:** Creates a new DM informed by successful patterns

This means your simulator gets smarter over time as you accumulate more conversation data.

## Sequence Settings Panel

While simulating, you can edit your actual sequence settings:

### DM Template
Click **Edit Template** to modify the message template for your entire sequence. Changes apply to all future sends.

### Insert Variable
Use the **Insert Variable** dropdown to browse and insert variables into your template without memorizing syntax.

### AI Prompt
Adjust how AI responds in this sequence:
- Tone (formal, casual, friendly)
- Instruction (be helpful, book a call, provide value)
- Max responses per conversation

See [Cold DM Generation](cold-dm-generation.md) for more on AI prompts.

---

## A/B Testing Strategy

Use the simulator to test messaging variations **before sending**:

### Test 1: Soft vs. Direct Ask

**Variant A (Soft):**
```
Hi {{first_name}},

Saw your post on {{topic}}. Would love to connect and learn 
how you're thinking about it.
```

**Variant B (Direct):**
```
{{first_name}},

We help {{company_size}} companies improve {{pain_point}}. 
Interested in a quick conversation?
```

Simulate both with 3–5 different leads. Which feels more authentic for your audience?

### Test 2: Long vs. Short

**Variant A (Long):**
```
Hi {{first_name}},

I've been following {{company}} for a while and really impressed 
by how you're building {{achievement}}. 

In my experience working with similar companies, one thing that often 
holds teams back is {{pain_point}}. We've built a framework to help with this.

Would you be open to a 20-min conversation to explore?
```

**Variant B (Short):**
```
{{first_name}},

Impressed by {{company}}'s progress. We help with {{pain_point}}.
Worth a chat?
```

Simulate with your target audience. Short and punchy, or long and detailed?

### Test 3: Reference vs. No Reference

**Variant A (Reference):**
```
{{first_name}},

Noticed your post about {{recent_topic}}. We've worked with 
{{example_company}} on the same challenge.

Worth a conversation?
```

**Variant B (Generic):**
```
{{first_name}},

We help companies like {{company}} improve {{pain_point}}.
Interested?
```

Does referencing their specific activity/post get better simulated responses?

### Test 4: Tone

**Variant A (Professional):**
```
Dear {{first_name}},

I would like to discuss how we can assist {{company}} 
in improving {{pain_point}}.
```

**Variant B (Casual):**
```
Hey {{first_name}},

Been following {{company}}'s journey. Think we could help 
with {{pain_point}}.

Worth exploring?
```

---

## Tips for Effective Simulation

1. **Simulate with 5+ different leads** – Not just one. Different roles, industries, company sizes
2. **Include edge cases** – Leads with minimal data; leads from unexpected companies
3. **Test AI responses** – Reply as different lead personas (eager, skeptical, uninterested)
4. **Edit and iterate** – Don't accept the first variant; try edits until it feels right
5. **Take notes** – Document which messaging patterns resonate in your simulations
6. **Compare to your past success** – If you've sent campaigns before, reference what worked
7. **Get feedback** – Ask teammates to review simulated conversations
8. **Re-simulate before scale** – Before launching to 1000 leads, simulate again

## Common Issues

### "Variables aren't substituting correctly"

**Problem:** `{{company}}` shows as blank in the simulation.

**Solution:**
- Check that the lead has company data in their profile
- Use the Variable Hover tooltip to see what data is available
- Test with a different lead who has more complete data
- See [Template Variables](template-variables.md) for troubleshooting

### "AI responses feel generic"

**Problem:** Lead replies and AI response is boring or off-topic.

**Solution:**
- Check your AI Prompt in Sequence Settings (is it specific?)
- Provide more context in your knowledge base
- Add tone examples in Sequence Settings to guide the AI
- Try different lead replies to see if AI responds better to specific objections

### "Simulation doesn't feel representative"

**Problem:** You're testing with VPs but the simulator only shows ICs (individual contributors).

**Solution:**
- Manually search for VP-level leads in Step 2
- Run multiple simulations with diverse leads
- Check that your lead database is accurate and up-to-date

---

## Next Steps

- Learn [Building Sequences](building-sequences.md) to apply simulations to real campaigns
- Explore [Template Variables](template-variables.md) to understand all available data
- See [Cold DM Generation](cold-dm-generation.md) for AI generation best practices
- Review [Supported Actions](supported-actions.md) to test other action types
