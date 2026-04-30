# Best Practices

Practical tips for getting the most out of AutoReach. Each section covers a key area of the platform with actionable advice you can apply immediately.

---

## Where to Focus First

If you only do five things, do these. Everything else is optimization.

1. **Spend 30 minutes on your Offer.** It drives lead scoring, message personalization, and AI responses. Vague offer = generic everything. → [Setting Up Your Offer](#1-setting-up-your-offer)
2. **Use intent-driven lead sources, not cold CSV imports.** Tweet/content search + lookalikes outscore mass imports. → [Finding the Right Leads](#2-finding-the-right-leads)
3. **Warm up new accounts for 1-2 weeks before outreach.** Cold DMs from a silent account get ignored or flagged. → [Account Safety](#6-account-safety)
4. **Start at 15-20 actions/day and ramp slowly.** Sudden spikes trigger bot detection. → [Account Safety](#6-account-safety)
5. **Run Simulation before launching any sequence.** Catch broken templates and weak personalization before 200 leads see them. → [Writing Better DMs](#4-writing-better-dms)

Skip ahead to [Common Mistakes to Avoid](#8-common-mistakes-to-avoid) if you want the same advice in negative form.

---

## Sections

| # | Section | When to read |
|---|---|---|
| 1 | [Setting Up Your Offer](#1-setting-up-your-offer) | Before launching anything |
| 2 | [Finding the Right Leads](#2-finding-the-right-leads) | Choosing discovery methods |
| 3 | [Building Effective Sequences](#3-building-effective-sequences) | Designing your outreach flow |
| 4 | [Writing Better DMs](#4-writing-better-dms) | Reply rate is low or you're tuning templates |
| 5 | [Managing Conversations](#5-managing-conversations) | Replies are coming in |
| 6 | [Account Safety](#6-account-safety) | Before launching, and weekly thereafter |
| 7 | [Measuring Success](#7-measuring-success) | Reading dashboards, deciding what to fix |
| 8 | [Common Mistakes to Avoid](#8-common-mistakes-to-avoid) | Quick troubleshooting checklist |

---

## 1. Setting Up Your Offer

Your Offer is the foundation that powers everything in AutoReach: lead discovery, scoring, DM personalization, and AI responses. Time spent here pays off across the entire platform.

- **Be specific about your target audience.** "VP of Demand Gen at B2B SaaS companies with $10M+ ARR" scores better than "marketing professionals." Include who to target, who to avoid, and any context that helps scoring.
- **Write detailed pain points.** Name the exact problems your buyers face: "Outbound outreach timing is guesswork" is more powerful than "help with sales." Pain points drive intent matching and message personalization.
- **Be specific in your description and pain points.** The more detailed your offer, the better AutoReach generates search keywords and matches leads via the Lead Pool.
- **Add your known competitors.** This helps AutoReach detect leads engaging with competitor content, which is one of the strongest intent signals.
- **Upload 3-5 high-quality knowledge base documents.** Case studies, pricing sheets, and objection-handling guides give the AI real context for conversations. A few focused documents outperform a large volume of generic content.
- **Review and update quarterly.** As you learn which types of companies convert, refine your target audience and pain points to match.

See [Creating Your First Offer](getting-started/create-offer.md) and [Offers & Knowledge Base](core-concepts/offers-and-knowledge-base.md).

---

## 2. Finding the Right Leads

Not all lead sources are equal. Prioritize quality and intent over volume.

- **Start with intent-driven sources.** X tweet search and LinkedIn content search find people actively discussing relevant topics. These leads carry inherent intent signals and score higher than cold imports.
- **Use LinkedIn people search for systematic targeting.** When you need specific roles at specific companies or in specific locations, people search gives you precise control.
- **Try lookalike audiences for scale.** Once you know which seed accounts attract your ideal buyers, lookalike discovery can tap into entire communities of relevant prospects.
- **Enable buyer expansion for continuous growth.** Buyer expansion runs daily, re-extracting followers from seed accounts and rotating through role-based searches so your pipeline never dries up.
- **Use the Lead Pool for instant results.** When you create a new offer, the Lead Pool delivers scored leads in seconds from pre-enriched profiles. Use it alongside other discovery methods, not as a replacement.
- **Aim for 100-200 quality leads to start.** It is better to run a tight campaign on highly-scored leads than to blast 1,000 random prospects. You can always scale up after seeing what works.
- **Include commenters in content searches.** People who comment on relevant posts often show stronger engagement and intent than passive readers.

See [Finding Leads Overview](finding-leads/overview.md).

---

## 3. Building Effective Sequences

Sequences are your outreach campaigns. Structure them to build familiarity before making a direct ask.

- **Lead with soft engagement.** Like a post, view a profile, or follow before sending a DM. This builds familiarity so the lead recognizes your name when your message arrives.
- **Keep sequences to 3-5 steps.** Longer sequences are not necessarily better. A focused flow of like, follow, then DM often outperforms complex 10-step campaigns.
- **Use conditions to branch intelligently.** On LinkedIn, always add a condition step after a connection request to check if it was accepted before sending a DM. This avoids wasting messages on unconnected leads.
- **Set appropriate delays between steps.** Same-day engagement followed by a next-day DM feels natural. A DM within minutes of a like feels automated.
- **Mind the total across sequences.** Daily limits are set per sequence, but your account's safe ceiling is a single number. If you run two sequences on the same account at 20/day each, that's 40 daily actions on the account — size each sequence's limit so the combined total stays within your account-level threshold. See [Account Safety](#6-account-safety) below for starting limits.
- **Use the simulation tool before launching.** Test your DM template with 3-5 different leads to check variable substitution, tone, and edge cases where data might be missing. See [Simulation & A/B Testing](outreach/simulation-and-testing.md).
- **Associate an offer with each sequence.** This connects your sequence to the right scoring and personalization context.

See [Building Sequences](outreach/building-sequences.md).

---

## 4. Writing Better DMs

Your first message determines whether a lead responds. Make it count.

- **Reference something specific.** Use `{{post}}` to reference a lead's recent content, or `{{current_role}}` and `{{company_name}}` to show you did your research. Generic messages get ignored.
- **Keep it to 50-100 words.** Short, direct messages with one clear question at the end outperform long pitches.
- **End with exactly one question.** A single, easy-to-answer question gives the lead a natural way to respond. Multiple questions feel overwhelming.
- **Avoid banned openers.** "Saw you..." and "Noticed you..." are overused. Open with a statement or insight instead.
- **Use the variable picker.** Browse available template variables in the flow editor rather than guessing syntax. The more lead data you reference, the more personalized the message feels.
- **Test with leads who have incomplete data.** Some leads may not have a company name or recent posts. Make sure your template still reads well when variables are missing.
- **Set a custom DM generation prompt for DM-specific instructions.** This is separate from the general AI prompt and lets you control cold DM tone independently from conversation replies.

See [DM Personalization](outreach/dm-personalization.md).

---

## 5. Managing Conversations

Conversations are where deals happen. Balance AI automation with personal touch.

- **Let AI handle the first 2-3 replies.** AI responses are stage-aware and handle common scenarios well: acknowledging interest, asking discovery questions, and handling basic objections.
- **Take over manually for hot prospects.** When a lead shows strong buying intent or asks detailed product questions, toggle AI off and respond personally. Your highest-value conversations deserve your direct attention.
- **Add tone examples from your best conversations.** When a conversation leads to a meeting, review the exchanges and add the best ones as tone examples. AutoReach auto-captures winning patterns, but manual curation improves quality.
- **Enable conversation follow-ups selectively.** Automatic follow-ups work well for mid-funnel leads who went silent. Set a 3-5 day wait with a max of 1-2 follow-ups to avoid being pushy.
- **Use the Conversation Analyzer monthly.** After you have enough data (20+ conversations), run the analyzer to identify patterns in what worked versus what did not, and apply the suggested improvements.
- **Review the AI's graceful exits.** When the AI detects a dead-end conversation, it exits respectfully. Review these to make sure the AI's exit language matches your style.

See [AI Response Engine](conversations/ai-response-engine.md), [Tone & Knowledge](conversations/tone-and-knowledge.md), and [Inbox](conversations/inbox.md).

---

## 6. Account Safety

Protecting your social accounts is non-negotiable. AutoReach has built-in protections, but your behavior matters too.

- **Warm up new accounts before outreach.** Run the Engagement Engine for at least a week on new or inactive accounts before launching sequences. Build a visible activity history first.
- **Use dedicated proxies.** Each social account should have its own proxy to avoid IP-based detection.
- **Start with conservative daily limits.** Begin at 15-20 actions per day and increase slowly over weeks, not days.
- **Monitor the Accounts page regularly.** Check error rates, cooldown status, and account health indicators. Catching issues early prevents escalation.
- **Respect emergency pauses.** When AutoReach pauses an account for bot detection or IP blocks, do not immediately resume. Wait for the full cooldown period and investigate the cause.
- **Keep your Chrome Extension active.** Session cookies expire. Keep the extension running to ensure your accounts stay connected.
- **Sign in to LinkedIn from one browser only.** LinkedIn rotates its session token (`li_at`) every time the same account signs in from a new browser, phone, or device. That rotation invalidates the cookies AutoReach holds and forces a reconnection. Pick one browser as your daily LinkedIn workspace and avoid logging in elsewhere. To audit existing sessions, open LinkedIn and go to **Settings & Privacy > Sign In & Security > Where you're signed in**, then end any sessions you do not actively use.
- **AutoReach's proxy will not appear in LinkedIn's "Where you're signed in" list.** This is normal. AutoReach reuses your browser's existing session cookie rather than logging in again, so no new session entry is created. As long as the Accounts page shows the account as active, the connection is healthy.
- **Do not run AutoReach and manual mass-actions simultaneously.** If you are manually liking 50 posts while AutoReach is also running engagement, the combined activity can trigger rate limits.

See [Account Safety](settings/account-safety.md) and [Engagement Engine Overview](engagement-engine/overview.md).

---

## 7. Measuring Success

Track the right metrics to know whether your outreach is working and when to adjust.

- **Reply rate is your primary signal.** A reply rate above 10% on cold DMs indicates good targeting and messaging. Below 5% means either your ICP is too broad or your message needs work.
- **Track meetings booked per week.** This is the ultimate outcome metric. If replies are high but meetings are low, your conversation AI or follow-up strategy needs adjustment.
- **Compare lead sources.** Check which discovery method (tweet search, LinkedIn search, lookalike, Lead Pool) produces the highest-scoring leads and best reply rates. Double down on what works.
- **Monitor your Active-to-Enrolled ratio.** If many Active leads are not being enrolled, check your auto-enrollment settings and sequence status.
- **Watch the Monitor-to-Active promotion rate.** A healthy pipeline has leads regularly graduating from Monitor to Active as new signals appear. If promotions are rare, your offer's pain points and target audience may need refinement.
- **Review AI response quality monthly.** Read through 10-20 AI-generated conversations to check for tone drift, missed objections, or generic responses.
- **Check cost per lead.** Use the cost estimation tool to understand your per-lead AI spend and optimize model selections for high-volume categories.

See [Pipeline Cost Estimation](settings/cost-estimation.md) and [AI Model Configuration](settings/ai-models.md).

---

## 8. Common Mistakes to Avoid

The top mistakes new users make and how to avoid them.

1. **Skipping the Offer setup.** A vague offer definition produces generic scoring, weak personalization, and irrelevant leads. Spend 30 minutes crafting a detailed offer before doing anything else.

2. **Importing thousands of cold CSV leads first.** CSV imports have no intent signals and require full enrichment. Start with intent-driven sources (tweet search, LinkedIn content search) that produce higher-scoring leads faster.

3. **Setting daily limits too high on new accounts.** Jumping to 100 actions per day on a fresh account is a fast path to getting flagged. Start at 15-20 and increase gradually over weeks.

4. **Ignoring the simulation tool.** Launching a sequence to 200 leads without testing your DM template is risky. Always simulate with 3-5 diverse leads first to catch issues with variable substitution, tone, and missing data.

5. **Leaving AI on for every conversation.** AI handles routine responses well, but your highest-value prospects deserve personal attention. Toggle AI off for conversations that show strong buying intent and handle them yourself.

6. **Never updating tone examples.** Tone examples define how your AI sounds. If you never add examples from real conversations, the AI relies on generic patterns. Add examples from your best conversations regularly.

7. **Running outreach without warming up accounts.** Sending cold DMs from an account with no recent activity looks suspicious. Run the Engagement Engine for at least a week first to build credibility.

8. **Using broad, untargeted searches.** Searching for generic terms like "marketing" produces thousands of irrelevant leads. Use specific intent phrases like "looking for a marketing automation tool" to find people with real buying signals.

9. **Forgetting to set up webhook integration.** Without a Calendly or Cal.com webhook, AutoReach cannot automatically detect booked meetings. Set up the webhook during onboarding to get automatic meeting tracking.

10. **Not reviewing the Buyers page.** When auto-enroll is off, scored leads appear on the Buyers page waiting for your review. Check it regularly to enroll high-quality leads and adjust your targeting based on what you see.
