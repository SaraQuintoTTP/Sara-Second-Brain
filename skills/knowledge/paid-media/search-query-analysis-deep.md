---
framework: Search Query Analysis & Negative Keyword Architecture
author: msitarzewski/agency-agents
type: deepknowledge
category: paid-media
status: active
agents: [Measurer]
---

# Search Query Analysis & Negative Keyword Architecture — Deep Knowledge
## Source: John Williams (@itallstartedwithaidea), msitarzewski/agency-agents

---

## CONTEXT & PRINCIPLES

Search query analysis is the highest-ROI recurring task in Google Ads management. Unlike structural or
tracking changes (which are one-time fixes), search term hygiene compounds over time: every irrelevant
query blocked permanently improves future efficiency without additional spend.

**Core insight:** The Search Query Report (SQR) is not a list of keywords — it is a window into
user intent. The analyst's job is to map every query to a buyer stage, score its relevance, and
decide: add as keyword, add as negative, or ignore.

**Expected outcomes from disciplined monthly analysis:**
- Reduce non-converting spend by 10-20% in the first analysis cycle
- Maintain irrelevant query impressions below 5% of total
- Achieve 80%+ of spend on correctly intent-aligned queries
- Surface 5-10 high-potential new keywords per cycle

**Why Italian SMEs are especially affected:**
- Italian broad match triggers more linguistic variants than English (inflected language)
- Many SME accounts run broad match without robust negatives → systematic waste
- Agency handoffs often leave shared negative lists empty
- Local service businesses (artigiani, professionisti) are particularly vulnerable to
  informational queries (come fare, fai da te, tutorial) that are never going to convert

---

## EXTENDED OPERATIVE RECIPE

### Step 1 — Data Export Setup

**Minimum data required:**
- Search Terms Report: last 30 days (monthly analysis) or last 7-14 days (weekly)
- Columns to include: Search Term, Match Type, Campaign, Ad Group, Clicks, Impressions,
  Cost, Conversions, Conversion Value, CTR, Avg CPC, Quality Score (if visible)
- Export as CSV; minimum 500 rows for meaningful n-gram analysis
- Pull separately for each account if managing multiple

**Tool setup for n-gram analysis:**
Option A (recommended): Python pandas + frequency count (see template below)
Option B: Google Ads Scripts (in-account, automated)
Option C: Manual pivot table in Excel/Google Sheets (for <200 row reports)

**For Italian SME accounts with small spend (<€1k/month):**
- Use 60-90 day window instead of 30 days (insufficient data in 30 days)
- Merge campaigns into single export to achieve statistical significance

---

### Step 2 — N-Gram Frequency Analysis

**What is an n-gram?**
An n-gram is a contiguous sequence of n words from a text. In SQR analysis:
- 1-gram (unigram): single words — "gratis", "corso", "usato"
- 2-gram (bigram): word pairs — "come fare", "fai da te", "prezzi bassi"
- 3-gram (trigram): three-word phrases — "video tutorial gratuito"

**Why n-grams beat keyword-by-keyword review:**
A query "scarpe artigianali fai da te tutorial gratuito" is one irrelevant query.
The 2-gram "fai da te" appears in 47 queries this month → add as negative once, block 47 irrelevant queries.

**N-gram analysis process:**

Step 2a — Tokenize all queries into 1/2/3-grams using Python (pandas + Counter) or pivot table in Excel/Sheets.
Step 2b — Weight by spend (not just frequency): multiply gram frequency by associated cost to find high-spend irrelevant patterns, not just high-frequency ones.
Step 2c — Identify irrelevant modifier patterns:
Focus n-gram review on:
- High-frequency grams with 0 conversions
- High-spend grams with conversion rate far below account average
- Semantic mismatches (DIY terms, job-seeking terms, competitor brand names, geo terms if local business)

---

### Step 3 — Intent Mapping & SQOS Scoring

**Buyer intent taxonomy:**
| Stage | Intent | Query signals | Action |
|-------|--------|--------------|--------|
| Transactional | Ready to buy | "acquista", "preventivo", "prezzo", "ordina", brand name | Keep, bid up |
| Commercial | Comparing options | "migliore", "recensioni", "confronto", vs | Keep, consider |
| Informational | Learning | "come", "tutorial", "guide", "cos'è" | Negative (usually) |
| Navigational | Looking for specific site | Competitor brand, specific URL | Competitor campaign or negative |

**SQOS (Search Query Optimization System) Scoring:**
Score each high-spend query cluster on 3 dimensions (1-5 scale each):

1. **Intent alignment** (1=completely wrong, 5=perfect match)
   Does this query reflect someone who could become a customer?

2. **Message match** (1=no match, 5=exact match)
   Does the ad that triggered reflect what the searcher wants?

3. **Landing page alignment** (1=irrelevant LP, 5=perfect LP match)
   Does the landing page satisfy the query intent?

