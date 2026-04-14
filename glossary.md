# Glossary

Key terms used throughout AutoReach, listed alphabetically.

---

**Active** — A buyer state assigned to leads with a Buyer Score of 60 or higher. Active leads are considered ready for outreach and are eligible for automatic enrollment into sequences. See [Buyer States](core-concepts/buyer-states.md).

**Activity Window** — The time range during which AutoReach executes outreach actions (e.g., 9:00 AM to 9:00 PM). Actions scheduled outside this window are deferred until it reopens. Configured in Settings along with your timezone. See [Scheduling & Send Limits](outreach/scheduling.md).

**Auto-Enrollment** — Auto-enrollment periodically adds newly scored Active leads into a running sequence. See [Auto-Enrollment](autopilot/auto-enrollment.md).

**Autopilot** — AutoReach's one-click automation system that configures searches, creates sequences, enrolls leads, and runs five continuous background operations (lookalike rotation, auto-enrollment, buyer expansion, monitor resurfacing, and signal search). See [Autopilot Overview](autopilot/overview.md).

**Blacklist** — A list of accounts that AutoReach will never discover, enrich, or engage with. Adding an account to the blacklist immediately cancels all pending actions and removes the account from all sequences. See [Blacklisting](settings/blacklisting.md).

**Booking Link** — Your calendar scheduling URL (Calendly, Cal.com, or custom) that AutoReach includes in outreach messages via the `{{booking_link}}` template variable. When webhook integration is configured, AutoReach automatically detects when meetings are booked. See [Meeting Booking](meetings/booking-integration.md).

**Buyer Expansion** — An Autopilot operation that runs daily to discover new prospects from your existing pipeline. On X, it re-extracts followers from seed accounts. On LinkedIn, it rotates through role-based people searches. See [Buyer Expansion](autopilot/buyer-expansion.md).

**Buyer Intelligence** — AutoReach's AI-powered scoring system that evaluates each lead across three dimensions (fit, intent, and timing) to predict purchase probability. Also referred to as the scoring engine. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Buyer Score** — A composite score from 0-100 that combines fit, intent, and timing into a single number. The Buyer Score determines a lead's buyer state and pipeline position. The balance between dimensions adapts automatically based on your market. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Buyer State** — One of six statuses assigned to every lead: Active, Monitor, Poor Fit, Disqualified, Manual Outreach, or Not Scored. The state determines where a lead appears in the UI and whether it is eligible for outreach. See [Buyer States](core-concepts/buyer-states.md).

**Call Brief** — An AI-generated preparation document for an upcoming meeting with a lead. It pulls data from the lead's profile, conversation history, and buyer intelligence to give you talking points. See [Call Briefs](meetings/call-briefs.md).

**Chrome Extension** — A browser extension required to connect your X and LinkedIn accounts to AutoReach. It extracts session cookies from your logged-in browser sessions. On LinkedIn, it also provides an "Add to Leads" button on profile pages. See [Installing the Chrome Extension](getting-started/chrome-extension.md).

**Cold DM** — The first direct message sent to a lead who has not previously interacted with you. AutoReach generates personalized cold DMs using AI, your offer context, lead profile data, and knowledge base content. See [Cold DM Generation](outreach/cold-dm-generation.md).

**Condition Step** — A sequence step that branches the flow based on lead behavior (replied, followed back, connection accepted, or has profile). Condition steps have two outgoing branches (true and false) and can retry on a configurable interval before falling to the false branch. See [Building Sequences](outreach/building-sequences.md).

**Connection Request** — A LinkedIn-specific sequence action that sends a connection request to a lead, optionally with a personalized note (up to 300 characters). Includes configurable auto-withdraw if not accepted within a set number of days. See [Building Sequences](outreach/building-sequences.md).

**Conversation Analyzer** — An AI system that reviews your outreach conversations, compares positive outcomes (meetings booked) against negative ones (lost), and suggests improvements to tone examples and prompts. See [Offers & Knowledge Base](core-concepts/offers-and-knowledge-base.md).

**Conversation Stage** — One of seven stages that classify where a conversation currently sits: Opener Reply, Discovery, Value Prop, Objection Handling, Soft Close, Follow Up, or Graceful Exit. The AI adapts its response style based on the detected stage. See [Conversation Stages](conversations/conversation-stages.md).

