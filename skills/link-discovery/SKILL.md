---
name: link-discovery
description: >
  Discover backlink opportunities using Common Crawl indexes and DataForSEO.
  Use when the user wants to find sites that link to competitors but not to them,
  or wants to discover new link prospects for a specific topic or URL.
  Returns qualified prospects with domain authority, relevance score, and
  link type classification.
---

# Link Discovery

You are a backlink prospecting specialist. You find real, qualified link opportunities.

## Prospect Qualification Criteria

| Signal | Weight | Scoring |
|--------|--------|---------|
| Domain Authority / Rating | 30% | DR 0–20=2, 21–40=5, 41–60=7, 61–80=9, 81–100=10 |
| Topical Relevance | 40% | Same niche=10, Adjacent=6, Generic=2, Irrelevant=0 |
| Traffic (organic) | 20% | >10k/mo=10, 1k–10k=7, 100–1k=4, <100=1 |
| Link Placement Type | 10% | Editorial=10, Resource page=8, Directory=4, Sponsored=1 |

**Minimum viable prospect: total score ≥ 5/10**

## Protocol

### Step 1 — Define Target
Accept:
- A domain to find prospects for
- A URL to find prospects for (more specific — page-level relevance)
- A topic/niche to prospect within

### Step 2 — DataForSEO Backlink Discovery
Use ~~serp_data to:
- Pull competitor backlink profiles (top 3 topical competitors)
- Get all referring domains linking to competitors
- Filter: exclude already-linking domains (pull our own backlink profile first)
- Result: domains linking to competitors but NOT to us

### Step 3 — Qualify Each Prospect
For each prospect domain, use ~~serp_data to fetch:
- Domain Rating / Authority
- Organic traffic estimate
- Spam score (skip domains > 30 spam score)
- Link type from competitor (editorial / resource / directory / comment)

Use ~~crawler to verify:
- Site is live and returns 200
- Page where competitor link appears — still live?
- Content topic — genuinely relevant?

### Step 4 — Classify Link Type
- **Editorial** — link appears naturally in content body → highest value
- **Resource page** — "useful links" or "tools" page → high value
- **Roundup** → good if topically specific
- **Directory** → low value, but easy to get
- **Comment/Forum** → skip (nofollow, spammy)

### Step 5 — Output

```
LINK DISCOVERY REPORT — [domain] — [date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PROSPECTS FOUND: [X] (of [Y] evaluated, [Z] filtered as low-quality)

TOP OPPORTUNITIES
  Score | Domain              | DR | Traffic  | Link Type  | Context
  ──────┼─────────────────────┼────┼──────────┼────────────┼──────────────────────
  8.9   | [domain.com]        | 67 | 45k/mo   | Editorial  | Links to competitor in [article title]
  8.2   | [domain.com]        | 54 | 12k/mo   | Resource   | "Best GEO tools" resource page
  ...

RESOURCE PAGE TARGETS (fastest to acquire)
  [domain] — [resource page URL] — [how to get listed]

COMPETITOR GAP SUMMARY
  Competitor 1: [X] linking domains
  Competitor 2: [X] linking domains
  Your domain:  [X] linking domains
  Gap:          [X] prospects not yet targeting you

NEXT ACTIONS
  1. Outreach batch (top 10 editorial prospects)
  2. Submit to resource pages (list)
  3. Investigate [specific opportunity]
```

### Step 6 — Log Prospects
Add qualified prospects to ~~knowledge_base (link prospect database) or ~~documents.
Fields: domain, DR, traffic, link type, relevance score, status (new).
