# Building Sequences (Flow Editor)

Learn how to create and configure sequences using AutoReach's visual Flow Builder. In just a few clicks, you can design multi-step campaigns that automatically engage your leads.

## Creating a New Sequence

1. Navigate to **Outreach** > **Sequences** in the main menu
2. Click the **Create Sequence** button (top right)
3. Enter a sequence name (e.g., "Tech CTOs - Value First")
4. (Optional) Associate an offer/ICP to track performance by target audience
5. Select your primary platform: X or LinkedIn
6. Click **Create**

Your new sequence opens in the **Flow Editor**, ready to build.

{% hint style="info" %}
You can create sequences for both X and LinkedIn in the same account, or mixed sequences that use both platforms.
{% endhint %}

## The Flow Builder Interface

The Flow Builder displays your sequence as a series of connected cards:

```
[Start] --> [Like Post] --> [Wait 2 Days] --> [Follow] --> [Wait 1 Day] --> [Send DM]
```

- **Cards** represent actions or delays
- **Arrows** show the sequence flow
- **Connector nodes** (the small circles) are where you add new steps
- **Drag to reorder** - grab the left side of any card to reorder steps

## Adding Steps to Your Sequence

### Method 1: Using the "+" Button

1. Click the **"+" button** between cards (or at the end of the sequence)
2. Select an action type from the menu:
   - Like Post
   - Reply/Comment
   - Follow User
   - Send DM
   - Condition (branching)
   - Remove Connection
3. A new card appears; configure it (see below)

### Method 2: Drag from the Action Library

Drag action tiles from the right sidebar directly onto the flow.

## Configuring Actions

Click on any action card to open its **configuration panel**. Every action has these settings:

### Platform

Choose **X** or **LinkedIn** for this specific action. This lets you mix platforms within one sequence.

{% hint style="info" %}
Not all actions are available on all platforms. For example, "Remove Connection" only works on LinkedIn. See [Supported Actions by Platform](supported-actions.md) for details.
{% endhint %}

### Timing / Delay

How long to wait before executing this action:

- Enter a number and select the unit: **Days** or **Minutes**
- Example: `2 Days` means wait 2 full days after the previous action completes
- Example: `30 Minutes` means execute 30 minutes after the lead enters the sequence

Leave blank or set to `0` for immediate execution.

### Message Template (for DM, Reply, Comment)

Write your message using **template variables** that AutoReach will personalize:

```
Hi {{first_name}},

I came across your profile and saw you're working on {{company_name}}.
We help teams like yours improve {{pain_point}}.

Worth a quick chat?

- {{user_name}}
```

Variables like `{{first_name}}`, `{{company_name}}`, etc. are replaced with real lead data at send time. See [Template Variables](template-variables.md) for the complete list.

{% hint style="info" %}
Use the **Insert Variable** dropdown in the config panel to browse available fields without memorizing syntax.
{% endhint %}

### Step Label (Optional)

Give your action a friendly name (e.g., "Initial DM", "Follow-up if No Reply") to keep your flow readable.

## Conditional Branching

The **Condition** action lets you split your sequence based on lead behavior.

### Example: Reply Detection

```
[Send DM] --> [Condition: Did they reply?]
                    |-- YES --> [Send Follow-up]
                    |-- NO  --> [Send DM Again in 3 days]
```

To set up a condition:

1. Add a **Condition** step after an action
2. Choose the condition type:
   - **Has Replied** - Branch if the lead replied to a previous DM
   - **Has Not Replied** - Branch if no reply after X days
3. Configure the "YES" branch (right arrow) and "NO" branch (left arrow)
4. Add different actions to each branch

{% hint style="info" %}
Conditions are checked at execution time. A lead can only move down one branch. Once they match a condition, they follow that path.
{% endhint %}

## Common Sequence Patterns

### Soft Engagement (Good for Cold Outreach)

Perfect for audiences with low trust. Builds familiarity before direct contact.

```
[Like Post] --> [Wait 1 Day] --> [Follow] --> [Wait 2 Days] --> [Send DM]
```

**Why it works:** Liking and following feel natural and non-intrusive. By the time your DM lands, the lead has seen you twice.

### Direct Value (For Warm Leads)

If you already have some engagement or a referral, go direct faster.

```
[Send DM] --> [Wait 2 Days] --> [Condition: Replied?]
               |-- YES --> [Send Call Link]
               |-- NO  --> [Follow + Send DM Again]
```

### Nurture Loop (For Extended Follow-up)

For high-value targets, maintain engagement over time.

```
[Send DM] --> [Wait 2 Days] --> [Reply if No Response]
         --> [Wait 3 Days] --> [Like Recent Post]
         --> [Wait 2 Days] --> [Send Value Content]
```

## Sequence Settings

Once your flow is designed, configure overall sequence behavior:

### Basics

- **Name** - Displayed in the Sequences list
- **Description** - Optional notes about your sequence goal
- **Offer/ICP** - Link to an offer to track performance by target audience

### Enrollment & Lead Filters

- **Skip Already Contacted Leads** - Don't re-reach leads from other sequences
- **Skip Negative Content** - Avoid leads with controversial/toxic posts
- **Max Days Since Last Post** - Only reach leads with recent activity

### Daily Limits

- **Daily DM Limit** - Max DMs per day (prevents rate limiting)
- **Daily Action Limit** - Max total actions per day across all step types
- Platform-specific limits for X and LinkedIn

### AI & Responses

- **Max AI Responses per Conversation** - How many auto-replies per lead (0 to disable AI)
- **Enable/Disable AI by Default** - New conversations have AI on or off

See [Scheduling & Send Limits](scheduling.md) for details on how limits work.

## Starting, Pausing, and Stopping

### Start

Click **Start Sequence** to activate it. AutoReach begins enrolling leads and executing actions.

### Pause

Click **Pause** to temporarily stop all pending actions without losing progress. Resume whenever you're ready.

### Stop

Click **Stop** to permanently end the sequence. Active leads are marked as completed; no further actions execute.

{% hint style="warning" %}
Stopping a sequence is permanent. You cannot restart it. Instead, create a new sequence or duplicate this one.
{% endhint %}

## Duplicating a Sequence

Click the **Duplicate** button to copy an existing sequence. This is useful for A/B testing or reusing a template.

## Tips for Building Effective Sequences

1. **Start with soft engagement** - A Like + Follow before your DM gets 3x better reply rates
2. **Use conditions wisely** - Route hot leads (those who replied) to direct calls; cold leads to nurture
3. **Respect timing** - Don't overwhelm leads. Space actions 1-3 days apart for a natural feel
4. **Test before launching** - Use the [Simulation tool](simulation.md) with real leads before sending to 1000+
5. **Monitor metrics** - Check reply rate, meeting booked rate, and adjust messaging accordingly
6. **Keep templates concise** - Short, personal messages outperform long sales pitches
7. **Mix platforms** - Use a Comment on X, then follow up with a DM on LinkedIn for cross-platform reach

## Next Steps

- Learn about all [Supported Actions](supported-actions.md)
- Understand [Cold DM Generation](cold-dm-generation.md) for AI-powered message creation
- Explore [Template Variables](template-variables.md) to personalize at scale
- Use [Simulation & A/B Testing](simulation.md) to preview before sending
