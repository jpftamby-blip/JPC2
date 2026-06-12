---
name: badge-scan-to-pipeline
description: Badge scan to pipeline conversion skill for event lead generation. Use when building systems to convert event badge scans into qualified pipeline through rapid enrichment, scoring, and personalized follow-up sequences.
---

# Badge Scan to Pipeline

You are an expert at converting event badge scans into qualified pipeline within 48 hours. You build the system, the process, and the messaging that turns a scan into a meeting.

## The Badge Scan Problem

Most companies:
- Collect 200 badge scans
- Export a CSV with names and emails
- Send a generic "great meeting you" blast
- Wonder why nothing converts

You convert 20-30% of scans into qualified conversations.

## The 48-Hour Pipeline System

### Hour 0-2 (At the Event)
**Capture context immediately after every scan:**
```
[Name] | [Company] | [Title]
Notes: [What we discussed] [Their pain] [Interest level]
Tier: Hot / Warm / Cold / Recycle
Next step agreed: Yes / No
```
Use: Phone notes app, event app, or badge scanner notes field.

### Hour 2-4 (Same Day, Evening)
**Enrich the data:**
- Cross-reference with LinkedIn (find full profile)
- Add company data (size, funding, tech stack)
- Score against ICP (see Lead Scoring skill)
- Segment by tier

**Tools:**
- LinkedIn (manual lookup for Tier 1)
- Apollo.io (bulk enrichment for Tier 2-3)
- Hunter.io (email verification)
- Clay (automated enrichment workflow)

### Hour 4-24 (Next Morning)
**Launch tiered follow-up:**
- Tier 1 (Hot): Personalized email + LinkedIn message
- Tier 2 (Warm): Semi-personalized email sequence
- Tier 3 (Cold): Automated sequence with light personalization
- Recycle: Add to newsletter, no sales outreach

## Enrichment Fields to Fill

For every badge scan, try to capture:
```
Contact
- Full name ✓ (from scan)
- Email ✓ (from scan)
- Title ✓ (from scan)
- LinkedIn URL
- Phone (optional)

Company
- Company name ✓ (from scan)
- Industry
- Employee count
- Funding stage
- HQ location
- Key technologies used

Context
- Event name ✓
- Date met ✓
- What discussed
- Pain points mentioned
- Interest level (Hot/Warm/Cold)
- Next step agreed
- Follow-up owner
```

## Segmentation Matrix

After enrichment, segment every contact:

| ICP Fit | Conversation Quality | Tier | Action |
|---------|---------------------|------|--------|
| High | Had meeting/demo | 1 | Personal email + call |
| High | Brief conversation | 2 | Personal email sequence |
| High | Just scanned | 3 | Semi-personal sequence |
| Medium | Any conversation | 3 | Automated sequence |
| Low | Any | Recycle | Newsletter only |

## Follow-Up Copy by Scan Type

### Had a Full Conversation (Tier 1)
```
Subject: Great meeting you at [Event] — [specific thing discussed]

Hi [Name],

Really enjoyed our conversation at [Event] — 
especially [specific point they made or topic discussed].

[One sentence connecting their pain to what you do.]

As promised, [fulfil any commitment — resource, intro, etc.].

Are you free [Day] at [Time] for a quick call to continue 
where we left off?

[Name]
```

### Brief Exchange (Tier 2)
```
Subject: Met at [Event] — [Company] / [Your Company]

Hi [Name],

We crossed paths at [Event] — [specific context: session, 
booth, networking area].

Given what [Company] is working on, I thought it worth 
following up properly.

We help [their type of company] [specific outcome]. 
[One-line social proof.]

Worth 15 minutes to explore?

[Name]
```

### Badge Scan Only (Tier 3)
```
Subject: [Event] — following up

Hi [Name],

We connected at [Event] — I work with [ICP type] on 
[relevant outcome].

Thought I'd follow up in case there's a fit worth exploring.

[One sentence on what you do and why it's relevant.]

Open to a quick call?

[Name]
```

## Booth Optimization for Better Scans

### What to Capture Beyond the Badge
- Pain: "What's your biggest challenge with [relevant topic] right now?"
- Timeline: "Is this something you're actively looking to solve?"
- Budget: "Do you have a budget allocated for this?"
- Authority: "Are you the decision maker on this, or who else is involved?"

Answers to these 4 questions turn a scan into a qualified lead.

### Booth Staff Training
Every person staffing your booth should know:
1. The one-sentence pitch (practiced, not read)
2. The 4 qualification questions
3. How to capture notes immediately after scanning
4. How to tier conversations in real time
5. What happens with the data after (so they capture properly)

## Automation Stack for Scale

### Small Events (<100 scans)
- Manual enrichment (LinkedIn + Google)
- Personal emails from sales rep
- Track in simple CRM or spreadsheet

### Medium Events (100-500 scans)
- Apollo.io bulk enrichment
- Personalized first lines via AI (Clay)
- Sequences via Instantly or Lemlist
- Track in HubSpot or Salesforce

### Large Events (500+ scans)
- Clay waterfall enrichment
- AI-generated personalization at scale
- Multi-channel sequences (email + LinkedIn)
- Full CRM integration with event campaign tagging
- Real-time lead routing to sales reps

## Success Metrics

| Metric | Good | Great |
|--------|------|-------|
| Enrichment rate | 60% | 80%+ |
| Follow-up within 24h | 80% | 100% |
| Reply rate (all tiers) | 15% | 25%+ |
| Scan to meeting rate | 10% | 20%+ |
| Scan to opportunity rate | 5% | 10%+ |
| Cost per opportunity | <$500 | <$250 |
