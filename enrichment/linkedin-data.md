# LinkedIn Profile Data

LinkedIn enrichment extracts comprehensive professional profile data from LinkedIn profiles. This data powers buyer scoring, ICP matching, and AI-generated personalized outreach.

## What Gets Extracted

### Basic Profile Information

| Data | Description |
|------|-------------|
| Name | Full name of the profile owner |
| Headline | Professional headline (e.g., "VP Sales @ Acme Corp") |
| Location | Geographic location and/or remote status |
| Industry | Primary industry classification |
| Profile Summary | About/Bio section text |
| Profile Pictures | URLs to profile and banner images |

The headline is especially valuable for outreach. It is often the first signal of seniority, role, and company.

### Work Experience

LinkedIn captures the complete employment history:

- **Company Name** - Every company the profile has worked at
- **Company Details** - Industry, size, headquarters, LinkedIn company page
- **Job Title** - Each role held
- **Employment Type** - Full-time, Part-time, Contract, etc.
- **Start/End Dates** - When employment began and ended
- **Location** - City/remote status for each role
- **Job Description** - Text written in the position description

This work history is crucial for:
- Understanding their expertise and career progression
- Identifying decision-maker levels (director, VP, C-level)
- Finding relevant shared connections or previous colleagues
- Contextualizing their company and industry knowledge

### Education

Complete educational background:

- **School Name** - University, college, bootcamp, or certification provider
- **Degree** - Bachelor's, Master's, PhD, Certificate, etc.
- **Field of Study** - Major, concentration, or specialization
- **Graduation Dates** - When the degree was completed
- **Activities & Societies** - Clubs, organizations, sports, or leadership roles

### Skills

Professional skills with endorsement counts:

- **Skill Name** - Technical skills, tools, methodologies
- **Endorsement Count** - How many connections have endorsed this skill
- **Endorsement % vs Network** - How this compares to others with the same skill

High-endorsement skills indicate deep expertise in that area.

### Languages

Languages listed on the profile:

- **Language Name** - The language they speak
- **Proficiency Level** - Elementary, Limited Working, Professional, Fluent, Native

Useful for multi-regional outreach and localization.

### Certifications & Credentials

Professional certifications that demonstrate expertise:

- **Certification Name** - Official credential name
- **Authority** - Issuing organization (e.g., AWS, Google, Salesforce)
- **License Number** - Official credential ID
- **Issue & Expiration Dates** - When the cert was earned and when it expires
- **Credential URL** - Link to verify the certification

Highly relevant for technical hiring and B2B targeting.

### Network Strength

- **Connection Count** - Total LinkedIn connections (capped at 500+)
- **Follower Count** - LinkedIn followers (different from connections)

Network size can indicate influence and engagement level.

## How LinkedIn Data is Accessed

{% hint style="info" %}
**Authentication:** LinkedIn data is accessed using a cookie-based session + `li_at` token. This token is configured in your AutoReach workspace settings under **Settings > Accounts > LinkedIn**.
{% endhint %}

The `li_at` token is a private authentication token that authorizes AutoReach to make API requests to LinkedIn on your behalf. It is sensitive: treat it like a password and never share it.

## Data Quality & Completeness

LinkedIn profiles vary in completeness:

- **Well-maintained profiles** have work history, skills, endorsements, and recent activity
- **Sparse profiles** might be missing education, skills, or only have a headline
- **Private profiles** restrict what data can be accessed

AutoReach handles incomplete profiles gracefully. Missing fields simply will not be populated, and scoring algorithms account for incomplete data.

{% hint style="warning" %}
**Privacy Consideration:** Be respectful of LinkedIn's Terms of Service. AutoReach extracts profile data for legitimate outreach and lead qualification purposes. Avoid bulk scraping of profiles that weren't added to your workspace through proper channels.
{% endhint %}

## Using LinkedIn Data for Outreach

AI message generation uses LinkedIn data to:

- **Identify expertise** - "I noticed you've been leading Sales teams for 8+ years..."
- **Reference shared interests** - "We both went to Stanford..."
- **Acknowledge achievements** - "Your work scaling GTM at TechCorp is impressive..."
- **Find connection points** - "I see you've worked with AWS and Salesforce..."

The richer the LinkedIn profile, the more personalized your AI-generated outreach can be.
