# Frequently Asked Questions

Answers to the most common questions about AutoReach. For detailed guides, follow the links to the relevant documentation pages.

---

## Getting Started

### How do I get started with AutoReach?

Sign up at [autoreach.tech](https://autoreach.tech), add your AI API keys (OpenAI required, Anthropic recommended), connect at least one social account through the Chrome Extension, create an Offer, and start Autopilot. The onboarding wizard walks you through each step. See the [Quickstart](getting-started/quickstart.md) for a full walkthrough.

### Do I need both X and LinkedIn accounts connected?

No. You need at least one social account connected to use AutoReach. You can connect X only, LinkedIn only, or both. Connecting both platforms gives you cross-platform profile matching and more outreach options.

### How much should I load onto my AI API keys?

We recommend at least $30 on both OpenAI and Anthropic, with auto-recharge enabled on both platforms. This ensures AutoReach never stops working due to depleted credits. Your actual usage depends on how many leads you process and which models you select.

### Can I use AutoReach without Autopilot?

Yes. Autopilot is a convenience feature that automates initial setup. You can manually create searches, build sequences, score leads, and manage everything yourself. Autopilot simply handles the initial configuration so you can get started faster.

---

## Finding Leads

### Where do leads come from?

AutoReach discovers leads from multiple sources: X tweet search, LinkedIn content search, LinkedIn people search, LinkedIn job search, lookalike audience discovery, follower extraction, comment extraction, the Lead Pool, CSV import, manual add, and the Chrome Extension. See [Finding Leads](finding-leads/overview.md) for a breakdown of each method.

### How many leads should I target at once?

Quality matters more than quantity. Start with 100-200 leads from intent-driven sources (tweet search or LinkedIn content search) rather than thousands from bulk imports. Leads found through keyword searches carry inherent intent signals and score higher than cold imports that need full enrichment from scratch.

### Can I import leads from a CSV file?

Yes. Go to the Leads page and use the CSV Import feature. You can import leads with X handles, LinkedIn URLs, or email addresses. Imported leads are queued for full enrichment and scoring. Duplicate detection prevents the same lead from being added twice.

### What is the Lead Pool?

The Lead Pool is a shared database of pre-enriched lead profiles stored as vector embeddings. When you create an offer, AutoReach uses semantic similarity to instantly match existing profiles against your ICP. This is the fastest way to get scored leads because they skip enrichment entirely. See [Lead Pool](finding-leads/lead-pool.md) for details.

### Can I export my leads to CSV?

Yes. You can export leads from the All Leads page or the Buyers page. Use the export controls to download your lead data as a CSV file.

---

## Scoring and Buyers

### How does buyer scoring work?

AutoReach scores each lead across three dimensions: Fit (does this person match your ICP?), Intent (are they actively looking for a solution?), and Timing (is this the right moment to reach them?). These combine into a single Buyer Score from 0-100 that determines the lead's buyer state. See [Buyer Intelligence & Scoring](core-concepts/buyer-intelligence.md) for the full breakdown.

### Why is a lead scored as Poor Fit?

A lead lands in Poor Fit when their Buyer Score is low. This usually means they have a significant mismatch with your ICP, such as wrong industry, wrong seniority, or wrong company size. Check the scoring breakdown to see which dimension scored lowest. Poor Fit leads are still monitored and can be promoted if new signals appear, like a job change or new social activity. See [Buyer Intelligence](core-concepts/buyer-intelligence.md) for details.

### Can a lead's score change over time?

Yes. Scores are not static. They update when new signals are detected (a relevant post, a job change, company funding), when you update your offer definition, or when you trigger a manual rescore. The resurfacing scheduler automatically rechecks Monitor and Poor Fit leads on a regular cycle. See [Continuous Operations](autopilot/continuous-operations.md).

### What is the difference between Active and Monitor buyer states?

Active leads are ready for outreach and eligible for automatic enrollment into sequences. Monitor leads have potential but are not quite ready - perhaps strong fit but weak intent. Monitor leads are automatically rechecked on a regular schedule and promoted to Active if their score improves. See [Buyer Intelligence](core-concepts/buyer-intelligence.md).

---

## Sequences and Outreach

### How do sequences work?

A sequence is a multi-step outreach campaign that you build visually in the flow editor. You define actions (like a post, follow, send a DM, send a connection request), set delays between steps, and add conditions that branch based on lead behavior. Once started, AutoReach executes the steps automatically for each enrolled lead. See [Building Sequences](outreach/building-sequences.md).

### What happens if I run out of daily send limits?

When a daily limit is reached, remaining actions are automatically rescheduled to the next day at a random time within your activity window. Leads stay in the sequence and no actions are lost. Limits reset at midnight in your timezone. See [Scheduling & Send Limits](outreach/scheduling.md).

### What is the difference between pausing and stopping a sequence?

Pausing temporarily stops all pending actions without losing progress. You can resume a paused sequence and it picks up where it left off. Stopping permanently ends the sequence. A stopped sequence cannot be restarted. To run the same campaign again, duplicate the sequence and start the copy. See [Building Sequences](outreach/building-sequences.md).

### How do I duplicate a sequence?

Open the sequence you want to copy, then use the duplicate option from the sequence menu. This creates a new draft sequence with the same steps, templates, prompts, and settings. You can modify the copy before starting it. Tone examples and enrolled leads are not copied to the duplicate.

### Can I run multiple sequences at the same time?

Yes. You can have multiple active sequences running simultaneously, even on the same platform. Each sequence has its own daily limits, enrolled leads, and settings. Be mindful of total daily activity across all sequences to keep your accounts safe.

---

## AI and Messaging

### How does AI personalize my DMs?

When a DM step executes, AutoReach replaces template variables (like first name, company, role) with real lead data, then passes any remaining placeholders to the AI along with the lead's profile, recent posts, your offer context, and knowledge base content. The AI fills in context-specific details and ensures the message sounds natural. See [Cold DM Generation](outreach/dm-personalization.md).

### How do I customize the tone of AI messages?

Add tone examples to your sequence. These are conversation samples that teach the AI how you sound. The AI retrieves the most relevant examples at response time via semantic search. You can also adjust the AI prompt and DM generation prompt in your sequence settings. AutoReach auto-captures winning conversation patterns from meetings you book. See [Tone Examples](conversations/tone-and-knowledge.md).

### What does "max AI responses = 0" mean?

A value of 0 means unlimited. The AI will continue responding to a conversation for as long as it remains active, with no cap on the number of replies. Set it to a positive number (like 3 or 5) to limit how many times the AI auto-replies in a single conversation before stopping. See [Scheduling & Send Limits](outreach/scheduling.md).

---

## Conversations

### How does the AI know what stage a conversation is in?

AutoReach classifies conversations into 7 stages: Opener Reply, Discovery, Value Prop, Objection Handling, Soft Close, Follow Up, and Exit. Stage detection uses a combination of heuristics (message count, objection count) and AI classification based on conversation history. The AI adapts its tone and goals for each stage. See [Conversation Stages](conversations/ai-response-engine.md).

### Can I take over a conversation from the AI?

Yes. Toggle AI off for any individual conversation using the AI ON/OFF switch in the Inbox. When AI is off, only your manual messages are sent. Sending a manual message also auto-cancels any pending AI response. You can toggle AI back on at any time. See [Manual Controls](conversations/inbox.md).

### How do follow-ups work when a lead goes silent?

Enable conversation follow-ups in your sequence settings. You configure how many days to wait before following up (default 3) and how many follow-ups to send (default 2). AutoReach periodically checks for stale conversations and generates a fresh-angle message to re-engage the lead. See [Manual Controls](conversations/inbox.md).

---

## Engagement Engine

### What does the Engagement Engine do?

The Engagement Engine builds a credible social presence on your accounts by automatically posting content, engaging with relevant posts (likes, replies, comments), and growing your visibility. This makes your accounts look active and authentic before and during outreach. See [Engagement Engine Overview](engagement-engine/overview.md).

### Do I need to approve everything the Engagement Engine posts?

By default, yes. All generated content enters an approval queue where you can approve, reject, or edit it. You can enable auto-approval in your Engagement Engine settings to skip manual review and let content post automatically. Pending approvals expire if not reviewed within a set period. See [Approving Content](engagement-engine/content-generation.md).

---

## Autopilot

### What does Autopilot actually automate?

Autopilot runs five continuous operations: lookalike rotation (finding new seed accounts), auto-enrollment (adding scored leads to sequences), buyer expansion (daily discovery of new prospects), monitor resurfacing (rechecking lower-scored leads for new signals), and signal search (finding prospects posting about your offer topics). See [What Autopilot Does](autopilot/overview.md).

### Is Autopilot safe for my accounts?

Yes. Autopilot respects all the same safety measures as manual operation: daily send limits, activity windows, human behavior simulation, negative content screening, and gradual resumption. It does not bypass any account safety features. See [Account Safety](settings/account-safety.md).

---

## Account Safety

### How does AutoReach avoid getting my account banned?

AutoReach uses multiple layers of protection: consistent browser identity management per account, human behavior simulation (randomized delays, session clustering, typing simulation), time-of-day and day-of-week activity patterns, negative content screening, daily send limits, and automatic emergency pausing when issues are detected. See [Account Safety](settings/account-safety.md).

### What should I do if my account gets paused?

Check the Accounts page to see the error type and reason. Auto-recoverable errors (rate limits, timeouts) resolve after a cooldown period. Non-recoverable errors (bot detection, captcha) require manual intervention. After resolving the issue, manually resume the account. All associated sequences and warmup activities are paused together and need to be resumed. See [Account Safety](settings/account-safety.md).

---

## Billing and Usage

### How much does AutoReach cost to run?

AutoReach itself has a subscription fee. On top of that, you pay for AI API usage directly to OpenAI and Anthropic using your own API keys. Per-lead costs vary based on which AI models you select and which enrichment features you enable. The cost estimation tool in Settings shows real-time estimates based on your configuration. See [Pipeline Cost Estimation](settings/cost-estimation.md).

### How do I reduce my AI costs?

Three strategies: disable web enrichment for leads that don't need it (it's the most expensive per-lead operation), use lower-cost models for high-volume categories like classification and keyword generation in your AI Model settings, and choose efficient fallback models since fallback models also contribute to your overall cost. You can also run smaller, more targeted searches rather than broad ones to reduce the number of leads entering the pipeline. See [Pipeline Cost Estimation](settings/cost-estimation.md) and [AI Model Configuration](settings/ai-models.md).

### How do I set up webhooks for meeting tracking?

Go to Settings and configure your calendar integration. For Calendly, add your booking link and follow the instructions to get the Personal Access Token with all scopes enabled. For Cal.com, copy the webhook URL generated by AutoReach and paste it into Cal.com. The webhook allows AutoReach to automatically detect when meetings are booked and update lead status. See [Meeting Booking](meetings/meetings.md).
