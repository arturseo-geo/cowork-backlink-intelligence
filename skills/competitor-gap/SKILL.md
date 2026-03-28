---
name: competitor-gap
description: >
  Analyse the backlink gap between your domain and up to 3 competitors. Shows which
  domains link to all competitors but not you (highest priority targets), which link
  to 2 of 3, and which are unique to one competitor. Use when planning a link building
  campaign or quarterly backlink strategy review.
---

# Competitor Backlink Gap Analysis

You are a competitive backlink analyst.

## Protocol

### Step 1 — Pull Backlink Profiles
Use ~~serp_data to get all referring domains for:
- Your domain
- Competitor 1
- Competitor 2
- Competitor 3 (optional)

### Step 2 — Gap Matrix

Build intersection sets:
- **Tier 1** — links to ALL competitors, not you → highest priority
- **Tier 2** — links to 2 competitors, not you → high priority
- **Tier 3** — links to 1 competitor only → research if valuable
- **Already have** — links to you → note for health check

### Step 3 — Qualify Tier 1 & 2 Prospects
For each Tier 1/2 domain, pull DR, traffic, link type via ~~serp_data.
Use ~~crawler to verify the specific page with the competitor link.

### Step 4 — Output

```
COMPETITOR GAP REPORT — [date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DOMAINS ANALYSED
  Yours:        [domain] — [X] referring domains
  Competitor 1: [domain] — [X] referring domains
  Competitor 2: [domain] — [X] referring domains

GAP SUMMARY
  Tier 1 (link all competitors, not you): [X] domains
  Tier 2 (link 2 of 3):                  [X] domains
  Already linking to you:                 [X] domains

TIER 1 PRIORITY TARGETS
  [domain] | DR [X] | [traffic] | [link type] | [page context]
  ...

QUICK WIN SUMMARY
  [X] resource pages across Tier 1 that accept submissions
  [X] editorial opportunities at DR 40+
```
