# DM and Email Personalization

When a DM or Email step executes in a sequence, AutoReach generates a personalized message for each lead. It takes your template with `{{variable}}` placeholders, enriches it with lead data, and uses AI to produce a natural, personalized message.

The variable system documented here applies to **both DMs (X / LinkedIn) and Email steps** (subject and body). Email-specific routing details are covered in [Email Channel](email-channel.md).

## When You Need This Page

You don't have to read this whole page to get started. Autopilot generates a working DM template for you, and the defaults are fine for the first run.

Come back here when:

- **Your reply rate is low** and you want to add more relevant references to your messages (a recent post, a specific role, a pain point).
- **You're writing your own template from scratch** and need to know which `{{variables}}` are available.
- **Messages are coming out generic** because you're missing the variables that drive personalization (typically `{{post}}` for X, `{{current_role}}` + `{{company_name}}` for LinkedIn, or a custom `{{pain_point}}` placeholder the AI fills from your offer).
- **A variable isn't substituting** and you need to know whether it's a known variable (direct fill from lead data) or a custom one (AI-inferred from context).

If your first sequence is sending and getting replies, you can skip this page entirely.

## Personalization Flow

Message personalization follows three passes:

1. **Direct substitution** - replaces known variables with data from the lead's profile
2. **Post fetch** - fetches `{{post}}`/`{{tweet}}` content if referenced in the template
3. **AI personalization** - fills remaining placeholders using lead profile, enrichment data, offer context, knowledge base content, and tone examples

Messages with unresolved variables are blocked and never sent.

---

## Known Variables (Direct Substitution)

These variables are replaced directly from lead data in the first pass.

### Identity

| Variable | Source |
|---|---|
| `{{name}}` | Full name, falls back to username |
| `{{first_name}}` | Extracted from full name |
| `{{username}}` | Platform handle |
| `{{bio}}` | Lead bio |
| `{{location}}` | Lead location |
| `{{email}}` | Lead email |

### Network

| Variable | Source |
|---|---|
| `{{followers}}` | Follower count |
| `{{following}}` | Following count |

### Profile Links

| Variable | Source |
|---|---|
| `{{website}}` | Lead website URL |
| `{{linkedin_url}}` | LinkedIn profile URL |
| `{{x_profile_url}}` | X profile URL |

### Professional Profile

| Variable | Source |
|---|---|
| `{{headline}}` | LinkedIn headline, falls back to bio |
| `{{summary}}` | Profile summary |
| `{{current_role}}` | Current job title from LinkedIn experience |
| `{{skills}}` | Top skills, comma-separated |

### Company Data

| Variable | Source |
|---|---|
| `{{company_name}}` | Company name from enrichment or profile |
| `{{company_size}}` | Employee count range (e.g., "51-200") |
| `{{company_industry}}` | Company industry from enrichment or profile |
| `{{funding_stage}}` | Company funding stage |
| `{{tech_stack}}` | Top technologies, comma-separated |

### Web Enrichment Insights

| Variable | Source |
|---|---|
| `{{achievements}}` | Notable achievements (filtered to current company) |
| `{{speaking}}` | Speaking engagements |
| `{{podcasts}}` | Podcast appearances |
| `{{enrichment_summary}}` | Web enrichment summary |

Achievements, speaking engagements, and podcasts are filtered to the lead's current company. Data from previous employers is excluded.

### Sender and Booking

| Variable | Source |
|---|---|
| `{{user_name}}` | Your name (sender) |
| `{{booking_link}}` | Calendar URL with lead-specific tracking |

---

## Special Variables (Fetched at Send-Time)

These variables trigger data fetching when used in a template.

### `{{post}}` / `{{tweet}}`

Both map to the same logic (`{{tweet}}` is a backwards-compatible alias). Fetches the lead's recent post content using this priority:

1. **Stored content** - if the lead was sourced from a search with original post content
2. **Live fetch** - fetches the latest post from the lead's profile
3. **Bio fallback** - AI uses bio for personalization instead

For commenter-sourced leads, the context includes both the original post and the lead's reply.

### `{{replied_post}}`

