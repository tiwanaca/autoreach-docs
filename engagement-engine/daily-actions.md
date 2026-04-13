# Daily Action Allocation

The Engagement Engine generates a randomized mix of actions each day. Counts vary daily to mimic natural human behavior.

## Daily Action Ranges

There are no ramp-up phases. Activity starts at full range from day 1.

### X (Twitter)

| Action | Base | Variation | Daily Range |
|---|---|---|---|
| Likes | 5 | ±60% | 2–8 |
| Follows | 3 | ±60% | 1–5 |
| Tweets | 3 | ±40% | 2–4 |
| Replies | 5 | ±50% | 2–8 |
| DMs | — | — | Always 0 |

Additional skip chances per action type:
- **Tweets**: 15% chance of 0 tweets for the day
- **Replies**: 20% chance of 0 replies for the day

### LinkedIn

| Action | Base | Variation | Daily Range |
|---|---|---|---|
| Profile views | 2 | ±50% | 1–3 |
| Likes | 3 | ±50% | 1–5 |
| Connection requests | 1 | ±50% | 0–2 |
| Comments | 2 | ±50% | 1–3 |
| Posts | 1 | flat | 0–1 |

LinkedIn posts have a **20% skip chance** (0 posts for the day).

## Skip Days

There is a **15% chance** of a full skip day on any given day. On skip days:

- **X**: Only 0–2 likes, all other actions set to 0
- **LinkedIn**: Only 0–1 profile views, all other actions set to 0

Skip days simulate natural human behavior — everyone takes days off. Outreach sequences are **not affected** by skip days. Only Engagement Engine activity pauses.

## Action Scheduling

Actions are distributed into sessions within your activity window:

- Sessions are placed at random time intervals during active hours
- Actions within each session are spaced with randomized delays (2–5 seconds between actions)
- No sudden bursts of activity

## Per-Action Randomization

During execution, each individual action has additional randomization:

- **3% random skip rate**: any action has a 3% chance of being skipped entirely
- **4% give-up rate**: chance to abandon an action mid-execution (simulates distraction)

## Error-Based Ramp-Down

If account errors occur, daily activity automatically reduces:

| Errors (24h) | Activity Level |
|---|---|
| 1 | 90% |
| 2 | 70% |
| 3 | 50% |
| 4 | 30% |
| 5+ | 10% |

## Configurable Ceilings

Default maximum ceilings per account (configurable):

| Action | Default Max |
|---|---|
| Likes | 25 |
| Follows | 10 |
| Replies | 8 |
| DMs | 8 |

## Next Steps

- **[Content Generation](content-generation.md)**: How tweets and posts are created
- **[Engagement Automation](engagement.md)**: How engagement targeting works
