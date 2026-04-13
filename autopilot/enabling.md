# Enabling Autopilot

Enabling Autopilot is a one-click process. The setup runs in the background and completes in 1–2 minutes.

## Prerequisites

- At least one **Offer** created with your ICP and value proposition
- At least one **social account** connected (X and/or LinkedIn)
- No existing active Autopilot config for the same Offer

## The Enable Flow

When you click "Enable Autopilot," the following steps execute:

### Step 1: Create Configuration

An `autopilot_config` record is created immediately with `active` status. Any prior disabled config for the same Offer is removed first. The UI returns immediately while setup continues in the background.

### Step 2: Generate AI Content

Autopilot generates a shared campaign prompt and tone examples for your Offer. This content is reused across all sequences created in the next step.

### Step 3: Create Sequences (Per Platform)

For each connected platform (X, then LinkedIn), Autopilot:

1. Creates a sequence with AI-generated steps, tone examples, and `auto_enroll_active_leads` enabled
2. Generates keywords from your Offer
3. Creates a recurring search (`tweet_search` or `linkedin_search`) with `daily_recurring` enabled
4. Finds a lookalike influencer account via AI search
5. Creates a seed extraction source — `target_user` for X (200 followers to extract) or `linkedin_seed_search` with buyer expansion enabled for LinkedIn

Platforms are processed sequentially to avoid AI rate limits.

### Step 4: Track Resources

All created resource IDs (sequences, searches, target users, lookalike accounts, seed searches) are saved to the config's `created_resources` field for lifecycle management.

### Step 5: Background Loops Begin

Once setup completes, the three Autopilot loops (lookalike rotation, auto-enrollment, signal search) begin processing the new config on their regular intervals.

## What to Expect After Enabling

- **Searches begin immediately**: Your first recurring searches start running
- **Follower extraction starts**: Seed accounts begin extracting followers
- **First leads appear**: Typically within the first few hours as searches and extraction run
- **Auto-enrollment activates**: Leads scoring 60+ are enrolled into sequences automatically

## Re-enabling After Disable

If you previously disabled Autopilot and re-enable it:

- New sequences, searches, and lookalike accounts are created fresh
- Existing leads in the database are preserved and can be re-scored
- Previous automation infrastructure is not restored — Autopilot starts fresh

## Next Steps

- **[What Autopilot Does](what-it-does.md)**: See the continuous operations that begin after setup
- **[Pausing and Disabling](pausing-and-disabling.md)**: How to stop and resume Autopilot
