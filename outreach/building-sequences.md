# Building Sequences (Flow Editor)

The flow editor is a visual sequence builder. You design sequences as connected nodes on a canvas, configure each step's action and timing, then save and start the sequence.

## Creating a New Sequence

1. Navigate to **Sequences** in the sidebar
2. Click **Create Sequence**
3. Enter a sequence name
4. Associate an offer (required-  the create button is disabled without one)
5. Select platform accounts-  at least one of Twitter or LinkedIn is required
6. Click **Create**

The sequence is created in Draft status and opens in the flow editor with a default template applied based on the selected platform(s).

Once set, platform accounts **cannot be changed** on a sequence-  this prevents workflow disruption mid-execution.

## Default Templates

When a new sequence is created, a default flow template is applied based on the configured accounts:

**X (Twitter) template:**
```
Like → Follow → DM
```

**LinkedIn template:**
```
Connection Request → Condition: Connection Accepted? (with retries) → DM (if accepted)
```

**Combined X + LinkedIn template:**
```
Like X → Like LinkedIn → Follow
→ Connection Request → Like X → Condition
→ DM LinkedIn (if connected) / DM X (if not)
```

Each template includes pre-configured delays between steps. Templates can be modified after creation - adjust the timing and steps to match your outreach style. Use the "Reset to Default" dialog to restore the original template.

## The Flow Editor Interface

The flow editor displays your sequence as nodes connected by edges on a canvas:

- **Nodes** represent actions (like, DM, follow, etc.) or logic (conditions)
- **Edges** (arrows) show the execution flow between steps
- **Handles** (small circles on nodes) are connection points-  drag from a source handle to a target handle to create edges
- **Drag nodes** to reposition them on the canvas

There is no explicit "Start" node-  the entry point is the topmost node (lowest Y position on the canvas).

### Adding Steps

**Using the "+" button:** Click between nodes or at the end of the flow to open the step popover and select an action type.

**Drag-to-connect:** Drag from a node's source handle and drop on empty canvas to open a creation menu where you select the new step type.

### Deleting Steps

Hover over a node to reveal the delete button. When a step is deleted, the chain is repaired-  any step that pointed to the deleted step is automatically updated to point to the deleted step's next step, preserving flow continuity.

### Saving

Saving is **manual**-  click the "Save Sequence" button. An "Unsaved changes" indicator appears when the flow has been modified. The save operation validates the flow structure before persisting.

**What gets saved:**
- **Visual layout**-  node positions, edges, and viewport state for the flow editor
- **Execution model**-  action configurations, step order, and step connections

## Action Types

| Action | Platforms | Description |
|---|---|---|
| Like | X, LinkedIn | Like a lead's recent post |
| Comment | LinkedIn | Comment on a lead's LinkedIn post (AI-generated from post content) |
| Follow | X | Follow the account |
| DM | X, LinkedIn | Send a direct message |
| Condition |-  | Branch based on lead status |
| Connection Request | LinkedIn | Send a connection request |
| Withdraw Connection | LinkedIn | Withdraw a pending or accepted connection |

## Configuring Steps

Click any node to open its configuration panel on the right side.

### Common Settings (All Action Types)

| Setting | Description |
|---|---|
| Platform | X or LinkedIn (for actions that support both) |
| Delay Days | Days to wait before executing (0 = immediate) |
| Delay Minutes | Additional minutes (0–59) |
| Label | Optional display name for the step |

Total delay = (days x 24 hours) + minutes. Displayed on the node as "Delay: 1d 15m" or "Immediate" for zero delay.

### DM Configuration

| Setting | Description |
|---|---|
| Message template | Required-  message text with `{{variable}}` placeholders |
| AI prompt | Optional-  custom AI instructions for personalization |

Use the variable picker to browse available placeholders. The AI personalizes the template for each lead using their profile data, recent activity, and offer context.

### Comment Configuration

| Setting | Description |
|---|---|
| AI prompt | Optional - custom instructions for comment generation |

Comments are AI-generated from the lead's most recent LinkedIn post content. If no AI prompt is set, the sequence's comment prompt ("How AI comments on posts") is used as default instructions.

### Connection Request Configuration

| Setting | Description |
|---|---|
| Connection note | Optional personalized note (max 300 characters, character count shown) |
| Auto-withdraw days | Auto-withdraw if not accepted within N days (default 14, range 1–30) |

The connection note supports `{{variable}}` placeholders for personalization.

### Condition Configuration

| Setting | Description |
|---|---|
| Condition type | What to evaluate (see table below) |
| Retry interval (days) | Days between rechecks |
| Max retries | Max rechecks before falling to FALSE branch |

**Condition types:**

| Type | Description |
|---|---|
| Replied | Lead replied to a previous message |
| Followed back | Lead followed back (X only) |
| Has profile | Lead has a filled-out profile on the target platform |
| Connection accepted | LinkedIn connection request was accepted |

