# Cross-Platform Profile Matching

Automatically find X/Twitter profiles for LinkedIn leads and LinkedIn profiles for X leads. Enable true multi-platform outreach from single-platform discovery sources.

## How It Works

Cross-Platform Matching uses AI-powered web search to resolve missing platform profiles:

### X Profile Finder (For LinkedIn Leads)

When you discover a prospect on LinkedIn, AutoReach:
1. Extracts their name, company, location, and role
2. Performs an OpenAI-powered web search for their X/Twitter profile
3. Evaluates multiple search strategies to increase success rate
4. Matches the found profile with confidence scoring
5. Automatically links the X profile to the LinkedIn lead

### LinkedIn Profile Finder (For X Leads)

When you discover a prospect on X, AutoReach:
1. Extracts their name, company, location, and profile description
2. Performs web search for their LinkedIn URL
3. Uses multiple matching strategies and signal validation
4. Links the LinkedIn profile to the X lead
5. Updates prospect with full professional profile data

## Confidence Scoring

Each matched profile is assigned a confidence score based on multiple signals:

| Signal | Weight | Validation |
|--------|--------|-----------|
| **Name Match** | 30% | Exact or fuzzy name matching |
| **Source Platform Signal** | 25% | Cross-reference from official sources |
| **Company Match** | 20% | Verify same company/domain |
| **Multiple Signals** | 15% | Additional confirming data points |
| **Location Match** | 10% | Geographic alignment confirmation |

**Confidence Score Examples:**
- 95%+ confidence: Multiple signals align, name match, same company
- 80-95% confidence: Strong signals, minor uncertainty on one dimension
- 60-80% confidence: Name and company match, location uncertain
- Below 60%: Not matched (too much uncertainty)

Only matches above 60% confidence are linked to prospects.

## URL Pattern Support

AutoReach recognizes and validates both standard and shortened URL patterns:

**Standard LinkedIn URLs:**
- `linkedin.com/in/john-smith-12345678/`
- `linkedin.com/in/john-smith/`

**Standard X URLs:**
- `twitter.com/johnsmith`
- `x.com/johnsmith`

**Short/Custom URLs:**
- Custom vanity URLs
- URL shorteners (detected and resolved)

All patterns are properly validated and de-duplicated.

## Automatic Enrichment Pipeline Integration

Cross-Platform Matching runs automatically during the enrichment pipeline:

1. **Lead Discovery:** Prospect found via any search method
2. **Initial Enrichment:** Basic profile data extracted
3. **Cross-Platform Search:** Looks for matching profile on opposite platform
4. **Confidence Validation:** Scores the match quality
5. **Profile Linking:** Updates prospect record with both platform profiles
6. **ICP Scoring:** Evaluates prospect against your ICP

You do not need to do anything. It happens automatically.

## Search Strategies

AutoReach employs multiple search strategies to maximize match accuracy:

### Strategy 1: Direct Name + Company Search
```
"John Smith" linkedin.com site:linkedin.com company:salesforce
```
Targets exact name and company match on LinkedIn.

### Strategy 2: Name + Domain Search
```
"John Smith" salesforce.com site:linkedin.com
```
Matches person at specific company domain.

### Strategy 3: Title + Company Search
```
"Sales Engineer" salesforce.com site:linkedin.com
```
If name is common, uses title and company for precision.

### Strategy 4: Alternative Name Formats
```
"john smith" OR "j smith" OR "john s" linkedin
```
Catches nickname variations and shortened forms.

These strategies run in sequence until a high-confidence match is found.

## Platform-Specific Considerations

### When Finding X Profiles for LinkedIn Leads

**More challenging because:**
- X usernames often differ from real names
- Many professionals don't maintain active X accounts
- Nickname/handle variation is higher

**Success rate:** 40-60% of B2B professionals have X profiles

### When Finding LinkedIn Profiles for X Leads

**Easier to match because:**
- LinkedIn names typically match legal/professional names
- Company information is usually verifiable
- Profile URLs are more stable

**Success rate:** 70-85% of X accounts have LinkedIn profiles

## Best Practices

1. **Use for full coverage:** Link profiles for maximum outreach flexibility across both platforms.

2. **Review confidence scores:** Prospects with 90%+ confidence are safe bets. For 60-80% matches, do manual review if you're uncertain.

3. **Combine discovery methods:** Start with your strongest platform, then use cross-platform matching for additional reach.

4. **Verify manual matches:** When manually reviewing cross-platform matches, check:
   - Same person/name
   - Same company
   - Timeline consistency (role tenure alignment)

5. **Use for platform diversity:** If you want to reach same prospect across multiple platforms, cross-platform matching ensures you have all profiles.

6. **Monitor match quality:** Track email/message deliverability from cross-platform matches. High bounce rates suggest lower match quality.

## Example Workflows

**Scenario 1: LinkedIn-First Outreach with X Follow-up**
1. Run LinkedIn Content Search → find 500 prospects
2. Cross-Platform Matching automatically finds X profiles
3. Send LinkedIn message to all 500
4. Follow up with X mention/DM for those with X profiles (200-400)
5. Higher touch rate from dual-platform contact

**Scenario 2: X-First Discovery with Full Professional Profiles**
1. Run Tweet Search → find 300 prospects
2. Cross-Platform Matching finds LinkedIn profiles
3. Enrich full professional data from LinkedIn (company, role, tenure)
4. Better ICP matching with full profile data
5. More informed outreach messaging

**Scenario 3: Account-Based Outreach**
1. Run LinkedIn People Search for target accounts
2. Cross-Platform Matching finds X profiles
3. Identify executives on both platforms
4. Run coordinated multi-platform ABM campaign
5. LinkedIn message + X social proof (likes, follows, mentions)

## Troubleshooting

**Not finding X profiles for LinkedIn leads?**
- This is normal. Not all professionals are on X
- Some X accounts are private or inactive
- Try with more distinctive names (less competition for matches)
- Company information improves match success

**LinkedIn profile matches seem less accurate?**
- LinkedIn is easier to match, so low confidence scores indicate real mismatches
- Verify matches manually for 60-75% confidence scores
- Check company and role alignment carefully

**Getting false positives?**
- Review confidence scores and only use 80%+ matches for automatic outreach
- Manually verify 60-80% matches before sending messages
- If false positive rate is high, adjust match thresholds

**Some prospects have both profiles but aren't being matched?**
- Confidence scoring may be below threshold (legitimate safety feature)
- Manually verify and update if you're confident it's correct
- Provide feedback if matching is consistently too conservative

**What about privacy?**
- Cross-Platform Matching only uses publicly available profile data
- No scraping of private messages or private profile data
- Matches are only visible to you (not shared publicly)

## Advanced Strategies

**Multi-Channel Messaging Sequence:**

1. **Day 1:** LinkedIn message from primary account
2. **Day 3:** X follow/mention if cross-platform profile found
3. **Day 5:** Second LinkedIn message if no response
4. **Day 7:** Email if available (from enrichment)

This creates impression frequency without spamming via multiple platform touches.

**Platform Prioritization:**

- **Start on strength:** Use your strongest platform first (where you have better account health)
- **Cross-promote:** Once conversation starts on one platform, mention profile on other platform
- **Natural transition:** Move conversation to platform prospect prefers based on response patterns

**Lookalike + Cross-Platform:**

1. Find lookalike audiences on X
2. Cross-Platform Matching finds their LinkedIn profiles
3. Automatically have full professional context for outreach
4. Enrichment data from LinkedIn improves ICP scoring
