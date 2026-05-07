# Content Generation and Approvals

All Engagement Engine content is AI-generated using your offer context, content pillars, and the current week's theme. You control what gets posted through the approval queue.

## Generation Flow

1. **Input**: Your offer, ICP, pain points, weekly pillar, and current date
2. **AI generation**: Content is generated using your configured AI models
3. **Approval routing**: Content enters the approval queue as **Pending Approval**, or goes directly to the post queue if auto-approval is enabled

## X Tweets

Tweets are short-form content generated daily based on the current week's pillar:

- Concise and engaging, optimized for the X platform
- References current year and recent trends
- Matches your professional voice and tone

## LinkedIn Posts

LinkedIn posts are longer, narrative-driven content:

- Professional tone suited to the LinkedIn platform
- Designed for engagement, comments, and shares

## Engagement Comments (LinkedIn)

When the Engagement Engine comments on LinkedIn posts, it generates contextual responses:

- References the original post specifically
- Adds value to the conversation (not generic "great post" responses)
- Matches your professional voice
- Concise and conversational

## Year Awareness

All content generation prompts include current date and year context. This ensures posts reference recent trends and do not contain outdated year references.

---

## Approval Queue

All generated content enters the approval queue as "Pending Approval" unless auto-approval is enabled. Each item shows the content text and its scheduled post time.

### Approval Statuses

| Status | Description |
|---|---|
| Pending Approval | Awaiting your review |
| Approved | Approved and waiting to post at scheduled time |
| Queued | Picked up for posting |
| Posted | Successfully published (tweets/posts) |
| Completed | Successfully published (engagement comments) |
| Discarded | Permanently removed by you |
| Skipped | Expired without review or auto-approval was disabled |
| Failed | Post attempt failed |

### Actions

**Approve** - Post the content as-is at its scheduled time. The status moves to "Approved" and the item is queued for posting.

**Regenerate** - Replace the content with a new AI-generated version. The new version enters the queue as a new "Pending Approval" item.

**Discard** - Permanently remove the content. No replacement is generated.

**Edit** - Modify the text before approving:

1. Open the approval queue
2. Edit the text as needed
3. Approve the edited version

### Auto-Approval

Two separate toggles in your Engagement Engine settings control auto-approval:

- **Auto-post** - Generated posts (tweets, LinkedIn posts) skip the approval queue and post automatically
- **Auto-comment** - Generated engagement comments (on other posts) skip the approval queue

When enabled, content posts automatically at scheduled times without manual review. You can still view posted content in activity logs.

When disabled, all content requires manual review before posting.

### Approval Expiry

Pending approvals expire after **48 hours**. Stale approvals are automatically marked as "Skipped". This prevents a backlog of outdated content from accumulating if you do not review the queue regularly.

## Next Steps

- **[Content Strategy and Pillars](content-strategy.md)**: How content themes are organized
- **[Engagement Automation](engagement.md)**: How engagement targeting works
- **[Engagement Engine Overview](overview.md)**: Return to the overview
