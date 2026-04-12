# Buyer Expansion

Buyer Expansion is how Autopilot discovers new prospects automatically. Every 24 hours, it mines your best-performing accounts to find more people like them—without requiring manual prospecting.

{% hint style="info" %}
**When Autopilot is enabled**, all searches are automatically set with Buyer Expansion turned ON. This means they will run every day to keep your pipeline full with fresh leads.
{% endhint %}


## How Expansion Works

When you enable Autopilot, it:

1. Identifies top-performing accounts in your space (thought leaders, competitors, etc.)
2. Extracts their followers as new prospects
3. Rotates to fresh accounts every 24 hours
4. Keeps your pipeline flowing with new leads

Expansion is always running in the background, so you never manually have to say "find me more people like this."

## X/Twitter Expansion

On X, Autopilot:

1. **Monitors target accounts** — Watches accounts you've flagged with `buyer_expansion: true`
2. **Calculates daily batches** — Determines how many followers to extract (100–200 per day)
3. **Increments extraction goals** — Tracks progress toward full follower extraction
4. **Adds random delay** — Waits 0–6 hours before triggering extraction (spreads activity naturally)
5. **Detects exhaustion** — If an account's followers are fully extracted, automatically disables expansion for that account

This ensures you're continuously discovering new X prospects while staying within platform limits.

{% hint style="info" %}
**Why X expansion matters:** X users often self-identify around your space. Followers of thought leaders, competitors, and industry accounts are pre-filtered for relevance.
{% endhint %}

## LinkedIn Expansion

On LinkedIn, Autopilot takes a role-based approach:

1. **Rotates through priority roles** in order:
   - CEO
   - CTO
   - CFO
   - COO
   - Founder
   - VP Sales
   - VP Engineering
   - Director
   - Manager

2. **Automatically moves to the next role** when pagination runs out on the current role
3. **Resets pagination** when starting a new role
4. **Continuously updates** existing enriched profiles in your database

This means you systematically build a prospect list across all decision-maker levels without manual configuration.

{% hint style="success" %}
**Role rotation is smart.** By cycling through roles, you discover different buyer personas at target companies—not just CEOs.
{% endhint %}

## Exhaustion Detection

Both X and LinkedIn expansion include automatic **exhaustion detection**:

- **X accounts:** Once all followers are extracted, Autopilot stops expanding that account
- **LinkedIn roles:** Once pagination completes a role, Autopilot moves to the next priority role
- **Exhaustion logging:** You're notified when an expansion source is fully depleted

This prevents wasted effort on accounts or roles you've already fully mined.

## Daily Expansion Volume

Typical expansion brings in:

- **X:** 100–200 new followers per account per day
- **LinkedIn:** 50–150 new prospects per role per day

Combined, Autopilot can add **200–350+ new prospects daily** without manual work.

## Keeping Your Pipeline Fresh

Expansion runs **every 24 hours**, ensuring:

- New leads enter your scoring pipeline continuously
- You never "run out" of prospects in your ICP
- Your outreach is always working with fresh data
- Supply matches demand (more leads as you convert)

## Monitoring Expansion Activity

Check expansion status:

1. Go to **Autopilot Dashboard**
2. View **Expansion Stats:**
   - Total leads discovered (cumulative)
   - Daily new leads from expansion
   - Active expansion accounts/roles
   - Exhaustion status

3. Check **Activity Log** to see real-time expansion events

## Expansion and Your Lead Pool

Every new prospect discovered via expansion:

1. Is enriched with profile data
2. Enters real-time lead scoring
3. Is matched against your Offer criteria
4. Qualifies or disqualifies based on ICP

High-scoring expansion leads auto-enroll into sequences within minutes.

## How Expansion Feeds the Outreach Loop

```
Expansion discovers new leads
         ↓
Real-time scoring evaluates them
         ↓
Auto-enrollment moves score 60+ to sequences
         ↓
Sequences run outreach campaigns
         ↓
Replies come in → moved to Inbox
         ↓
You close deals
```

Expansion is the top of the funnel that never stops flowing.

{% hint style="warning" %}
**Expansion respects platform limits.** Autopilot spreads extraction across time windows and uses random delays to stay under the radar. This keeps your account safe while maximizing new leads.
{% endhint %}

## Can I Control Expansion?

You can adjust:

- **Priority roles** — Customize the LinkedIn role rotation order
- **Expansion accounts** — Add/remove accounts to expand from
- **Expansion frequency** — Speed up or slow down (default: every 24 hours)
- **Pause expansion** — Temporarily stop expansion without disabling Autopilot

Go to **Autopilot Settings > Expansion** to customize.

## Common Questions

**Q: Where do expansion leads come from?**  
A: Followers of accounts you've flagged for expansion + LinkedIn users in priority roles at target companies.

**Q: Are expansion leads warm?**  
A: Warmer than cold database lists, yes. They follow relevant accounts or work at target companies. But they're not pre-qualified—that's what scoring does.

**Q: Can I expand from my competitors?**  
A: Absolutely. Many users add competitor accounts as expansion sources to build lookalike audiences.

**Q: What if I run out of followers to extract?**  
A: Autopilot detects exhaustion and disables that source. You can add new expansion accounts to keep it going, or let Autopilot cycle to the next priority role.

---

Expansion turns your best-performing accounts into a lead generation machine. Let Autopilot do the mining while you focus on selling.
