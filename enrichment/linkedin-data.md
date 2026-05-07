# LinkedIn Profile Data

LinkedIn enrichment extracts comprehensive professional profile data from LinkedIn profiles. This data powers buyer scoring, ICP matching, and AI-generated personalized outreach.

## How It Works

LinkedIn profile enrichment fetches comprehensive profile data using your connected LinkedIn account-  including experience, education, skills, languages, certifications, contact information, and company data.

If your LinkedIn account is temporarily unavailable, the job is automatically deferred and retried.

## What Gets Extracted

### Basic Profile Information

| Field | Description |
|---|---|
| Name | Full name |
| Headline | Professional headline (e.g., "VP Sales @ Acme Corp") |
| Summary | About/bio section text |
| Location | Geographic location |
| Industry | Primary industry classification |
| Profile Image | Profile picture URL |
| Background Image | Banner/cover image URL |
| Profile ID | LinkedIn profile identifier |
| Public Identifier | Vanity URL slug |
| Bio | Built from headline + summary |

### Contact Information

Extracted from the lead's LinkedIn contact information:

| Field | Description |
|---|---|
| Email | Primary email address |
| Phone Numbers | Array of phone numbers |
| Websites | Array of website URLs |
| Twitter Handle | Linked Twitter/X handle |

The first website is promoted to the lead's website URL if the lead doesn't already have one. Email is promoted to the lead's primary email if not already set.

### Work Experience

Each position includes:

| Field | Description |
|---|---|
| Title | Job title |
| Company Name | Employer name |
| Company URL | Company LinkedIn page URL |
| Company Logo | Company logo image URL |
| Company Size | Employee count range (e.g., start and end) |
| Company Industries | Industry classifications |
| Location | Position-specific location |
| Start Date | Month and year |
| End Date | Month and year, or null for current position |
| Description | Position description text |
| Employment Type | Full-time, Part-time, Contract, etc. |

Positions are deduplicated by title, company, and year, and sorted newest-first.

### Derived Role Data

From the work history, the enrichment derives current role information:

| Field | Description |
|---|---|
| Title | Current job title |
| Company Name | Current employer |
| Is Current | Whether the position is current |
| Tenure (months) | Months in current role |
| Tenure (days) | Days in current role (precision) |

### Education

Each entry includes:

| Field | Description |
|---|---|
| School Name | University, college, or institution |
| School Logo | School logo URL |
| Degree | Bachelor's, Master's, PhD, etc. |
| Field of Study | Major or specialization |
| Start Date | Month and year |
| End Date | Month and year |
| Description | Additional details |
| Activities | Activities and societies |

### Skills

Sorted by endorsement count (highest first):

| Field | Description |
|---|---|
| Name | Skill name (e.g., "Python", "Machine Learning") |
| Endorsement Count | Number of endorsements from connections |

### Languages

| Field | Description |
|---|---|
| Name | Language name |
| Proficiency | Level (e.g., Native or Bilingual, Professional Working, Limited Working, Elementary) |

### Certifications

| Field | Description |
|---|---|
| Name | Certification name |
| Authority | Issuing organization (e.g., AWS, Google, Salesforce) |
| License Number | Official credential ID |
| Issue Date | Month and year |
| Expiration Date | Month and year |
| URL | Credential verification URL |

### Network Strength

| Field | Description |
|---|---|
| Connection Count | Total LinkedIn connections |
| Follower Count | LinkedIn followers |

### Company Data

The enrichment also fetches the full company profile for the lead's current employer:

| Field | Description |
|---|---|
| Company ID | LinkedIn company ID |
| Name | Company name |
| Description | Company description |
| Tagline | Company tagline |
| Industry | Company industry |
| Company Type | Type of organization |
| Headquarters | HQ location |
| Staff Count | Estimated employee count |
| Staff Count Range | Range string (e.g., "1001-5000") |
| Website | Company website URL |
| Founded Year | Year founded |
| Specialities | Array of specialties |
| Logo URL | Company logo URL |
| Follower Count | Company page followers |

The staff count is promoted to the lead's employee count field for lead filtering.

**Company Jobs**: Open job postings at the company, each with title, location, and posting date. Used as a hiring signal.

**Company Posts**: Recent company page posts with text, date, and URL. Used for signal detection.

### Recent Activity

When running as part of the pipeline, LinkedIn enrichment also fetches the lead's recent posts and engagement (if not already fetched):

| Field | Description |
|---|---|
| Recent Posts | Array of structured post objects |
| Posts Text | Concatenated text with date labels for AI consumption |
| Fetch Timestamp | When posts were fetched |
| Empty Flag | True if no posts found |
| Interaction Orbit | Who the lead interacts with on social media |
| Signal Date | Updated if a newer post is found |

## Error Handling

Transient errors (rate limits, account busy, budget exceeded) are automatically deferred and retried. Permanent errors (no LinkedIn URL, profile doesn't exist) are logged and the pipeline continues-  enrichment failure does not block scoring or other enrichment steps.

If your LinkedIn session expires, you'll need to reconnect your account.

## Data Quality

LinkedIn profiles vary in completeness. Missing fields are simply not populated-  scoring accounts for incomplete data. A lead with only a headline and current company still gets enriched and scored, just with less context for personalization.

Company data and company posts are fetched on a best-effort basis. If either fails, the lead continues through the pipeline with profile-level data only.

## Next Steps

- **[X Profile Data](twitter-data.md)**: See what data is extracted from X profiles
- **[Web Enrichment](web-enrichment.md)**: Discover how company-level data is gathered from the web
- **[Enrichment Pipeline](pipeline.md)**: See how LinkedIn enrichment fits into the full pipeline
