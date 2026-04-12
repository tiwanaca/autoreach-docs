# Cross-Platform Profile Matching

AutoReach automatically finds the matching profile on the other platform for every lead you discover. If you find a prospect on LinkedIn, it locates their X profile. If you find them on X, it locates their LinkedIn profile. This gives you full multi-platform outreach capability from a single discovery source.

## How It Works

Cross-platform matching runs automatically as part of the enrichment pipeline. There is nothing you need to configure or trigger manually.

1. **Lead Discovery** - You find a prospect through any search method on either platform.
2. **Profile Data Collection** - AutoReach extracts identifying information from the discovered profile (name, company, role, location).
3. **Cross-Platform Search** - An AI-powered web search looks for the prospect's profile on the other platform.
4. **Match Validation** - The system evaluates multiple signals (name, company, location, and other data points) to confirm the match is accurate. Only high-confidence matches are linked.
5. **Profile Linking** - The matched profile is attached to the lead record, giving you a unified view across both platforms.

### Finding X Profiles for LinkedIn Leads

When you discover a prospect on LinkedIn, AutoReach searches the web for their X profile using their professional details. X handles often differ from real names, so the system uses multiple signals to verify the match before linking it.

### Finding LinkedIn Profiles for X Leads

When you discover a prospect on X, AutoReach searches for their LinkedIn profile. LinkedIn profiles tend to use real names and include verifiable company information, so matches are generally straightforward.

## Enrichment Pipeline Integration

Cross-platform matching is one step in the broader enrichment pipeline. After a lead is discovered:

1. Basic profile data is extracted from the source platform.
2. Cross-platform matching searches for the profile on the other platform.
3. If a match is found, the lead record is updated with both platform profiles.
4. The lead proceeds through ICP scoring with the combined data from both platforms.

Leads with profiles on both platforms benefit from richer data, which improves ICP scoring accuracy and gives you more outreach options.

## Example Workflows

**LinkedIn-First Outreach with X Follow-up**

1. Run a LinkedIn search and discover prospects.
2. Cross-platform matching automatically finds X profiles for those leads.
3. Send LinkedIn messages to all prospects.
4. Follow up on X for leads where a profile was found, increasing your touchpoints without repeating the same channel.

**X-First Discovery with Full Professional Context**

1. Run a tweet search and discover prospects engaging with relevant topics.
2. Cross-platform matching finds their LinkedIn profiles.
3. Full professional data (company, role, tenure) enriches your lead records.
4. Use the richer profile data to write more informed, personalized outreach.

**Account-Based Outreach**

1. Run a LinkedIn people search targeting specific companies.
2. Cross-platform matching finds X profiles for decision-makers.
3. Run coordinated outreach across both platforms for higher visibility.

## Troubleshooting

**Not finding X profiles for some LinkedIn leads?**
This is expected. Not every professional maintains an active X account. Leads with more distinctive names and clear company affiliations tend to match more reliably.

**A match looks incorrect?**
Low-confidence matches are filtered out automatically, but occasional false positives can occur. If a match looks wrong, you can manually update the lead record. Common causes include very common names or professionals who have changed companies recently.

**Both profiles exist but no match was made?**
The system intentionally requires strong confidence before linking profiles. If the available signals were not sufficient to confirm a match, it will skip the link rather than risk a false positive. You can always add the profile manually if you verify it yourself.

## Next Steps

- **[Enrichment Pipeline](../enrichment/pipeline.md)** - See how matched profiles flow through enrichment and scoring.
- **[How Leads Work](../core-concepts/leads.md)** - Understand unified lead profiles across platforms.
