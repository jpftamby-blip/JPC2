---
name: lead-scoring
description: Lead scoring skill for B2B SaaS pipeline management. Use when building scoring models, prioritizing outreach lists, qualifying inbound leads, and helping sales teams focus on the highest-value prospects first.
---

# Lead Scoring

You are an expert in B2B lead scoring for SaaS companies. You build models that help sales and recruiting teams focus their time on the prospects most likely to convert.

## Two Types of Lead Scoring

### Fit Score (Who they are)
Does this lead match your ICP? Static attributes.

### Engagement Score (What they do)
How interested are they showing? Behavioral signals.

**Combined score = Fit + Engagement**

## Fit Scoring Model

### Firmographic Fit (max 40 points)

| Attribute | Criteria | Points |
|-----------|----------|--------|
| Industry | Primary vertical | 15 |
| Industry | Secondary vertical | 8 |
| Industry | Not a fit | 0 |
| Company size | Sweet spot | 10 |
| Company size | Edge of range | 5 |
| Company size | Outside range | 0 |
| Funding stage | Exact match | 10 |
| Funding stage | Adjacent stage | 5 |
| Funding stage | Wrong stage | 0 |
| Geography | Primary market | 5 |
| Geography | Secondary market | 2 |
| Geography | Not served | 0 |

### Technographic Fit (max 20 points)

| Attribute | Criteria | Points |
|-----------|----------|--------|
| Tech stack | Full compatibility | 10 |
| Tech stack | Partial compatibility | 5 |
| Tech stack | Incompatible | -10 |
| Integration needs | Matches your integrations | 10 |
| Integration needs | Partial match | 5 |

### Contact Fit (max 20 points)

| Attribute | Criteria | Points |
|-----------|----------|--------|
| Job title | Economic buyer | 15 |
| Job title | Champion/influencer | 10 |
| Job title | End user | 5 |
| Job title | Not relevant | 0 |
| Seniority | C-suite/VP | 10 |
| Seniority | Director | 7 |
| Seniority | Manager | 5 |
| Seniority | IC | 2 |

**Total Fit Score: 0-80 points**

## Engagement Scoring Model

### Digital Engagement (max 60 points)

| Action | Points |
|--------|--------|
| Replied to email | 25 |
| Opened email 3+ times | 15 |
| Opened email 1-2 times | 5 |
| Clicked link in email | 20 |
| Visited pricing page | 25 |
| Visited case study | 15 |
| Visited blog post | 5 |
| Requested demo | 50 |
| Downloaded content | 10 |
| Attended webinar | 20 |
| Watched >50% of video | 15 |
| Connected on LinkedIn | 10 |
| Replied on LinkedIn | 20 |
| Commented on your content | 10 |
| Followed your company | 5 |

### Negative Signals (deduct points)

| Action | Points |
|--------|--------|
| Unsubscribed from email | -30 |
| Marked email as spam | -50 |
| No engagement in 90 days | -20 |
| Removed LinkedIn connection | -20 |
| "Not interested" response | -40 |

## Combined Score Matrix

| | Low Engagement (<20) | Med Engagement (20-50) | High Engagement (50+) |
|--|---------------------|----------------------|----------------------|
| **High Fit (60+)** | 🟡 Nurture actively | 🟠 Sales follow-up | 🔴 Immediate outreach |
| **Med Fit (30-60)** | ⚪ Low priority | 🟡 Nurture | 🟠 Sales follow-up |
| **Low Fit (<30)** | ⚪ Remove/archive | ⚪ Monitor only | 🟡 Qualify before pursuing |

## Lead Scoring for Recruiting

### Candidate Score (max 100)

**Profile Fit (max 50)**
| Signal | Points |
|--------|--------|
| Exact title match | 20 |
| Adjacent title | 10 |
| Required skills present | 15 |
| Preferred skills present | 10 |
| Location match | 5 |
| Years experience in range | 10 |
| Target company background | 10 |

**Movability Score (max 50)**
| Signal | Points |
|--------|--------|
| Tenure 2-4 years | 20 |
| No recent promotion | 15 |
| Company in transition | 20 |
| Active on LinkedIn | 10 |
| Recent activity increase | 10 |
| Mutual connections | 10 |
| Just promoted (<6 months) | -20 |
| Company on major upswing | -10 |

## Scoring Implementation

### Simple (Spreadsheet)
```
Columns: Name | Company | Fit Score | Engagement Score | Total | Priority | Next Action
Update weekly manually
Sort by Total Score descending
```

### Medium (CRM-based)
- HubSpot: Use custom properties + workflows
- Salesforce: Use Lead Scoring fields + Einstein
- Pipedrive: Custom fields + automation

### Advanced (Clay/Apollo)
- Waterfall enrichment for firmographic data
- Auto-score on import
- Dynamic re-scoring on engagement
- Slack alerts when score crosses threshold

## Score Decay

Leads go stale. Apply decay:
- No engagement for 30 days: -10 points
- No engagement for 60 days: -20 points
- No engagement for 90 days: Move to cold list
- Trigger event occurs: Reset engagement score

## Priority Action Thresholds

| Total Score | Action | Timeline |
|-------------|--------|----------|
| 90-100 | Call immediately | Same day |
| 75-89 | Priority email + LinkedIn | Within 24 hours |
| 60-74 | Sequence enrollment | Within 48 hours |
| 40-59 | Nurture sequence | Within 1 week |
| 20-39 | Monitor + content | Monthly |
| Under 20 | Archive or remove | — |
