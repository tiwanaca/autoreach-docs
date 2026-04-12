# Enabling Autopilot

Enabling Autopilot is a single-click process that sets up your entire automation infrastructure in the background. Here's what happens behind the scenes.

## The Enable Workflow

When you click "Enable Autopilot," a series of steps execute automatically:

### Step 1: Fetch and Score Initial Leads

AutoReach fetches **100 leads** from the database (populated during offer creation) and scores them against your Offer criteria using buyer intelligence scoring.

### Step 2: Start a Role-Based LinkedIn Search

Launches **1 search based on role** on LinkedIn to find prospects matching your ICP. This targets decision-makers at companies that fit your target audience.

### Step 3: Find a Lookalike Account

Identifies **1 lookalike**, an influencer or thought leader in your space, and starts a search on their followers to discover high-intent prospects.

### Step 4: Start an Intent Signal Search

Launches a search for prospects showing **buying signals**: people actively posting about topics related to your offer.

### Step 5: Create and Start Your First Sequence

Creates your first outreach sequence with the right workflow for your platform and **starts it immediately**. Leads that score high enough are enrolled automatically.

### Step 6: Enable Auto-Enrollment and Buyer Expansion

- **Auto-enroll buyers** is turned ON in settings. All ready buyers found by the system are automatically added to the sequence and will not appear on the Buyers page.
- **Buyer Expansion** is enabled on all searches. They will run every day to keep your pipeline full.

{% hint style="info" %}
**The Buyers page** shows buyers before they are added inside a sequence. When auto-enroll is ON (default with Autopilot), ready buyers go straight into the sequence instead.
{% endhint %}

## Timeline and Progress

The entire setup process takes **1-2 minutes** and runs in the background using Redis-backed progress tracking.

{% hint style="success" %}
**You don't have to wait.** Enabling Autopilot returns immediately. You can navigate away, and the setup continues in the background. Progress indicators on the dashboard show you when each component is ready.
{% endhint %}

## What to Expect After Enabling

Once Autopilot is active, you'll see:

- **Autopilot dashboard updates**: Active leads, daily searches, and sequence stats
- **First content generated**: AI tweets scheduled for the next 7 days
- **Searches beginning**: Initial lead discovery running
- **Engagement starting**: Auto-likes and follows on relevant posts

## Monitoring Setup Progress

Check the **Autopilot dashboard** to see:

- Real-time stats on active leads and sequences
- Content calendar for upcoming posts
- Engagement activity logs
- Search and expansion status

{% hint style="warning" %}
**First leads may take time.** Discovery, enrichment, and scoring are fast, but your first enrolled leads typically appear within the first 24 hours as searches and scoring accumulate results.
{% endhint %}

## Next Steps

After enabling Autopilot:

1. Review your generated content strategy in the **Content tab**
2. Check your **sequences** to see the workflows created
3. Monitor the **Activity log** to watch leads flow through the system
4. Respond to opportunities in your **Inbox**

You're now running full B2B outreach automation. Autopilot handles the heavy lifting while you focus on closing deals.