```
SQOS Total = Intent (1-5) + Message Match (1-5) + Landing Page (1-5)
Score 12-15: Excellent — protect and scale
Score 8-11: Good — optimize message or LP
Score 4-7: Poor — restructure ad group
Score 3: Critical — add as negative or pause
```

---

### Step 4 — Negative Keyword Decision Tree

```
NEW QUERY FROM SEARCH TERM REPORT
           │
           ▼
   Has it converted? ─── YES ──► Add as positive keyword (exact match)
           │                      OR keep as is if already matched
          NO
           │
           ▼
   Spend > threshold?
   (>€5 for <€500/mo accounts; >€15 for >€2k/mo accounts)
           │
    YES    │    NO
    │      │    └──► Low-spend irrelevant? Flag for batch negative next cycle
    ▼      ▼
   SQOS score?
           │
    <4     │   4-7   │   >7
    │      │         │
    ▼      ▼         ▼
  Add as  Review    Keep —
  negative ad copy   possible
  NOW     + LP      new KW
           │
           ▼
   What scope for the negative?
           │
   ┌───────┴────────┬──────────────┐
   ▼                ▼              ▼
Campaign-level   Ad Group-level  Account-level
(irrelevant to   (irrelevant to  (universally
this campaign    this theme      irrelevant:
only)            only)           "gratis", job
                                  terms, DIY)
```

**Negative keyword levels — Italian SME typical setup:**

**Account-level shared list "Esclusioni Globali":**
```
gratis
gratuito
tutorial
come fare
fai da te
corsI
usato
seconda mano
lavoro
offerta lavoro
wikipedia
youtube
[competitor brand names]
```

**Campaign-level negatives (example: lead gen campaign for consulenza fiscale):**
```
[commercialista corso]     → they want to study, not hire
[software commercialista]  → they want software, not a professional
[associazione]             → not a private client
```

**Ad group-level negatives (example: ad group "apertura partita IVA"):**
```
[costi apertura]           → informational, price-shopping not ready
[conviene]                 → deliberation, not transactional
```

---

### Step 5 — Query Sculpting for Match Type Management

**The close variant problem:**
Google now forces broad match and phrase match to trigger on "close variants" including:
- Synonyms
- Paraphrases
- Implied words
- Same meaning reorderings

**Sculpting workflow:** When broad/phrase match steals from exact match: add the query as exact-match negative in the broad/phrase ad group → forces traffic to the correct ad group.

**Cross-campaign overlap:** Group SQR by Search Term, count unique campaigns. Queries appearing in 2+ campaigns create internal auction competition → add as negative in lower-priority campaigns.

---

### Step 6 — Monthly Analysis Workflow (Recurring)

**Recommended cadence for Italian SME accounts:**

| Account spend | Frequency | Time budget |
|---------------|-----------|-------------|
| <€500/month   | Monthly   | 30 min      |
| €500-2k/month | Bi-weekly | 45 min      |
| >€2k/month    | Weekly    | 60 min      |

**Monthly workflow checklist:**
- [ ] Export SQR for the period (last 30/14/7 days)
- [ ] Run n-gram analysis (bigrams priority, then unigrams)
- [ ] Flag: any bigram with >2 occurrences AND 0 conversions AND >avg CPC spend
- [ ] Run SQOS on top 20 queries by spend
- [ ] Apply decision tree to all flagged queries
- [ ] Update shared negative lists in Google Ads
- [ ] Identify top 3-5 converting queries not yet added as explicit keywords → add as exact match
- [ ] Log changes in client account notes
- [ ] Update Measurer KPI baseline for next cycle comparison

---

### Step 7 — New Keyword Discovery

High-converting search terms not yet added as explicit keywords represent growth opportunities:

**Discovery criteria:**
- Conversion rate ≥ account average
- ≥3 conversions in the period
- Not currently an exact match keyword
- Query intent matches campaign goal

**Action:** Add as exact match keyword in appropriate ad group, set initial bid at ad group default.
Monitor for 2 weeks before adjusting.

---

## VARIANTS & ADAPTATIONS

**Per PMI budget <€1k/mese ads:**
- Skip Python n-gram analysis — use pivot table in Google Sheets
- Focus on unigram analysis only (1-word modifiers like "gratis", "usato", "corsI")
- Maintain a single shared negative list "Esclusioni Globali" — no campaign-level complexity
- Monthly cadence sufficient; no need for weekly

**Per PMI con account ads recente (<6 mesi):**
- Less data available → extend window to 60-90 days
- Prioritize broad negative categories (DIY, informational, job-seeking) over specific queries
- New accounts: implement negative foundations BEFORE running broad match
- Do not add negatives aggressively in first 30 days — need data to understand local query patterns

