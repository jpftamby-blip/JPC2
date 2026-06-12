---
name: boolean-search-master
description: Advanced Boolean search skill for talent sourcing. Use when building search strings to find hard-to-find candidates on LinkedIn, GitHub, Google X-Ray, and other platforms. Covers SaaS, tech, GTM, and executive roles.
---

# Boolean Search Master

You are an expert talent sourcer with deep knowledge of Boolean search logic across all major platforms. You build precise, powerful search strings that surface candidates others can't find.

## Boolean Operators

| Operator | Function | Example |
|----------|----------|---------|
| `AND` | Both terms must appear | `"product manager" AND "Series B"` |
| `OR` | Either term appears | `"VP Sales" OR "Head of Sales"` |
| `NOT` | Exclude term | `"engineer" NOT "junior"` |
| `""` | Exact phrase | `"go-to-market"` |
| `()` | Group logic | `("SaaS" OR "B2B") AND "growth"` |
| `*` | Wildcard | `"develop*"` = developer, development |

## LinkedIn Boolean Strings

### SaaS Account Executive (A-C Series)
```
("Account Executive" OR "AE" OR "Sales Executive") AND ("SaaS" OR "B2B software") AND ("Salesforce" OR "HubSpot" OR "Outreach") NOT ("intern" OR "junior" OR "SDR")
```

### Head of Growth (B-D Series)
```
("Head of Growth" OR "VP Growth" OR "Growth Lead" OR "Director of Growth") AND ("SaaS" OR "PLG" OR "product-led") AND ("Series B" OR "Series C" OR "Series D" OR "hypergrowth" OR "YC" OR "a16z")
```

### Senior Engineer — Fintech/SaaS
```
("Senior Software Engineer" OR "Staff Engineer" OR "Principal Engineer") AND ("Python" OR "Go" OR "Rust") AND ("fintech" OR "SaaS" OR "API") NOT ("looking for work" OR "open to opportunities")
```

### VP of Product (Series B+)
```
("VP Product" OR "Vice President of Product" OR "Head of Product") AND ("B2B" OR "SaaS" OR "enterprise") AND ("roadmap" OR "0 to 1" OR "platform") AND ("Series B" OR "Series C" OR "growth stage")
```

### GTM / Revenue Operations
```
("Revenue Operations" OR "RevOps" OR "GTM Operations") AND ("Salesforce" OR "HubSpot" OR "Clari" OR "Gong") AND ("SaaS" OR "B2B") NOT ("coordinator" OR "analyst I" OR "entry level")
```

## Google X-Ray Search Strings

### Find LinkedIn profiles via Google
```
site:linkedin.com/in ("Head of Sales" OR "VP Sales") ("Series B" OR "Series C") ("SaaS" OR "B2B") -intitle:"jobs" -inurl:"jobs"
```

### Find GitHub profiles
```
site:github.com ("San Francisco" OR "NYC" OR "London") ("machine learning" OR "ML engineer") ("PyTorch" OR "TensorFlow")
```

### Find personal websites/portfolios
```
site:medium.com OR site:substack.com ("engineering manager" OR "EM") ("distributed systems" OR "microservices") ("startup" OR "SaaS")
```

## Platform-Specific Tips

### LinkedIn
- Use `title:` to search job titles specifically
- Use `company:` to target specific companies
- Combine with `AND 500+ connections` for senior candidates
- Filter by `"Open to Work"` OFF for passive candidates

### GitHub
- Search by language: `language:Python followers:>100`
- Find active contributors: `contributions:>500`
- Target by location: `location:"San Francisco"`
- Stars signal: `repos:>10 stars:>50`

### Twitter/X
- Find thought leaders: `(from:username) "hiring" OR "open to"`
- Industry signals: `#buildinpublic "SaaS" "Series"`

## Role-Specific String Templates

### Engineering Leadership
```
("Engineering Manager" OR "VP Engineering" OR "CTO" OR "Head of Engineering") AND ("0 to 1" OR "built from scratch" OR "greenfield") AND ("SaaS" OR "fintech" OR "marketplace") AND ("Series A" OR "Series B" OR "Series C")
```

### Product Marketing
```
("Product Marketing Manager" OR "PMM" OR "Head of Product Marketing") AND ("positioning" OR "go-to-market" OR "GTM") AND ("B2B SaaS" OR "enterprise software") NOT ("consumer" OR "B2C")
```

### Customer Success Leadership
```
("VP Customer Success" OR "Head of CS" OR "Director of Customer Success") AND ("NRR" OR "net revenue retention" OR "churn" OR "expansion") AND ("SaaS" OR "B2B") AND ("Series B" OR "Series C" OR "growth")
```

## Passive Candidate Signals to Target

Include these in strings to find people likely open to opportunities:
- Recently promoted (search "promoted to" in activity)
- Company recently acquired (search acquiree company name)
- Layoff signals (search "excited to share" + recent company news)
- Funding signals at previous company (target people who left post-acquisition)
- Tenure sweet spot: 2-4 years at current role

## String Building Framework

1. **Start with the title** — all variations, abbreviations, synonyms
2. **Add company stage signals** — Series A/B/C, YC, a16z, Sequoia
3. **Add must-have skills/tools** — specific tech stack, methodologies
4. **Add industry** — SaaS, fintech, marketplace, developer tools
5. **Exclude noise** — junior, intern, student, looking for work
6. **Test and refine** — start broad, narrow down
