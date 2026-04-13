# Building Sequences (Flow Editor)

The flow editor is a visual sequence builder powered by React Flow (`@xyflow/react`). You design sequences as connected nodes on a canvas, configure each step's action and timing, then save and start the sequence.

## Creating a New Sequence

1. Navigate to **Outreach > Sequences**
2. Click **Create Sequence**
3. Enter a sequence name
4. (Optional) Associate an offer to track performance by target audience
5. Select platform accounts — at least one of Twitter or LinkedIn is required
6. Click **Create**

The sequence is created in `draft` status and opens in the flow editor with a default template applied based on the selected platform(s).

Once set, platform accounts **cannot be changed** on a sequence — this prevents workflow disruption mid-execution.

## Default Templates

When a new sequence is created, a default flow template is applied based on the configured accounts:

**X (Twitter) template:**
```
Like (immediate) → Follow (15min) → DM (1 day)
```

**LinkedIn template:**
```
Connection Request (immediate) → Condition: Connection Accepted? (retry 3d × 3) → DM (if accepted)
```

**Combined X + LinkedIn template:**
```
View LinkedIn Profile → Like X (10min) → Like LinkedIn (10min) → Follow (1 day)
→ Connection Request (10min) → Like X (1 day) → Condition (2 days)
→ DM LinkedIn (if connected) / DM X (if not)
```

Templates can be modified after creation. Use the "Reset to Default" dialog to restore the original template.

## The Flow Editor Interface

The flow editor displays your sequence as nodes connected by edges on a canvas:

- **Nodes** represent actions (like, DM, follow, etc.) or logic (conditions)
- **Edges** (arrows) show the execution flow between steps
- **Handles** (small circles on nodes) are connection points — drag from a source handle to a target handle to create edges
- **Drag nodes** to reposition them on the canvas

There is no explicit "Start" node — the entry point is the topmost node (lowest Y position on the canvas).

### Adding Steps

**Using the "+" button:** Click between nodes or at the end of the flow to open the step popover and select an action type.

**Drag-to-connect:** Drag from a node's source handle and drop on empty canvas to open a creation menu where you select the new step type.

### Deleting Steps

Hover over a node to reveal the delete button. When a step is deleted, the chain is repaired — any step that pointed to the deleted step is automatically updated to point to the deleted step's next step, preserving flow continuity.

### Saving

Saving is **manual** — click the "Save Sequence" button. An "Unsaved changes" indicator appears when the flow has been modified. The save operation validates the flow structure before persisting.

**What gets saved:**
- **Visual layout** — node positions, edges, and viewport state for the flow editor
- **Execution model** — action configurations, step order, and step connections

These are separate storage systems. The visual representation and execution model are persisted independently.

## Action Types

| Action | Platforms | Description |
|---|---|---|
| `like` | X, LinkedIn | Like a lead's recent post |
| `reply` | X, LinkedIn | Reply to a post (AI-generated from post content) |
| `follow` | X | Follow the account |
| `dm` | X, LinkedIn | Send a direct message |
| `condition` | — | Branch based on lead status |
| `connection_request` | LinkedIn | Send a connection request |
| `view_profile` | LinkedIn | View the lead's LinkedIn profile |
| `withdraw_connection` | LinkedIn | Withdraw a pending or accepted connection |

## Configuring Steps

Click any node to open its configuration panel on the right side.

### Common Settings (All Action Types)

| Setting | Description |
|---|---|
| Platform | X or LinkedIn (for actions that support both) |
| Delay Days | Days to wait before executing (0 = immediate) |
| Delay Minutes | Additional minutes (0–59) |
| Label | Optional display name for the step |

Total delay = `(delay_days × 24 hours) + delay_minutes`. Displayed on the node as "Delay: 1d 15m" or "Immediate" for zero delay.

### DM Configuration

| Setting | Description |
|---|---|
| `message_template` | Required — message text with `{{variable}}` placeholders |
| `ai_prompt` | Optional — custom AI instructions for personalization |

Use the variable picker to browse available placeholders. The AI personalizes the template for each lead using their profile data, recent activity, and offer context.

### Reply Configuration

| Setting | Description |
|---|---|
| `ai_prompt` | Optional — custom instructions for reply generation |

Replies are AI-generated from the lead's most recent post content. If no `ai_prompt` is set, the sequence's `warmup_prompt` is used as default instructions.

### Connection Request Configuration

| Setting | Description |
|---|---|
| `connection_note` | Optional personalized note (max 300 characters, character count shown) |
| `auto_withdraw_days` | Auto-withdraw if not accepted within N days (default 14, range 1–30) |

The connection note supports `{{variable}}` placeholders for personalization.

### Condition Configuration

| Setting | Description |
|---|---|
| `condition_type` | What to evaluate (see table below) |
| `retry_interval_days` | Days between rechecks |
| `retry_max_attempts` | Max rechecks before falling to FALSE branch |

**Condition types:**

