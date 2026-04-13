# Cold DM Generation

AutoReach has two DM generation systems: a **standalone cold DM generator** for creating one-off personalized messages, and a **template-based personalizer** used by sequences to generate DMs at send-time. Both use AI with lead enrichment data, offer context, and knowledge base content to produce personalized messages.

## Standalone Cold DM Generator

The cold DM generator creates **2 unique DM variants** from a set of inputs. This is used for ad-hoc message generation, not for automated sequences.

### Inputs

| Input | Required | Description |
|---|---|---|
| Offer | Yes | What you're offering (10–300 characters) |
| Target | Yes | Who you're reaching (10–400 characters) |
| Goal | Yes | Conversation objective |
| Keep it short and punchy | No | Checkbox — when enabled, generates shorter, punchier messages |
| Recent tweet/post | No | Paste a recent tweet or post for contextual personalization |
| Name | No | Lead name or username for personalization |

### Goal Options

| Goal | Description |
|---|---|
| Start Conversation | Open dialogue, no hard ask |
| Provide Value First | Share something useful (article, intro, tool) |
| Soft Pitch | Gentle suggestion to explore your offer |
| Book a Call | Direct ask for a meeting |

### How It Works

1. Uses your configured AI model
2. Builds context from goal instruction, tweet context, and name-based greeting rules
3. Calls AI with a strict system prompt enforcing DM rules
4. Parses response into 2 variants (split by blank lines)
5. Cleans em dashes and removes numbering prefixes

## Sequence DM Personalization

When a `dm` step executes in a sequence, it uses the **message personalizer** — a different system from the standalone generator. The personalizer takes a template with `{{variable}}` placeholders and produces a fully personalized message.

### Template Variables

**Direct substitution** (replaced from lead data):

| Variable | Source |
|---|---|
| `{{name}}` | Lead's full name |
| `{{first_name}}` | Parsed first name |
| `{{username}}` | Platform handle |
| `{{bio}}` | Lead bio |
| `{{location}}` | Lead location |
| `{{followers}}` | Follower count |
| `{{following}}` | Following count |
| `{{email}}` | Lead email |
| `{{website}}` | Lead website URL |
| `{{linkedin_url}}` | LinkedIn profile URL |
| `{{x_profile_url}}` | X profile URL |
| `{{company_name}}` | Company name |
| `{{company_size}}` | Employee count |
| `{{company_industry}}` | Company industry |
| `{{funding_stage}}` | Funding stage |
| `{{tech_stack}}` | Technology stack |
| `{{headline}}` | LinkedIn headline |
| `{{summary}}` | LinkedIn summary |
| `{{current_role}}` | Current job title |
| `{{skills}}` | LinkedIn skills |
| `{{achievements}}` | Notable achievements |
| `{{speaking}}` | Speaking engagements |
| `{{podcasts}}` | Podcast appearances |
| `{{enrichment_summary}}` | Web enrichment summary |
| `{{user_name}}` | Your name (sender) |
| `{{booking_link}}` | Calendar booking URL with tracking |

**Special variables** (fetched at send-time):

| Variable | Description |
|---|---|
| `{{post}}` | Lead's recent post (unified: X or LinkedIn) |
| `{{tweet}}` | Backwards-compatible alias for `{{post}}` |
| `{{replied_post}}` | Post text from a prior reply action in the sequence |

**AI-inferred variables** (filled by AI from context):

| Variable | Description |
|---|---|
| `{{role}}` | Inferred from bio and enrichment |
| `{{company}}` | Inferred company name |
| `{{industry}}` | Inferred industry |
| `{{pain_point}}` | Inferred pain point based on offer context |
| `{{question}}` | AI-generated question |
| Any custom `{{placeholder}}` | AI infers from available lead data |

### Post/Tweet Fetching Priority

When `{{post}}` or `{{tweet}}` is used, the system fetches content in this order:

1. Stored X intent stream content (if lead was sourced from X search with original content)
2. Stored LinkedIn intent stream content (if lead was sourced from LinkedIn search with original content)
3. Live fetch of latest tweet from X (if a Twitter account is connected; retries up to 8 times over 30 minutes)
4. Fallback: instructs AI to use bio for personalization instead