**Daily Limit** — The maximum number of outreach actions AutoReach will execute per sequence per day. Separate limits exist for combined actions, LinkedIn-specific actions, and X-specific actions. When a limit is reached, remaining actions are rescheduled to the next day. See [Scheduling & Send Limits](outreach/scheduling.md).

**Disqualified** — A buyer state for leads with very low fit and buyer scores (both below 15). Disqualified leads are excluded from automatic rescoring and resurfacing. They can be manually overridden to Manual Outreach if needed. See [Buyer States](core-concepts/buyer-states.md).

**DM Template** — A message template with `{{variable}}` placeholders that AutoReach fills with real lead data at send-time. Templates use a two-pass system: direct substitution for known variables, then AI inference for custom placeholders. See [Template Variables](outreach/template-variables.md).

**Engagement Engine** — A system that builds social credibility on your accounts by automatically posting content, engaging with relevant posts (likes, replies, comments, follows), and maintaining human-like activity patterns. See [Engagement Engine Overview](engagement-engine/overview.md).

**Enrichment** — The automatic process of gathering additional data about a lead after discovery. Includes profile enrichment (bio, experience, skills), activity enrichment (recent posts), cross-platform matching, web enrichment, email finding, and website finding. See [The Enrichment Pipeline](enrichment/pipeline.md).

**Fit Score** — A score from 0-100 measuring how well a lead matches your ideal customer profile. Evaluates industry, company size, role/seniority, geographic match, and skill/background alignment. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Follow-Up** — An automatic message sent when a lead goes silent after a conversation. Configurable per sequence with wait time (1-30 days) and max count (1-10). Follow-ups are generated with a fresh angle to re-engage the lead. See [Manual Controls](conversations/manual-controls.md).

**Graceful Exit** — A conversation stage triggered when a lead declines or the conversation reaches a dead end. The AI exits respectfully and leaves the door open for the future. See [Conversation Stages](conversations/conversation-stages.md).

**Heat Score** — An account-level metric that aggregates signals from the last 7 days across all leads at a company. Companies with multiple recent signals have a higher heat score, indicating the account is worth prioritizing.

**ICP (Ideal Customer Profile)** — A description of the type of person and company most likely to buy your product. Defined in your Offer's target audience field. Your ICP powers lead discovery, scoring, and personalization throughout AutoReach. See [Offers & Knowledge Base](core-concepts/offers-and-knowledge-base.md).

**Intent Score** — A score from 0-100 measuring whether a lead is actively looking for a solution. Evaluates signals like asking for recommendations, switching tools, complaining about current solutions, engaging with competitors, and mentioning relevant pain points. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Intent Signal** — A data point indicating that a lead is interested in, evaluating, or planning to buy a solution like yours. Examples include asking for recommendations, mentioning competitor tools, complaining about current processes, or posting about relevant challenges. See [Signal Detection](core-concepts/signals.md).

**Knowledge Base** — A collection of documents (PDF, DOCX, TXT) uploaded to an Offer that AutoReach uses for AI responses. Documents are chunked, embedded as vectors, and retrieved via semantic search to provide context during conversations. Limited to 10 documents per offer, 10MB per file. See [Offers & Knowledge Base](core-concepts/offers-and-knowledge-base.md).

**Lead** — A unified profile of a potential buyer that combines data from X and LinkedIn. Leads are automatically discovered, enriched, scored, and tracked throughout the outreach lifecycle. See [How Leads Work](core-concepts/leads.md).

**Lead Pool** — A global database of pre-enriched lead profiles stored as vector embeddings. When you create an offer, AutoReach uses semantic similarity search to instantly match existing profiles against your ICP, delivering scored leads in seconds. See [Lead Pool](finding-leads/lead-pool.md).

**Lookalike Audience** — A set of leads discovered by finding influencers, thought leaders, or communities whose audiences match your ICP, then extracting their followers. AutoReach uses AI to find the right seed accounts automatically. See [Lookalike Audiences](finding-leads/lookalike-audiences.md).

