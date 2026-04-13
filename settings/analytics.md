# Analytics and Reporting

AutoReach provides a comprehensive analytics suite to help you understand your outreach performance, track AI spending, and monitor account health. All analytics are accessible from the dashboard and the Analytics section of the app.

---

## Dashboard Overview

The main dashboard shows your key pipeline metrics at a glance:

| Metric | What It Measures |
|---|---|
| **Total Leads** | All leads in your account (across all sources) |
| **Qualified Leads** | Leads scored as active buyers by the intelligence engine |
| **Sequence Leads** | Leads currently enrolled in sequences |
| **Contacted** | Leads who have received a DM or message |
| **Replied** | Leads who have responded to your outreach |
| **Meetings Booked** | Leads who scheduled a meeting through your calendar link |
| **Pipeline Value** | Estimated revenue from qualified leads, based on your offer's deal size |

These numbers update in real time as your sequences run and leads progress through the pipeline.

---

## Daily Summary

The daily summary gives you a snapshot of today's activity across all your sequences and the Engagement Engine:

- **DMs sent** -- how many direct messages went out today
- **Comments/replies posted** -- engagement actions on lead posts
- **Likes** -- posts liked as part of sequences or warmup
- **Follows** -- new accounts followed (X only)
- **Connection requests** -- LinkedIn connection requests sent
- **Profile views** -- LinkedIn profiles viewed
- **Total actions** -- combined count of all actions today

This summary appears as a notification card so you can quickly see how active your outreach has been.

---

## Activity Feed

The activity feed is a chronological log of every completed action across your account. It shows:

- **What happened** -- the action type (like, DM, reply, follow, connection request, profile view)
- **Who it was for** -- the lead's name and username
- **Which sequence** -- the sequence that triggered the action (or "Engagement Engine" for warmup actions)
- **Platform** -- whether it happened on X or LinkedIn
- **When** -- the exact timestamp
- **Preview** -- a snippet of the message sent or the post engaged with

The feed combines both sequence actions and Engagement Engine activity into a single timeline, sorted newest first. Use it to review what AutoReach has been doing on your behalf and spot-check message quality.

---

## Sequence Performance

Each sequence has its own performance view showing:

- **Lead status breakdown** -- how many leads are at each stage (pending, active, contacted, replied, meeting booked, completed)
- **Step-level analytics** -- completion counts for each step in your flow (e.g., how many likes sent, how many DMs delivered)
- **Reply rate** -- percentage of contacted leads who responded
- **Meeting rate** -- percentage of contacted leads who booked a meeting
- **Conversion funnel** -- visual breakdown from enrolled leads through to meetings

Access sequence performance by clicking on any sequence in the Sequences list.

---

## AI Usage Tracking

AutoReach tracks every AI call made on your behalf so you can monitor token consumption and costs.

### Usage Summary

The AI Usage page shows aggregate stats for a configurable time period (up to 90 days):

- **Total tokens used** -- prompt tokens (input) and completion tokens (output)
- **Total cost** -- estimated cost in USD based on model pricing
- **Breakdown by action** -- which activities consumed the most tokens (scoring, DM generation, replies, classification, etc.)
- **Breakdown by model** -- cost split across different AI models (GPT, Claude, etc.)
- **Daily trend** -- a day-by-day chart of token usage and cost

### Recent Activity Log

Below the summary, a paginated log shows individual AI calls with:

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

- **What happened** -- whether it is a quota issue or a provider error
- **Which provider** -- the affected AI service
- **When** -- when the issue was first detected

You can dismiss the warning once you have resolved the issue (e.g., added credits to your API account).

> **Tip:** Enable auto-recharge on both your OpenAI and Anthropic accounts to prevent quota exhaustion from interrupting your outreach.

---

## Account Health Monitoring

The account status view shows the health of every connected X and LinkedIn account:

- **Active/Paused status** -- whether the account is running or paused
- **Pause reason** -- if paused, why (rate limit, bot detection, auth error, etc.)
- **Today's actions** -- how many actions have been performed today
- **Error indicators** -- whether errors have occurred in the last 24 hours and what the most recent error was

This is your first place to check if something seems wrong with your outreach. A healthy account shows as active with zero errors.

---

## LinkedIn Pipeline Analytics

If you use the LinkedIn pipeline, additional analytics are available:

- **Funnel stages** -- leads broken down by stage (new, requested, accepted, contacted, replied, meeting, won, lost)
- **Needs follow-up** -- how many leads are overdue for a follow-up message
- **Reply rate** -- percentage of contacted leads who replied
- **Meeting rate** -- percentage of contacts that converted to meetings
- **Last pipeline run** -- when the pipeline last processed new activity

---

## Next Steps

- **[Cost Estimation](cost-estimation.md)**: Estimate costs before running a pipeline
- **[AI Model Configuration](ai-models.md)**: Change which models are used to optimize cost vs. quality
- **[Account Safety](account-safety.md)**: Adjust rate limits and safety settings
