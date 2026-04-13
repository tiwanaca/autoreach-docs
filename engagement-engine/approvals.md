# Approving Content

The Engagement Engine generates content automatically, but you control what gets posted through the approval queue.

## Approval Statuses

Content moves through these statuses:

| Status | Description |
|---|---|
| Pending Approval | Awaiting your review |
| Pending | Approved and waiting to post at scheduled time |
| Posting | Currently being posted |
| Posted / Completed | Successfully published |
| Discarded | Permanently removed by you |
| Regenerated | Replaced with a new AI-generated version |
| Skipped | Expired (48 hours without review) or approval queue disabled |
| Failed | Post attempt failed |

## The Approval Queue

All generated content enters the approval queue as "Pending Approval" unless auto-approval is enabled. Each item shows the content text and its scheduled post time.

### Approve

Click **Approve** to post the content as-is at its scheduled time. The status moves to "Pending".

### Regenerate

Click **Regenerate** to replace the content with a new AI-generated version. The new version enters the queue as a new "Pending Approval" item.

### Discard

Click **Discard** to permanently remove the content. The item is deleted and no replacement is generated.

## Auto-Approval

Toggle **auto-approval** in your warmup strategy settings. When enabled:

- Generated content goes directly to "Pending" status (skips the approval queue)
- Content posts automatically at scheduled times without manual review
- You can still view posted content in activity logs

When disabled, all content requires manual review before posting.

## Approval Expiry

Pending approvals expire after **48 hours**. The warmup scheduler checks for stale approvals every cycle (10 minutes) and marks expired items as "Skipped".

This prevents a backlog of outdated content from accumulating if you don't review the queue regularly.

## Queue Disabled Mode

If the approval queue is disabled in your account settings, generated content is skipped rather than entering the approval queue at all.

## Next Steps

- **[Content Generation](content-generation.md)**: How content is created
- **[Engagement Engine Overview](overview.md)**: Return to the overview