References a post that was commented on in a **prior sequence step**. If a comment action executed earlier in the sequence, this variable provides the original post text and your comment text so the DM can reference prior engagement.

If no prior comment happened (step was skipped), the AI uses a generic opener instead.

---

## Custom Variables (AI-Inferred)

Any `{{placeholder}}` that is not in the known variables list is treated as a custom variable. The AI fills it using explicit information from the lead's profile, enrichment data, and offer context. If the information is not available, the placeholder and surrounding text are removed. The AI never invents or guesses information.

Common AI-inferred variables:

| Variable | What AI looks for |
|---|---|
| `{{role}}` | Job title from bio, headline, or enrichment |
| `{{company}}` | Company name from bio or enrichment |
| `{{industry}}` | Industry from bio or enrichment |
| `{{pain_point}}` | Relevant challenge based on offer and lead context |
| `{{question}}` | Contextual question based on lead and offer |

You can use any custom placeholder name.

---

## Example Template

```
hey {{first_name}},

saw you're {{current_role}} at {{company_name}} which probably means {{pain_point}}

I help with {{tech_stack}} teams - think {{enrichment_summary}}.

quick 15-min review, no cost.

interested?

{{user_name}}
{{booking_link}}
```

**Pass 1** replaces `{{first_name}}`, `{{current_role}}`, `{{company_name}}`, `{{tech_stack}}`, `{{enrichment_summary}}`, `{{user_name}}`, `{{booking_link}}` with lead data.

**Pass 2** sends `{{pain_point}}` to AI, which infers it from the lead's profile and offer context or removes it with surrounding text.

---

## Booking Link Tracking

The `{{booking_link}}` variable injects your calendar URL with lead-specific tracking parameters:

| Provider | Parameter | Value |
|---|---|---|
| Calendly | `a1` | Lead identifier |
| Cal.com | `x_username` | Lead identifier |
| Other | `a1` (fallback) | Lead identifier |

---

## DM Quality Standards

AutoReach enforces quality standards on generated messages to ensure they read naturally and avoid common spam patterns:

- **Concise and direct** - short messages with simple language
- **Ends with a question** - invites a natural reply
- **No generic openers** - avoids overused phrases
- **Specific personalization** - references actual lead data (company, role, recent post) rather than generic compliments
- **No hype language** - avoids buzzwords and sales jargon

## Custom Prompts

Sequences have two separate prompt fields for DM control:

| Field | Purpose |
|---|---|
| DM Generation Prompt | Overrides the system prompt for message personalization only |
| AI Prompt | Controls AI conversation replies across all stages |

The DM Generation Prompt is optional. If not provided, the default system prompt is used. It allows DM-specific instructions separate from general conversation AI behavior.

## Template Generation

AutoReach can generate DM templates for you using AI. Provide a campaign name, tone preference (professional/casual/friendly), and length, and the AI creates a template with `{{variable}}` placeholders ready for personalization.

## Negative Content Checking

Before replying to a lead's post, the system checks for sensitive content. If the check cannot be completed, the message proceeds rather than blocking.

**Skipped topics:** Death, obituaries, serious illness, natural disasters, violence, terrorism, suicide, personal tragedies.

**Allowed topics:** Work complaints, business failures, layoffs, market downturns, sarcasm, controversial opinions, career setbacks.

## Multi-Language Support

DM generation supports 6 languages: English, Italian, Spanish, French, German, and Portuguese. Set via the language option in your offer settings. For non-English offers, all AI output (keywords, messages, templates) is generated in the selected language.

## Platform Behavior

All known variables work identically on both X and LinkedIn. Platform differences affect the AI's tone and context, not variable availability:

| Aspect | X | LinkedIn |
|---|---|---|
| Username prefix | `@username` | `username` (no prefix) |
| Tone instruction | Casual and direct | Slightly more professional |
| `{{post}}` label | "on X" | "on LinkedIn" |

## Next Steps

- **[Simulation and A/B Testing](simulation-and-testing.md)**: Preview DMs with real leads before sending
- **[Building Sequences](building-sequences.md)**: Integrate DM steps into multi-step campaigns
- **[Supported Actions](supported-actions.md)**: When to use DM vs. other engagement types