Condition nodes have two outgoing branches: **TRUE** (left handle, green) and **FALSE** (right handle, red). Each branch can connect to a different next step. The condition is evaluated at the scheduled time-  if false and retries remain, it rechecks after the retry interval. After exhausting retries, the FALSE branch executes.

Example: "Recheck every 3 days, up to 3 times" = 9 days max before falling to the FALSE branch.

## Flow Validation

### Editor Validation (Before Save)

- At least one node must exist
- All action nodes must be reachable from the entry node (topmost)
- No orphaned nodes
- DM nodes must have a non-empty message template
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
| Skip contacted leads | Don't re-reach leads contacted in other sequences |
| Skip negative content | Skip leads with controversial or toxic posts (LinkedIn only) |
| Skip old posts (days) | Only reach leads with activity within N days (LinkedIn only) |
| Prefer original posts | Prefer original posts over reposts for engagement |

### Daily Limits

Each sequence has configurable daily action limits (combined, LinkedIn-specific, and X-specific). See [Scheduling](scheduling.md) for the full limits table and enforcement details.

### AI Temperature

Controls how strictly the AI follows your prompt rules vs. allowing creative variation. Range 0 (strict) to 1 (default). Lower values produce more predictable, rule-following responses. This setting is only available when your content writing model supports temperature control.

### AI & Responses

| Setting | Default | Description |
|---|---|---|
| Max AI responses per conversation | 0 (unlimited) | Max auto-replies per conversation (max 100) |
| AI replies off by default | false | New conversations start with AI off |

### Follow-Up

| Setting | Default | Range |
|---|---|---|
| Conversation follow-up enabled | false |-  |
| Follow-up wait (days) | 3 | 1–30 |
| Max follow-ups | 2 | 1–10 |

### AI Prompts

| Setting | Description |
|---|---|
| AI prompt | General AI instructions for message generation |
| DM generation prompt | Specific prompt for cold DM generation |
| How AI comments on posts | Instructions for AI comment generation on LinkedIn posts (LinkedIn only) |

### Outreach Persona

Configure the sender identity and sales flow used by AI when generating messages:

| Setting | Description |
|---|---|
| Sender name | Name used in messages (defaults to your profile name) |
| Sender role | Your role/title for context |
| Sender is the founder | Toggle if you are both the sender and the company founder |
| Founder name | Company founder's name (hidden when sender is the founder) |

**Sales Flow** defines the steps in your closing flow (e.g., video call, free tool, website). Each step has a type, label, link, and an optional description explaining when to use that step. The AI references these steps when guiding leads toward a booking.

## Starting, Pausing, and Stopping

| Action | Effect |
|---|---|
| **Start** | Sets status to Active, triggers background scheduling of actions for enrolled leads |
| **Pause** | Temporarily stops all pending actions without losing progress. Can be resumed. |
| **Stop** | Permanently ends the sequence. Cannot be restarted-  create a new sequence or duplicate. |

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
Connection Request → Condition: Accepted? (retry 3d × 3)
  → TRUE: DM
  → FALSE: End
```

## Managing Sequences

### Duplicating a Sequence

To reuse an existing sequence design, click **Duplicate** from the sequence menu. You will be asked to provide a new name and select which accounts to use (X, LinkedIn, or both). The duplicate copies all steps, flow layout, AI prompts, and settings - but starts with no enrolled leads, so you can use it for a different audience or offer.

### Viewing the Lead Timeline

Click on any lead within a sequence to see their individual action timeline. The timeline shows every step that has been completed, is currently pending, or has failed - along with scheduled times, execution timestamps, and any error details. This is useful for understanding exactly where a specific lead is in the sequence flow.

### Retrying Failed Actions

When an action fails (due to rate limits, network errors, or platform issues), you can retry it by clicking the retry button on the failed action in the lead timeline. Retried actions are rescheduled and re-enter the execution queue.

### Filtering Sequence Leads

The sequence leads table supports filters to help you focus on specific subsets of the enrolled audience:

| Filter | Description |
|---|---|
| Status | Lead lifecycle status (Pending, Active, Replied, Meeting Booked, etc.) |
| Current step | Which step the lead is currently on |
| Has replied / Has meeting / Contacted | Boolean filters for common outcomes |
| Followers range | Filter by follower count (min / max) |
| Enrolled date | Filter by enrollment timestamp (after / before) |
| Next action type | What action is scheduled next (DM, Like, Connection Request, etc.) |
| Scheduled | When the next action is due (e.g., today, next 7 days) |
| Connection | LinkedIn connection state: Pending (Sent), Pending (Received), Connected, Withdrawn |

Active filters appear as removable chips above the table. Use the sort dropdown alongside to reorder by last action time, score, name, or enrollment date.

## Next Steps

- **[Supported Actions](supported-actions.md)**: Detailed reference for each action type
- **[DM Personalization and Template Variables](dm-personalization.md)**: How AI generates personalized first messages
- **[Scheduling](scheduling.md)**: Activity windows, timing, and send cadence
- **[Simulation and A/B Testing](simulation-and-testing.md)**: Preview messages and compare variants