| Type | Description |
|---|---|
| `replied` | Lead replied to a previous message |
| `followed_back` | Lead followed back (X only) |
| `has_profile` | Lead has a filled-out profile on the target platform |
| `connection_accepted` | LinkedIn connection request was accepted |

Condition nodes have two outgoing branches: **TRUE** (left handle, green) and **FALSE** (right handle, red). Each branch can connect to a different next step. The condition is evaluated at the scheduled time — if false and retries remain, it rechecks after `retry_interval_days`. After exhausting retries, the FALSE branch executes.

Example: "Recheck every 3 days, up to 3 times" = 9 days max before falling to the FALSE branch.

## Flow Validation

### Editor Validation (Before Save)

- At least one node must exist
- All action nodes must be reachable from the entry node (topmost)
- No orphaned nodes
- DM nodes must have a non-empty `message_template`
- Condition nodes must have at least one branch edge (true or false)

### Pre-Start Validation (Before Activation)

- Sequence must not already be active
- At least one configured account must exist and not be paused for health issues
- At least one step must be configured
- At least one pending or active lead must be enrolled

## Sequence Settings

Beyond the flow itself, configure overall sequence behavior:

### Enrollment & Lead Filters

| Setting | Description |
|---|---|
| `skip_contacted_leads` | Don't re-reach leads contacted in other sequences |
| `skip_negative_content` | Skip leads with controversial or toxic posts |
| `skip_old_posts_days` | Only reach leads with activity within N days |
| `prefer_original_posts` | Prefer original posts over reposts for engagement |

### Daily Limits

Each sequence has configurable daily action limits (combined, LinkedIn-specific, and X-specific). See [Scheduling](scheduling.md) for the full limits table and enforcement details.

### AI & Responses

| Setting | Default | Description |
|---|---|---|
| `max_ai_responses_per_conversation` | 0 (unlimited) | Max auto-replies per lead (max 100) |
| `ai_disabled_by_default` | false | New conversations start with AI off |

### Follow-Up

| Setting | Default | Range |
|---|---|---|
| `conversation_followup_enabled` | false | — |
| `conversation_followup_wait_days` | 3 | 1–30 |
| `conversation_followup_max_count` | 2 | 1–10 |

### AI Prompts

| Setting | Description |
|---|---|
| `ai_prompt` | General AI instructions for message generation |
| `dm_generation_prompt` | Specific prompt for cold DM generation |
| `warmup_prompt` | Prompt for warmup engagement (likes, replies) |

## Starting, Pausing, and Stopping

| Action | Effect |
|---|---|
| **Start** | Sets status to `active`, triggers background scheduling of actions for enrolled leads |
| **Pause** | Temporarily stops all pending actions without losing progress. Can be resumed. |
| **Stop** | Permanently ends the sequence. Cannot be restarted — create a new sequence or duplicate. |

## Common Sequence Patterns

### Soft Engagement First

```
Like → Follow (1 day) → DM (2 days)
```

Builds familiarity before direct contact. The lead sees engagement before receiving a message.

### Direct with Conditional Follow-Up

```
DM → Condition: Replied? (2 days)
  → TRUE: Stop
  → FALSE: Follow-Up DM
```

### LinkedIn Connection-First

```
View Profile → Connection Request (1 day) → Condition: Accepted? (retry 3d × 3)
  → TRUE: DM
  → FALSE: End
```

## Managing Sequences

### Duplicating a Sequence

To reuse an existing sequence design, click **Duplicate** from the sequence menu. You will be asked to provide a new name and select which accounts to use (X, LinkedIn, or both). The duplicate copies all steps, flow layout, AI prompts, and settings -- but starts with no enrolled leads, so you can use it for a different audience or offer.

### Rescheduling Pending Actions

If you change step delays or daily limits on an active sequence, you can recalculate the timing of all pending actions by clicking **Reschedule** in the sequence menu. This cancels all currently scheduled actions and recreates them with the updated timing. Only available for active sequences.

### Viewing the Lead Timeline

Click on any lead within a sequence to see their individual action timeline. The timeline shows every step that has been completed, is currently pending, or has failed -- along with scheduled times, execution timestamps, and any error details. This is useful for understanding exactly where a specific lead is in the sequence flow.

### Retrying Failed Actions

When an action fails (due to rate limits, network errors, or platform issues), you can retry it by clicking the retry button on the failed action in the lead timeline. For bulk retries, select multiple leads and use **Bulk Retry** to reset all failed actions for those leads at once. Retried actions are rescheduled and re-enter the execution queue.

## Next Steps

- **[Supported Actions](supported-actions.md)**: Detailed reference for each action type
- **[Cold DM Generation](cold-dm-generation.md)**: How AI generates personalized first messages
- **[Template Variables](template-variables.md)**: All available personalization variables
- **[Scheduling](scheduling.md)**: Activity windows, timing, and send cadence
- **[Simulation](simulation.md)**: Preview messages before sending
- **[A/B Testing](ab-testing.md)**: Compare message variants
