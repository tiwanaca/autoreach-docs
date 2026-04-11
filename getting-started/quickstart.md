# Quickstart

Get AutoReach up and running in under 15 minutes and launch your first outreach sequence.

## Step 1: Create Your Account and Log In

Visit [autoreach.tech](https://autoreach.tech) and sign up with your email. You'll receive a confirmation email—click the link to activate your account, then log in to the dashboard.

## Step 2: Create Your First Offer

An **Offer** is the core of AutoReach. It describes what you sell, who you're targeting, and what you want to achieve. AutoReach uses this to personalize messaging, score leads, and generate responses.

1. Go to **Offers** in the sidebar
2. Click **Create Offer**
3. Fill in the required fields:
   - **Name**: Your product or service (e.g., "B2B SaaS Security Audits")
   - **Description**: What you do, in 10-300 characters
   - **Target Audience**: Who you're reaching (e.g., "CTOs at mid-market tech companies")
   - **Goal**: Choose one:
     - `start_conversation` — Get a response
     - `provide_value` — Share insights or resources
     - `soft_pitch` — Introduce your solution gently
     - `book_call` — Schedule a meeting
4. Click **Save**

{% hint style="info" %}
**Tip**: The more detailed your offer, the better AutoReach's AI personalizes outreach. Add your target locations, pain points, and competitors in the offer settings for even smarter lead scoring.
{% endhint %}

## Step 3: Connect at Least One Social Account

AutoReach works on X (Twitter) and LinkedIn. You need at least one account to get started.

### Option A: Connect X/Twitter

1. Go to **Accounts** → **Add Account** → **X (Twitter)**
2. Use the Chrome Extension to extract cookies automatically, or manually paste cookies from your browser's DevTools
3. Set your **Activity Window** (e.g., 9am–9pm in your timezone)
4. Set your **Daily DM Limit** (default is 20/day)
5. Click **Save and Test**

### Option B: Connect LinkedIn

1. Go to **Accounts** → **Add Account** → **LinkedIn**
2. Use the Chrome Extension to extract cookies + li_at token
3. Configure your proxy (LinkedIn requires one)
4. Set your **Activity Window** and weekly connection limits
5. Click **Save and Test**

{% hint style="warning" %}
**Important**: LinkedIn enforces stricter rate limits than X. Always use a dedicated residential proxy for LinkedIn accounts. See [Connecting Your LinkedIn Account](connect-linkedin.md) for details.
{% endhint %}

## Step 4: Build Your First Sequence

A **Sequence** is a workflow of actions (like, follow, send DM) that runs on your leads automatically.

1. Go to **Sequences** → **Create Sequence**
2. Give it a name (e.g., "First Time Demo Prospects")
3. Select the Offer you just created
4. Select the social account to use (X or LinkedIn)
5. Click **Build with Flow Builder**

### Add Steps to Your Flow

The Flow Builder is drag-and-drop. Common first steps:

- **Like Post**: Engage with a prospect's recent post (builds rapport)
- **Follow User**: Follow the account (gets on their radar)
- **Send DM**: Send a personalized message (start a conversation)
- **Wait**: Pause before the next action (e.g., wait 2 days)

Example flow for X:
```
1. Like Post (with engagement trigger)
2. Wait 1 day
3. Follow User
4. Wait 2 days
5. Send DM (AI-personalized)
```

6. Click **Save Draft** when done

{% hint style="info" %}
**Tip**: Keep your first sequence simple. You can always add more advanced steps (conditions, nested flows) later. A like → follow → DM sequence is the classic starting point.
{% endhint %}

## Step 5: Add Leads and Launch

Now add prospects to your sequence.

### Option A: Manual Search and Add

1. In your sequence, go to **Add Leads**
2. Search for prospects:
   - **X**: Use Tweet Search (keywords, hashtags)
   - **LinkedIn**: Use People Search or Content Search
3. Select prospects from results and click **Add to Sequence**

### Option B: Enable Autopilot (Recommended)

Autopilot finds and adds qualifying leads automatically based on your Offer.

1. In your sequence, go to **Settings** → **Autopilot**
2. Toggle **Enable Autopilot**
3. Autopilot will search for prospects matching your target audience and add them continuously

## Step 6: Launch and Monitor

1. In your sequence, click **Launch** (your sequence status changes from Draft to Active)
2. AutoReach starts running actions on your leads according to your workflow
3. Go to **Inbox** to see conversations and replies in real-time
4. Respond to replies manually, or enable AI auto-reply if you've set it up

{% hint style="info" %}
**Monitoring**: Check the Inbox daily. Replies are prioritized by likelihood of being a real prospect (our scoring system flags high-intent signals).
{% endhint %}

## What's Next?

Congratulations! Your first sequence is live. Here's what to explore next:

- **[Core Concepts](../core-concepts/offers.md)** — Deep dive into Offers, Sequences, and Leads
- **[Autopilot Guide](../autopilot/overview.md)** — How to find leads automatically
- **[AI Responses](../features/ai-responses.md)** — Set up smart auto-replies to save time
- **[Analytics](../analytics/dashboard.md)** — Track response rates, meetings booked, and ROI

Need help? Check our [FAQ](../help/faq.md) or email support@autoreach.tech.