**Per accounts with broad match >60% of spend:**
- This is emergency mode: expect 20-30% irrelevant spend
- Start with account-level negatives list → immediate impact
- Then sculpt at campaign level
- Consider restricting to phrase match until account is clean

**Per local service businesses (plumber, electrician, lawyer in specific city):**
- Add all out-of-geo city names as negatives
- Add all national generic terms if serving only one region
- "Milano" as negative in a Napoli plumber account = critical

---

## COMPLETE APPLIED EXAMPLE (Italian SME)

**Scenario:** Studio Legale Rossi, lawyer in Turin, €800/month Google Ads, 3 campaigns.
Monthly SQR analysis (30 days, 847 search terms, €780 spent).

**N-gram analysis results (top irrelevant bigrams by spend):**
| Bigram | Occurrences | Total spend | Conversions |
|--------|-------------|-------------|-------------|
| corso avvocato | 34 | €47.20 | 0 |
| fai da te | 28 | €31.50 | 0 |
| lavoro avvocato | 22 | €29.80 | 0 |
| modello fac-simile | 19 | €22.40 | 0 |
| gratuito patrocinio | 15 | €18.90 | 1 (low value) |
| Wikipedia | 12 | €14.20 | 0 |

**Total waste identified:** €163.00 / month (20.9% of spend)

**Negatives added to account-level list:**
```
[corso avvocato]
[fai da te]
[lavoro avvocato]
[offerta lavoro]
[modello fac-simile]
[fac simile]
[Wikipedia]
[gratuito patrocinio]
```

**New keywords discovered (converting queries not yet explicit):**
- "avvocato diritto lavoro Torino" → 4 conversions, add as [exact match]
- "consulenza legale separazione Torino" → 3 conversions, add as [exact match]

**Projected improvement:** €163 waste eliminated + 2 high-intent exact match keywords added.

---

## TEMPLATE — Monthly Negative Keyword Report (Client Deliverable)

Sections: **Sintesi** (query analizzate, spesa, spreco €/%, negative aggiunte, nuove KW trovate) →
**Negative Keyword Aggiunte** (table: Keyword | Motivazione | Query bloccate | Risparmio stimato — separate tables per account-level and campaign-level) →
**Nuove Keyword da Aggiungere** (table: Keyword | Match Type | Conversioni | CPA) →
**Azione Richiesta** (approvazione lista, conferma budget, data prossima analisi).

---

## COMMON MISTAKES

1. **Adding negatives as broad match by default.** In Google Ads, negative broad match is NOT the same
   as regular broad match — it blocks any query containing that word in any order.
   Always use exact or phrase for negatives unless intentionally blocking a word in all contexts.

2. **Blocking high-volume terms without checking if they convert.**
   Always filter by conversions before negating. "prezzo avvocato" might be informational for most
   accounts but transactional for a price-transparent studio.

3. **Adding negatives account-level when they should be campaign-level.**
   "corso" might be irrelevant for a lawyer but relevant if the same account runs a "formazione"
   campaign. Scope your negatives correctly.

4. **Ignoring the n-gram approach in favor of query-by-query review.**
   Query-by-query review misses systematic patterns. One negative bigram can block 30+ irrelevant queries.
   N-gram analysis is the methodology; query-by-query is just noise.

5. **Treating SQOS scoring as optional.** The SQOS score prevents hasty negation of queries that
   could convert with better message match or landing page. Score before you negate.

6. **Never checking cross-campaign query overlap.**
   Internal competition inflates CPCs silently. Always run the overlap check monthly on accounts
   with 3+ campaigns targeting similar audiences.

---

## NOTES FOR THE ARTISAN

**Handoff to Measurer agent:**
After implementing negatives, Measurer should track week-over-week:
- Invalid click rate (should decrease)
- Average CPC (should decrease as irrelevant competition drops)
- Conversion rate (should increase as traffic quality improves)
- Cost per conversion (primary KPI: target 10-20% improvement within 60 days)

**Italian language negatives — common universal exclusions:**
```
fai da te, tutorial, corso, corsI, formazione, gratis, gratuito,
usato, seconda mano, lavoro, offerta lavoro, assunzione, Wikipedia,
forum, yahoo, definizione, significato, cos'è, come funziona
```

**When to escalate to Sara:**
- Negative list changes that might block branded terms
- Queries that suggest the campaign is targeting the wrong audience entirely
  (e.g., all queries are B2C but the client is B2B)
- Conversion rate drop >15% week-over-week after implementing negatives
  (possible over-negation of converting terms)

**Integration with paid-media-audit-deep:**
The search query analysis is a sub-task of Domain 4 (Keyword & Targeting) in the full account audit.
For pre-sales, pull the SQR waste analysis as a standalone finding — it is concrete, measurable,
and highly persuasive for Italian SME owners ("stai pagando €X al mese per persone che non
diventeranno mai clienti tuoi").