**Manual Outreach** — A buyer state you set manually on any lead, regardless of their score. Treated as Active for enrollment eligibility. Use this for VIP accounts, strategic partnerships, or leads you want to reach despite low scores. See [Buyer States](core-concepts/buyer-states.md).

**Monitor** — A buyer state for leads with a Buyer Score between 30 and 59. Monitor leads have potential but are not yet ready for outreach. They are automatically rechecked on a tiered schedule (every 5 to 21 days depending on buyer state) and promoted to Active if their score improves. See [Buyer States](core-concepts/buyer-states.md).

**Offer** — The foundation of AutoReach. An Offer describes what you sell, who you are targeting, and your outreach goals. It powers lead discovery, scoring, DM personalization, and AI responses. You can create multiple Offers, each with its own pipeline and settings. See [Offers & Knowledge Base](core-concepts/offers-and-knowledge-base.md).

**Pipeline** — The end-to-end flow a lead moves through: discovery, enrichment, scoring, engagement, response, and resurfacing. Also refers to the enrichment pipeline that processes leads through profile data collection, activity fetching, and scoring.

**Poor Fit** — A buyer state for leads with a Buyer Score below 30 who still have some baseline fit or score above 15. Poor Fit leads are monitored on a 21-day cycle and can be promoted if new signals appear. See [Buyer States](core-concepts/buyer-states.md).

**RAG (Retrieval-Augmented Generation)** — A technique where AI responses are enhanced with relevant context retrieved from your knowledge base and tone examples via semantic search. AutoReach retrieves relevant context from your knowledge base and tone examples for each AI response.

**Resurfacing** — The process of automatically rechecking lower-scored leads for new signals on a tiered schedule. When new signals boost a lead's score above the Active threshold (60+), they are promoted and become eligible for auto-enrollment. See [Monitor Resurfacing](autopilot/monitor-resurfacing.md).

**Scoring** — The process of evaluating a lead across fit, intent, and timing dimensions to produce a Buyer Score. AutoReach uses AI-powered Deep Analysis to score leads. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Sequence** — A multi-step outreach campaign built visually in the flow editor. Sequences define the actions (like, follow, DM, connection request), timing between steps, and branching logic for each enrolled lead. See [Building Sequences](outreach/building-sequences.md).

**Sequence Lead** — A lead that has been enrolled in a specific sequence. Each sequence lead tracks its own progress through the sequence steps, current status (pending, active, replied, meeting booked, completed, etc.), and action history.

**Signal** — Any data point that contributes to a lead's buyer score. Signals include intent signals (asking for recommendations, switching tools), company signals (funding, hiring, expansion), engagement signals (competitor engagement, own-post engagement), and timing signals (job changes, new hires). See [Signal Detection](core-concepts/signals.md).

**Simulation** — A preview environment where you can test DM personalization with real lead data, see variable substitution, and simulate AI responses to different lead replies, all without sending anything live. See [Simulation & A/B Testing](outreach/simulation.md).

**Timing Score** — A score from 0-100 measuring how urgent or immediate a lead's needs appear. Evaluates signals like recent job changes, company funding, hiring activity, product launches, and recency of relevant social engagement. See [Buyer Intelligence & Scoring](core-concepts/buyer-scoring.md).

**Tone Example** — A conversation sample stored per-sequence that teaches the AI how you want to sound. Tone examples are classified by conversation stage and retrieved via semantic search at response time. AutoReach auto-captures winning examples from booked meetings. See [Tone Examples](conversations/tone-examples.md).

**Tone Summary** — A 150-250 word AI-generated style guide extracted from your tone examples. It analyzes vocabulary, brevity, value-led approach, and anti-patterns. Auto-regenerated after every 3 new captured wins. See [Tone Examples](conversations/tone-examples.md).

**Warmup** — The process of building a credible social presence on your accounts before launching outreach. The Engagement Engine handles warmup by posting content, engaging with relevant posts, and growing visibility with human-like patterns. See [Engagement Engine Overview](engagement-engine/overview.md).

**Webhook** — An integration that allows external services (Calendly, Cal.com) to notify AutoReach when events occur, such as meeting bookings. Webhooks enable automatic lead status updates when meetings are booked. See [Meeting Booking](meetings/booking-integration.md).
