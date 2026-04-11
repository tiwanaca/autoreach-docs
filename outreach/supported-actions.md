# Supported Actions by Platform

AutoReach supports a range of actions across X (Twitter) and LinkedIn. This reference shows what's available on each platform and how each action works.

## Actions Reference Table

| Action | X | LinkedIn | Description |
|--------|---|----------|-------------|
| **Send DM** | ✓ | ✓ | Direct message |
| **Like Post** | ✓ | ✓ | Like a post |
| **Reply/Comment** | ✓ | ✓ | Reply to a post |
| **Follow/Connect** | ✓ | ✓ | Follow on X; connect on LinkedIn |
| **View Profile** | ✗ | ✓ | View a profile (LinkedIn only) |
| **Remove Connection** | ✗ | ✓ | Remove connection (LinkedIn only) |

## Action Details

### Send DM

**Platforms:** X ✓ | LinkedIn ✓

Send a direct message to a lead. The message is personalized using template variables, lead enrichment data, and your knowledge base context.

**When to use:**
- As the main call-to-action in your sequence
- After soft engagement (Like/Follow) to feel less cold
- In conditional branches for targeted messaging

**Typical delay:** 2–5 days after initial engagement

**Example:**
```
Hi {{first_name}},

I saw your recent post about {{topic}}.
We help {{company_size}} companies like {{company}} improve {{pain_point}}.

Worth exploring together?

—{{user_name}}
```

{% hint style="info" %}
DMs are fully AI-personalized. See [Cold DM Generation](cold-dm-generation.md) for rules and best practices.
{% endhint %}

---

### Like Post

**Platforms:** X ✓ | LinkedIn ✓

Like a lead's recent post. A soft engagement signal that shows interest without being intrusive.

**When to use:**
- First action in "soft engagement" sequences
- Early relationship-building
- Avoid immediately before a DM (feels stalky)

**Typical delay:** 0–1 day

**Example sequence flow:**
```
[Like Post] → [Wait 1 Day] → [Follow] → [Wait 2 Days] → [Send DM]
```

{% hint style="info" %}
Liking your target's post is one of the highest-reply-rate openers. Use it.
{% endhint %}

---

### Reply/Comment

**Platforms:** X ✓ | LinkedIn ✓

Reply to a public post with a thoughtful comment. More visible than a DM; builds credibility by engaging publicly.

**When to use:**
- To demonstrate expertise in your field
- When the post topic aligns perfectly with your offer
- As an alternative to DM for thought leaders and influencers

**Typical delay:** 1–2 days (don't reply immediately after publish)

**Example:**
```
Great point about {{post_topic}}. We've seen this challenge with our clients in {{industry}}. 
The key is {{your_insight}}. DM me if you want to dig deeper.
```

{% hint style="warning" %}
Comments are public and visible to all followers. Keep them professional and valuable—never salesy.
{% endhint %}

**Platform-specific behavior:**
- **X:** Replies appear in the thread and trigger notifications
- **LinkedIn:** Comments appear on the post; higher engagement rates typically

---

### Follow/Connect

**Platforms:** X ✓ | LinkedIn ✓

Follow on X or send a connection request on LinkedIn. Builds awareness and reciprocal following before outreach.

**When to use:**
- Mid-sequence, between soft engagement and DM
- To increase follower count and social proof
- As a low-friction way to stay top-of-mind

**Typical delay:** 1–3 days after Like Post

**Platform-specific behavior:**
- **X:** Instant follow; no approval needed
- **LinkedIn:** Sends connection request; lead must accept. If rejected, marked as failed; if accepted, lead is connected

{% hint style="info" %}
On LinkedIn, connection requests are subject to weekly limits. See [Scheduling & Send Limits](scheduling.md) for rate limits.
{% endhint %}

---

### View Profile

**Platforms:** X ✗ | LinkedIn ✓

Visit a lead's profile (LinkedIn only). A subtle signal of interest; useful for research or to trigger profile notifications.

**When to use:**
- Before connecting to show interest
- To gather additional context before messaging
- Light touch if a lead seems hesitant

**Typical delay:** Same day or 1 day before Connect

{% hint style="info" %}
LinkedIn's algorithm may notify users of profile views. This can warm them before your connection request.
{% endhint %}

---

### Remove Connection

**Platforms:** X ✗ | LinkedIn ✓

Remove a connection (LinkedIn only). Useful for cleaning up non-responders and keeping your network focused.

**When to use:**
- At the end of a sequence if no engagement
- To avoid spamming leads with repeated outreach
- To maintain a high-quality network

**Typical delay:** 7–14 days after final outreach attempt

**Example workflow:**
```
[Send DM] → [Wait 3 Days] → [Condition: Replied?]
             ├─ YES → [Send Follow-up]
             └─ NO  → [Wait 4 Days] → [Remove Connection]
```

{% hint style="warning" %}
Removing connections is permanent. Only use for leads you're confident won't convert.
{% endhint %}

---

## Action Lifecycle

Every action in a sequence moves through these states:

| State | Meaning |
|-------|---------|
| **Pending** | Waiting for scheduled time to arrive |
| **Queued** | Scheduled time reached; waiting for execution window |
| **In Progress** | Being executed (usually <1 second) |
| **Completed** | Successfully executed |
| **Failed** | Action could not be completed (e.g., LinkedIn rejected connection request) |
| **Skipped** | Action was bypassed (e.g., rate limit reached; will retry tomorrow) |
| **Deferred** | Special state for rate-limited connection requests; resumes next Monday |

{% hint style="info" %}
You can view the status of each action for each lead in the sequence details view. Failed actions can be retried manually.
{% endhint %}

---

## Rate Limiting & Anti-Burst Protection

AutoReach respects platform limits to keep your accounts healthy.

### DM Limits
- **Daily limit:** Configurable per sequence (typically 20–50/day)
- **Effect:** Actions exceeding daily limit are queued for next day

### Connection Request Limits (LinkedIn)
- **Free/Premium accounts:** 100 requests/week
- **Sales Navigator:** 200 requests/week
- **Effect:** Requests hitting limit go into **Deferred** state and auto-resume Monday morning

### Anti-Burst Protection
When you restart a paused sequence, AutoReach spaces out re-activated actions by **15–25 minutes** to avoid sudden spikes that trigger platform anti-spam filters.

{% hint style="warning" %}
Platform limits are enforced per account, not per sequence. If you run multiple sequences, they share the same daily limits. Plan accordingly.
{% endhint %}

---

## Deferred Actions

If a LinkedIn connection request hits the weekly limit, it enters **Deferred** state:

- The action is automatically retried the following **Monday morning**
- You don't need to do anything; AutoReach resumes it
- The lead stays in the sequence (not removed)
- Other actions in the sequence continue normally

This ensures high-quality connection requests stay in your queue and get sent when limits reset.

---

## Action Tips

1. **Space actions 1–3 days apart** – Feels natural; reduces rate limiting
2. **Lead with soft engagement** – Like/Follow/View Profile build social proof
3. **Use conditions smartly** – Different paths for engaged vs. cold leads
4. **Remove dead leads late** – After 7+ days of no engagement
5. **Mix action types** – Variety feels less automated
6. **Respect platform-specific limits** – Don't exceed 100+ connection requests on standard LinkedIn
7. **Preview before sending** – Use the Simulator to test action sequences with real leads

## Next Steps

- Learn [Building Sequences](building-sequences.md) to combine actions into campaigns
- See [Cold DM Generation](cold-dm-generation.md) for message best practices
- Explore [Scheduling & Send Limits](scheduling.md) for rate limit details
