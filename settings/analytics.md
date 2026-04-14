# Analytics and Reporting

AutoReach provides a comprehensive analytics suite to help you understand your outreach performance, track AI spending, and monitor account health. All analytics are accessible from the dashboard and the Analytics section of the app.

---

## Dashboard Overview

The main dashboard shows your key pipeline metrics at a glance:

| Metric | What It Measures |
|---|---|
| **Pipeline Created** | Total leads in your account (across all sources) |
| **Buyers Identified** | Leads scored as qualified buyers by the intelligence engine |
| **Outreach Delivered** | Leads who have been contacted |
| **Meetings Generated** | Total meetings booked through your calendar link |

A **potential pipeline** value is displayed in the hero section, showing estimated revenue from qualified leads based on your offer's deal size.

These numbers update in real time as your sequences run and leads progress through the pipeline.

---

## Daily Summary

The daily summary gives you a snapshot of today's activity across all your sequences and the Engagement Engine:

- **DMs sent** - how many direct messages went out today
- **Comments/replies posted** - engagement actions on lead posts
- **Likes** - posts liked as part of sequences or warmup
- **Follows** - new accounts followed (X only)
- **Connection requests** - LinkedIn connection requests sent
- **Profile views** - LinkedIn profiles viewed
- **Total actions** - combined count of all actions today

This summary appears as a **toast notification** when you open the app, giving you a quick snapshot of today's activity.

---

## Activity Feed

The activity feed is a chronological log of every completed action across your account. It shows:

- **What happened** - the action type (like, DM, reply, follow, connection request, profile view)
- **Who it was for** - the lead's name and username
- **Which sequence** - the sequence that triggered the action (or "Engagement Engine" for warmup actions)
- **Platform** - whether it happened on X or LinkedIn
- **When** - the exact timestamp
- **Preview** - a snippet of the message sent or the post engaged with

The feed combines both sequence actions and Engagement Engine activity into a single timeline, sorted newest first. Use it to review what AutoReach has been doing on your behalf and spot-check message quality.

---

## Sequence Performance

Each sequence has its own performance view showing:

- **Lead status breakdown** - how many leads are at each stage (pending, active, contacted, replied, meeting booked, completed)
- **Step-level analytics** - completion counts for each step in your flow (e.g., how many likes sent, how many DMs delivered)
- **Reply rate** - percentage of contacted leads who responded
- **Meeting rate** - percentage of contacted leads who booked a meeting
- **Conversion funnel** - visual breakdown from enrolled leads through to meetings

Access sequence performance by clicking on any sequence in the Sequences list.

---

## AI Usage Tracking

AutoReach tracks every AI call made on your behalf so you can monitor token consumption and costs.

### Usage Summary

The AI Usage panel on the Dashboard shows aggregate stats for a configurable time period (up to 90 days):

- **Total tokens used** - prompt tokens (input) and completion tokens (output)
- **Total cost** - estimated cost in USD based on model pricing
- **Breakdown by action** - which activities consumed the most tokens (scoring, DM generation, replies, classification, etc.)
- **Breakdown by model** - cost split across different AI models (GPT, Claude, etc.)
- **Daily trend** - a day-by-day chart of token usage and cost

### Recent Activity Log

Below the summary, a scrollable log shows individual AI calls with:

- The action that triggered it (e.g., "DM generation", "buyer scoring", "keyword generation")
- Which model was used
- Token counts (prompt and completion)
- Cost for that specific call
- Timestamp

This helps you identify which activities are driving your AI costs and whether any particular action is unusually expensive.

---

## AI Health Monitoring

AutoReach monitors the health of your AI providers in real time. If both your primary and fallback AI models fail (for example, due to exhausted API credits or a provider outage), a warning banner appears on your dashboard.

The warning includes:

- **What happened** - whether it is a quota issue or a provider error
- **Which provider** - the affected AI service
- **When** - when the issue was first detected

You can dismiss the warning once you have resolved the issue (e.g., added credits to your API account).

> **Tip:** Enable auto-recharge on both your OpenAI and Anthropic accounts to prevent quota exhaustion from interrupting your outreach.

---

## Account Health Monitoring

A health banner on the Dashboard alerts you when a connected account has issues. It shows the account's status and the reason for any problems (rate limit, bot detection, auth error, etc.). A healthy account shows no banner.

---

## LinkedIn Pipeline Analytics

If you use the Chrome Extension CRM pipeline for LinkedIn, additional analytics are available:

- **Funnel stages** - leads broken down by stage (new, requested, accepted, contacted, replied, meeting, won, lost)
- **Needs follow-up** - how many leads are overdue for a follow-up message
- **Reply rate** - percentage of contacted leads who replied
- **Meeting rate** - percentage of contacts that converted to meetings

---

## Next Steps

- **[Cost Estimation](cost-estimation.md)**: Estimate costs before running a pipeline
- **[AI Model Configuration](ai-models.md)**: Change which models are used to optimize cost vs. quality
- **[Account Safety](account-safety.md)**: Adjust rate limits and safety settings
