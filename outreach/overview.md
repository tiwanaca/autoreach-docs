# Outreach & Sequences Overview

Outreach & Sequences is the heart of AutoReach. It is where you design, launch, and manage multi-step campaigns that automate your engagement across X and LinkedIn.

## What is a Sequence?

A **sequence** is an automated campaign that guides leads through a series of actions designed to build relationships and drive results. Instead of manually reaching out to each lead one by one, sequences let you orchestrate engagement at scale while keeping everything personal.

A typical sequence might look like:

- Day 1: Like their recent post
- Day 2: Follow them
- Day 3: Send a personalized DM
- Day 5: If they replied, send a follow-up. If not, try again.

{% hint style="info" %}
Sequences run automatically on a schedule you define, respecting your Activity Window and daily send limits.
{% endhint %}

## How Sequences Work

### Visual Flow Builder

Design sequences using the intuitive **Flow Builder**: drag-and-drop cards connected by flows to visualize your entire campaign strategy. No coding required.

### Supported Actions

Each step in a sequence performs one of these actions:

- **Like Post** - Like a lead's recent post (soft engagement)
- **Reply/Comment** - Reply to a post with a personalized message
- **Follow/Connect** - Follow on X or send a connection request on LinkedIn
- **Send DM** - Send a direct message (AI-personalized)
- **Condition** - Branch your sequence: "If they replied, do X; if not, do Y"
- **Remove Connection** - Clean up non-responders (LinkedIn only)

### Personalization with AI

Every message sent through a sequence is **personalized** using:

- Lead's profile data (name, role, company, location)
- Enrichment intelligence (tech stack, funding, recent activity)
- Your knowledge base and context
- Lead behavior within the sequence

This means each lead receives a message that feels one-to-one, even though you're reaching thousands.

{% hint style="info" %}
No two leads get identical messages. AutoReach dynamically inserts variables like {{name}}, {{company}}, {{role}} and more into your templates.
{% endhint %}

## Key Configuration

Each sequence step is fully configurable:

- **Platform** - Choose X or LinkedIn for each action
- **Timing** - Delay before executing (days or minutes)
- **Message Template** - Write your message once, AutoReach personalizes it for each lead
- **Conditions** - Optional branching logic to route leads based on responses

## Daily Send Limits

To keep your accounts healthy and reduce the risk of platform limits, AutoReach enforces configurable **daily send limits** for DMs and other actions. Your limits scale based on your account age, history, and platform.

{% hint style="warning" %}
Exceeding daily limits can trigger platform anti-spam measures. AutoReach queues excess actions for the next day automatically.
{% endhint %}

## Activity Window

Outreach only happens during your configured **Activity Window**. For example, 9am-9pm in your timezone. This ensures messages are sent at natural, human hours.

Your enrichment pipeline can run 24/7 if you enable **24/7 Pipeline Mode**, preparing leads while you sleep, ready for outreach during your window.

## Track Your Results

Sequences report on key metrics:

| Metric           | What It Measures                                  |
| ---------------- | ------------------------------------------------- |
| Leads Added      | Total leads enrolled in the sequence              |
| Leads Contacted  | Leads that received at least one action           |
| Leads Replied    | Leads that messaged you back                      |
| Meetings Booked  | Leads that scheduled a call (if integrated)       |

Use these metrics to optimize your sequence strategy and identify what messaging and cadence work best.

## Next Steps

Ready to build your first sequence?

1. Start with **[Building Sequences (Flow Editor)](building-sequences.md)** to learn the interface
2. Explore **[Supported Actions by Platform](supported-actions.md)** to understand what's possible on X vs LinkedIn
3. Learn about **[Cold DM Generation](cold-dm-generation.md)** to create compelling first messages
4. Use **[Simulation & A/B Testing](simulation.md)** to preview before sending