For commenter-sourced leads, context includes both the original post and their reply: `"ORIGINAL POST: '...' \nTHEIR REPLY: '...'"`.

### Personalization Flow

1. **First pass** — replaces all known variables with lead data
2. **Post fetch** — fetches `{{post}}`/`{{tweet}}` content if referenced
3. **RAG context** — builds knowledge base + tone context (see below)
4. **AI pass** — sends remaining unknown placeholders to AI for intelligent inference, along with lead bio, enrichment data, offer context, and website content
5. **Returns** personalized message, word count, variables used, and token count

### Knowledge Base Integration (RAG)

When AI personalization runs, the system injects relevant context from your knowledge base and tone examples via semantic search. See [Knowledge Base](../conversations/knowledge-base.md) for how to upload and manage documents, and [Tone Examples](../conversations/tone-examples.md) for conversation samples.

### Tone Control

Tone examples and a tone summary are retrieved via semantic search and injected into the AI prompt to match your voice. See [Tone Examples](../conversations/tone-examples.md) for how to manage and customize them.

**Important rules** -- hard constraints extracted from your AI prompt's "Important Rules" section. If not explicitly defined, the system extracts constraints automatically.

### Custom Prompts

Sequences have two separate prompt fields for DM control:

| Field | Purpose |
|---|---|
| DM Generation Prompt | Overrides the system prompt for message personalization only |
| AI Prompt | Controls AI conversation replies across all stages |

The DM Generation Prompt is optional — if not provided, the default system prompt is used. It allows DM-specific instructions separate from general conversation AI behavior.

## DM Generation Rules

Both systems enforce strict rules on generated messages:

**Structure:**
- Maximum 3 short sentences with periods (not run-ons with commas)
- Must end with exactly one question
- No emojis, no em dashes (use commas or periods)
- Simple, natural language

**Banned openers:** "Saw you...", "Noticed you...", "I noticed...", "Since you...", "Looks like you..."

**Banned phrases:** "I'd love to...", "Would love to...", hype words (leverage, scale, optimize), run-on sentences

**Personalization:** Reference specific data (company, role, recent post) — no generic compliments ("great post!").

## Character Limits

| Platform | DM Limit | Generated Template |
|---|---|---|
| X | 10,000 characters | 50–100 words (validated, retries once if out of range) |
| LinkedIn | 10,000 characters | 50–100 words |

## Template Generation

AutoReach can generate DM templates for you using AI. The generated template follows a specific structure with `{{variable}}` placeholders, enforces 50–100 word count (retries if invalid), and returns the template text, variables used, and token count. You can provide campaign name, tone preference (professional/casual/friendly), and length options.

## Booking URL Injection

The `{{booking_link}}` variable injects the user's calendar URL with lead-specific tracking:

| Provider | Tracking Parameter | Value |
|---|---|---|
| Calendly | `a1` | Lead identifier |
| Cal.com | `x_username` | Lead identifier |
| Other | `a1` (fallback) | Lead identifier |

Tracking value is the lead's LinkedIn identifier (prefixed) for LinkedIn leads or the X username for X leads.

## Negative Content Checking

Before replying to a lead's post, the system checks for sensitive content. This is a **fail-open** design — if the check fails, the message proceeds.

**Skipped topics:** Death, obituaries, serious illness, natural disasters, violence, terrorism, suicide, personal tragedies.

**Allowed topics:** Work complaints, business failures, layoffs, market downturns, sarcasm, controversial opinions, career setbacks.

## Multi-Language Support

DM generation supports 6 languages: English (en), Italian (it), Spanish (es), French (fr), German (de), Portuguese (pt).

Set via the offer's `language` field. For non-English offers, the system prompt includes: `"CRITICAL: Write ALL messages in [language]. You are a native [language] speaker..."`. All generation output (keywords, messages, templates) follows the language instruction.

## Next Steps

- **[Template Variables](template-variables.md)**: Full reference for all personalization variables
- **[Simulation](simulation.md)**: Preview DMs with real leads before sending
- **[Building Sequences](building-sequences.md)**: Integrate DM generation into multi-step campaigns
- **[Supported Actions](supported-actions.md)**: When to use DM vs. other engagement types
