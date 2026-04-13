# Content Generation

All Engagement Engine content is AI-generated using your offer context, content pillars, and the current week's theme.

## Generation Flow

1. **Input**: Offer, ICP, pain points, weekly pillar, current date
2. **AI generation**: Claude (primary) with OpenAI fallback generates content
3. **Post-processing**: Em dashes are replaced with hyphens, formatting is cleaned
4. **Approval routing**: Content enters the approval queue as `pending_approval`, or goes directly to `pending` (auto-posts) if auto-approval is enabled

## X Tweets

Tweets are short-form content generated daily based on the current week's pillar:

- Concise and engaging, optimized for the X platform
- References current year and recent trends (year-awareness is injected into every prompt)
- Matches your professional voice and tone
- 2–4 tweets generated per day (with 15% chance of 0 tweets)

## LinkedIn Posts

LinkedIn posts are longer, narrative-driven content:

- One post per day (with 20% chance of 0 posts)
- Professional tone suited to the LinkedIn platform
- Designed for engagement, comments, and shares

## Engagement Replies

When the Engagement Engine replies to or comments on other posts, it generates contextual responses:

- References the original post specifically
- Adds value to the conversation (not generic responses like "great post")
- Matches your professional voice
- 1–3 sentences, concise and conversational

## Year Awareness

All content generation prompts include current date and year context. This ensures posts reference recent trends and don't contain outdated year references.

## Editing and Customization

You can edit any piece of generated content before it posts:

1. Open the approval queue
2. Edit the text as needed
3. Approve the edited version

See **[Approvals](approvals.md)** for the full approval workflow.

## Next Steps

- **[Approvals](approvals.md)**: Review and manage content before posting
- **[Content Strategy & Pillars](content-strategy.md)**: How content themes are organized
- **[Daily Action Allocation](daily-actions.md)**: How often content is posted
