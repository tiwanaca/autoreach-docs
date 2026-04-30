# Enabling, Pausing, and Disabling Autopilot

## Enabling Autopilot

Enabling Autopilot is a one-click process. The setup runs in the background and completes in 1-2 minutes.

> **What Autopilot replaces vs. what's still on you:** Autopilot creates the searches, sequences, tone examples, and enrollment rules so you don't have to. It does **not** replace daily limit configuration, conversation review in your Inbox, Engagement Engine content approval (unless you turn on auto-post), or meeting tracking setup. Think of it as automating the *setup and discovery* loop — the human-judgment parts (tone tuning, replying to hot leads, deciding when to scale up) still belong to you.

### Prerequisites

- At least one **Offer** created with your ICP and value proposition
- At least one **social account** connected (X and/or LinkedIn)
- No existing active Autopilot config for the same Offer

### The Enable Flow

When you click "Enable Autopilot," the following steps execute:

**Step 1: Create Configuration**

Autopilot is activated immediately. Any prior disabled configuration for the same Offer is removed first. The UI returns immediately while setup continues in the background.

**Step 2: Generate AI Content**

Autopilot generates a shared campaign prompt and tone examples for your Offer. This content is reused across all sequences created in the next step.

**Step 3: Create Sequences (Per Platform)**

For each connected platform (X, then LinkedIn), Autopilot:

1. Creates a sequence with AI-generated steps, tone examples, and auto-enrollment enabled
2. Generates keywords from your Offer
3. Creates a recurring search for that platform
4. Finds a lookalike influencer account via AI search
5. Creates a seed extraction source (follower extraction for X, or a people search with buyer expansion for LinkedIn)

**Step 4: Background Loops Begin**

Once setup completes, Autopilot's continuous operations (lookalike rotation, auto-enrollment, signal search) begin running automatically.

### What to Expect After Enabling

- **Searches begin immediately**: Your first recurring searches start running
- **Follower extraction starts**: Seed accounts begin extracting followers
- **First leads appear**: Typically within the first few hours
- **Auto-enrollment activates**: Qualified leads are enrolled into sequences automatically

---

## Pausing Autopilot

Pause when you want to temporarily stop all Autopilot operations and resume later exactly where you left off.

**When to pause:** Vacations, short breaks, account maintenance, or adjusting settings before resuming.

**To pause:** Click the pause icon on the autopilot card.

**To resume:** Click the play icon on the autopilot card. Autopilot restores searches, reactivates sequences, and resumes operations.

When paused:
- Searches are paused (preserved)
- Sequences are paused
- Seed sources and lookalike accounts are preserved
- All leads and conversations are preserved

---

## Disabling Autopilot

Disable when you are stopping outreach for the long term or want a clean slate.

**When to disable:** Fully stopping outreach for an Offer, switching to manual-only mode, or pivoting to a different ICP.

**To disable:** Click the trash icon on the autopilot card, then confirm by clicking **Remove**.

When disabled:
- Recurring searches are stopped
- Sequences are paused
- Lookalike expansion is disabled
- All leads, conversations, and historical data are preserved

### Re-enabling After Disable

When you re-enable Autopilot after disabling:

- New sequences, searches, and lookalike accounts are created fresh
- AI generates a new campaign prompt and tone examples
- New seed accounts are discovered for follower extraction
- Existing leads in your database are preserved and can be re-scored

---

## Pausing Individual Sequences

You can pause a single sequence without affecting the rest of Autopilot:

1. Go to **Sequences**
2. Select the sequence
3. Click **Pause**

This stops outreach for that sequence only. Other sequences and Autopilot operations continue normally.

## Next Steps

- **[Autopilot Overview](overview.md)**: All Autopilot operations at a glance
- **[Continuous Operations](continuous-operations.md)**: Auto-enrollment, buyer expansion, and monitor resurfacing
