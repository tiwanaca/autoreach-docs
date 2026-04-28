# Getting Results (Day 2 Guide)

You have launched your first sequence. Now what? This guide covers what to expect in the first 24-48 hours and how to iterate toward better results.

---

## What to Expect in the First 24-48 Hours

After starting a sequence, AutoReach begins executing actions according to the delays you configured in your flow. Here is a typical timeline:

- **Immediately**: The first step (usually a like) starts executing for enrolled leads
- **Within minutes to hours**: Subsequent steps fire according to the delays between nodes (e.g., follow after 15 minutes, DM after 1 day)
- **Within 24 hours**: Your first DMs go out (assuming a 1-day delay before messaging)
- **24-48 hours after DMs**: First replies start arriving

Do not expect instant results. Social outreach is a slow burn - most prospects need to see your name a few times before they engage.

> **Tip:** Check the Activity Feed on the **Dashboard** to see exactly what actions AutoReach has completed and when.

---

## Reading Your First Results

Open your dashboard to see your pipeline metrics. The key numbers to watch early on are:

- **Contacted** - confirms DMs are actually being delivered
- **Replied** - the metric that matters most; aim for 5-15% reply rates on cold outreach
- **Meetings Booked** - the ultimate conversion (this may take a few days to appear)

If you see "Contacted" climbing but "Replied" stuck at zero after 48 hours, see the troubleshooting section below.

---

## When Replies Come In

Replies appear in your **Inbox** (Conversations section). Each reply shows:

- The lead's profile information
- The full conversation thread
- The AI's suggested response (if AI responses are enabled)

### Handling Conversations

- **AI is on by default**: If you left AI responses enabled, AutoReach will automatically reply to incoming messages using your offer context and tone examples. Review the AI's responses early on to make sure the tone matches what you want.
- **Take over manually**: Click on any conversation to read the thread. You can toggle AI off for that conversation and respond yourself whenever a lead shows genuine buying interest.
- **Add tone examples**: If the AI's tone is not quite right, go to your sequence settings and add tone examples - these teach the AI how you actually talk.
- **Meeting tracking**: When a lead books a call through your Calendly or Cal.com link, AutoReach automatically marks the lead as Meeting Booked via webhook. If you use a custom booking URL (no webhook), open the lead in the Chrome Extension CRM panel and drag it to the Meeting stage so the metrics update.

> **Tip:** For your first few days, manually review every AI response before the next one goes out. This helps you tune the AI's style and catch anything off-brand.

---

## Adjusting Your Sequence if Reply Rates Are Low

If your reply rate is below 3% after the first 50-100 DMs, try these adjustments:

### Check Your Message Quality
Use the **Simulation** feature to preview what your DMs look like for specific leads. If they sound generic, add more personalization to your DM template or refine your AI prompt.

### Check Your Targeting
Review your scored leads. If most leads have low buyer scores, your ICP definition may be too broad. Tighten your offer's target audience, pain points, and qualifying criteria.

### Add a Warmup Before the DM
If you are going straight to DM, consider adding engagement steps first (like, follow, reply to a post). Leads are more likely to respond to someone whose name they recognize.

### Adjust Timing
If your DMs are going out at odd hours, review your activity window settings. Messages sent during business hours tend to get higher response rates.

### Try a Different Channel
If X DMs are not working, try LinkedIn (or vice versa). Some audiences are more responsive on one platform than the other.

---

## When to Add More Leads

Add more leads when:

- Your current batch is mostly processed (most leads have reached the end of the sequence)
- Your reply rate is healthy (3%+ for cold outreach) and you want more volume
- You have refined your messaging and are confident in the quality

You can add leads from any source: run a new search, import a CSV, or let Autopilot find them automatically.

> **Warning:** Do not add thousands of leads to a brand new sequence. Start with 50-100 leads, verify your messaging works, then scale up.

---

## Setting Up Autopilot

Once your manual sequences are performing well, enable Autopilot to automate the growth loop:

1. **Auto-Enrollment**: Automatically enroll newly scored leads into your active sequence. Go to the sequence settings and enable auto-enrollment with a minimum buyer score threshold.
2. **Buyer Expansion**: Enable daily recurring searches or follower extractions to continuously find new leads that match your ICP.
3. **AI Responses**: If you are comfortable with how the AI handles conversations, leave it enabled for hands-free follow-up.

See [Autopilot Overview](../autopilot/overview.md) for full details.

---

## Enabling the Engagement Engine

The Engagement Engine builds your brand presence by engaging with relevant content on X and LinkedIn. It operates separately from sequences and does not send DMs - it likes and comments on posts from people in your target audience.

Why this matters:

- Leads are more likely to reply to someone they have seen engaging thoughtfully in their feed
- Consistent engagement builds credibility and warms up your accounts
- It runs automatically in the background

Enable it from your account's detail page (go to **Accounts**, click your account, and find the Engagement Engine section). Start with approval mode so you can review each engagement before it goes out.

See [Engagement Engine Overview](../engagement-engine/overview.md) for setup instructions.

---

## Common "Why Isn't This Working?" Scenarios

### "My sequence is active but no actions are happening"
- Check that your connected accounts are healthy (no paused or error status on the **Accounts** page)
- Verify you have leads enrolled in the sequence (open the sequence and check the Leads tab)
- Check your activity window - actions only execute during your configured hours
- Make sure your daily action limits have not been reached for today

### "DMs are sending but nobody is replying"
- Review message quality with Simulation - personalization may be weak
- Check that your leads are relevant (high buyer scores)
- Verify your DMs are not landing in spam (check from the recipient's perspective if possible)
- Consider adding warmup steps before the DM
- Wait at least 48 hours - some people take time to respond

### "Leads are not getting scored"
- Verify your offer is fully configured with ICP details, pain points, and qualifying criteria
- Check the health warnings on the Dashboard - your API keys may have run out of credits
- Look at the lead's profile - if enrichment has not completed, scoring cannot run yet

### "AI messages look generic or off-brand"
- Add tone examples to your sequence (go to the Tone Examples section in sequence settings)
- Customize the AI prompt and DM generation prompt with specific instructions
- Use the Simulation tool to iterate on message quality before sending

### "Account shows a warning or paused status"
- Check the account health card on the **Accounts** page for the specific error
- If rate-limited, AutoReach automatically applies cooldown periods to protect your account. Wait for the cooldown to expire
- If cookies expired, reconnect via the Chrome Extension (click three dots > Reconnect)
- Review the [Account Safety](../settings/account-safety.md) guide for prevention tips

---

## Next Steps

- **[Building Sequences](../outreach/building-sequences.md)**: Refine your sequence flow and add new steps
- **[DM Personalization](../outreach/dm-personalization.md)**: Improve your DM templates and AI prompts
- **[Simulation & A/B Testing](../outreach/simulation-and-testing.md)**: Preview messages before sending
- **[Autopilot Overview](../autopilot/overview.md)**: Automate lead discovery and enrollment
- **[Engagement Engine](../engagement-engine/overview.md)**: Build brand presence through content engagement
