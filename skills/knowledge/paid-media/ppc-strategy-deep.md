---
framework: PPC Campaign Strategy
author: msitarzewski/agency-agents
type: deepknowledge
category: paid-media
status: active
agents: [Measurer]
---

# PPC Campaign Strategy — Deep Knowledge
## Source: msitarzewski/agency-agents (paid-media-ppc-strategist.md)

---

## CONTEXT & PRINCIPLES

Paid search is a **bidding market**, not a placement market. The advertiser who understands
margin, conversion probability, and audience quality sets the correct bid ceiling. Everyone
else overpays or undersells themselves.

For Italian SMEs (1–20 employees, monthly Google Ads budget €500–5,000), the priority
ordering is:

1. **Measurement first** — no campaign touch until tracking is verified (see tracking-server-side-deep.md).
2. **Conversion volume before efficiency** — a new account needs 30–50 conversions/month
   before Smart Bidding has sufficient signal. Manual or Max Clicks first.
3. **Structure protects budget** — bad campaign taxonomy causes budget cannibalization,
   attribution confusion, and reporting opacity.
4. **Quality Score as a cost lever** — a QS of 7 vs. 3 on the same keyword means paying
   ~40% less per click for equivalent position.

**MCP integration note:** Google Ads API access via `mcp-google-ads v1.6.0` allows
programmatic campaign creation, bid adjustments, label management, and performance pulls
directly from the AI workspace — no manual exports required.

---

## EXTENDED OPERATIVE RECIPE

### Step 1 — Account Audit & Baseline (session 0, ~90 min)

Before touching structure, read the account's history.

**Pull via MCP (mcp-google-ads):**
- Last 90 days: campaign performance by network (Search vs. Display vs. PMax)
- Keyword report: CPC, CTR, Conversion Rate, Cost/Conv, Quality Score
- Search term report: matched query vs. triggering keyword
- Auction Insights: competitor overlap, impression share, position above rate

**Diagnostic flags to raise immediately:**
- Brand keywords mixed with generic in the same campaign → budget bleed risk
- Broad match keywords without audience layers → uncontrolled spend
- Smart Bidding with <30 conv/month → algorithm starved, reverts to guessing
- Missing negative keyword list at account level
- Conversion action counting "All conversions" including micro-conversions → inflated data

**Output:** `audit_[client]_[date].md` with flagged items + severity (P1/P2/P3).

---

### Step 2 — Goal Definition & Budget Allocation Framework

Translate business objective → campaign KPI → bidding strategy.

| Business Goal | Primary KPI | Bidding Strategy | Min Budget Signal |
|---|---|---|---|
| Lead generation | Cost Per Lead | tCPA | €30/day or 30 conv/30d |
| E-commerce revenue | ROAS | tROAS | 50 conv/30d recommended |
| Brand awareness | Impression Share | Target IS / CPM | Any |
| App installs | CPI | Target CPI | 10 conv/day |
| Traffic (new site) | CPC | Max Clicks | Any |

**For PMI with budget <€2k/month ads:**
- Do NOT start with tCPA or tROAS — the algorithm needs data you don't yet have.
- Start with **Max Conversions** (no target) for 4–6 weeks to accumulate signal.
- Transition to tCPA only when: (a) ≥30 conversions in the last 30 days, AND
  (b) cost/conv has stabilized (variance <30% week-over-week).
- Set tCPA target at **120% of current observed CPA** on first activation — don't
  set it at the aspirational target or the algorithm will underspend.

**Budget split heuristic for SME:**
- 60–70% Search (intent-based, bottom-funnel)
- 15–20% PMax (if e-commerce with product feed; skip for pure lead gen)
- 10–15% Retargeting Display (if site traffic >500 sessions/month)
- 0% YouTube/Demand Gen until Search is profitable

---

### Step 3 — Campaign Structure Design

Principle: **separate what behaves differently**.

**Minimum viable structure for lead gen SME:**
```
Account
├── [BRAND] — Branded Search (brand keywords, Max Clicks or Target IS)
├── [GENERIC-HOT] — High-intent generic (exact/phrase, Max Conv or tCPA)
├── [GENERIC-COLD] — Informational generic (phrase/broad, separate budget cap)
└── [RLSA] — Remarketing Lists for Search Ads (if >1000 cookie pool)
```

**Ad Group taxonomy rule:**
Each ad group = one tightly themed keyword cluster (3–10 keywords max).
Name format: `[Campaign Abbr] | [Theme] | [Match Type]`
Example: `GEN-HOT | idraulico-Milano | EXM`

**Naming convention for campaigns:**
`[Network]-[Goal]-[Product/Service]-[Geo]-[Audience modifier]`
Example: `SRC-LG-Impianti-Milano-ALL`

**Labels to apply from day 1 (via MCP batch update):**
- `bidding_strategy:[manual|maxconv|tcpa|troas]`
- `phase:[testing|scaling|mature]`
- `budget_tier:[low|mid|high]`

---

### Step 4 — Keyword Strategy & Negative List

**Match type allocation for SME:**
- Exact Match: high-intent commercial keywords (50–60% of budget)
- Phrase Match: variations around core themes (30–40%)
- Broad Match: ONLY with Smart Bidding + audience layers, max 10–15% budget

**Negative keyword tiers:**
1. Account-level negatives (apply to all campaigns): competitors to exclude, irrelevant
   verticals, geographic exclusions, job-related terms ("lavoro", "offerta lavoro")
2. Campaign-level negatives: cross-campaign isolation (brand negatives on generic camps.)
3. Ad group negatives: theme isolation

**Weekly search term review cadence:**
- Pull search terms report via MCP
- Add irrelevant queries to negatives within 7 days of first impression
- Identify high-performing search terms → consider promoting to exact match keywords

---

### Step 5 — Ad Copy & Quality Score Optimization

**Quality Score components (Google weighting):**
- Expected CTR (~35% weight)
- Ad Relevance (~33%)
- Landing Page Experience (~32%)

**RSA (Responsive Search Ad) best practice:**
- 15 headlines (use all slots), 4 descriptions
- At least 3 headlines contain the primary keyword verbatim
- At least 2 headlines address objections or urgency
- Pin headline 1 = primary keyword / brand claim
- All assets rated "Good" or "Best" before scaling spend

**Italian SME ad copy checklist:**
- [ ] Local qualifier in headline (city/region) where relevant
- [ ] Price anchor or guarantee if competitive ("Preventivo Gratuito", "Garantito")
- [ ] CTA with specificity ("Chiama Ora", "Richiedi Online", not generic "Scopri")
- [ ] At least 1 extension: sitelinks (4 minimum), callout, structured snippet, call

---

### Step 6 — Smart Bidding Transition Protocol

```
Week 1-4:   Manual CPC or Max Clicks
            → establish baseline CPC and conversion data

Week 5-8:   Max Conversions (no target)
            → algorithm learns the account; expect CPA variance ±40%

Week 9-12:  tCPA at 120% of observed CPA
            → watch for underspend (budget not reached = target too tight)
            → adjust target +10% if spend <80% of daily budget

Week 13+:   Optimize target downward -5% every 2 weeks if:
            - Conv volume is stable (±15%)
            - Budget is being fully spent
```

**Do NOT change tCPA target more than once per week.** Each change resets the learning
period (minimum 7 days, up to 2 weeks).

---

### Step 7 — Simplified Forecast Model for SME

Use this when pitching a new campaign or justifying budget increase.

**Inputs needed:**
- Monthly search volume for target keywords (Google Keyword Planner)
- Estimated CTR by position (use 5–8% for top-of-page, 2–3% for position 3–4)
- Historical or industry benchmark CVR (leads: 3–8%; e-commerce: 1–3%)
- Target CPA or acceptable CAC

**Forecast formula:**
```
Monthly Impressions = SV × (budget_days / 30)
Monthly Clicks      = Impressions × CTR_estimate
Monthly Conv        = Clicks × CVR_benchmark
Monthly Spend       = Clicks × avg_CPC_estimate
Expected CPA        = Monthly Spend / Monthly Conv
```

**Conservative / Base / Optimistic scenarios:**
- Conservative: CTR × 0.7, CVR × 0.7
- Base: benchmark values
- Optimistic: CTR × 1.2, CVR × 1.15

Present all three to client. Never present only the optimistic scenario.

---

### Step 8 — Ongoing Optimization Cadence

| Frequency | Task | Tool |
|---|---|---|
| Daily | Budget pacing check, anomaly flag | MCP dashboard pull |
| Weekly | Search term review + negatives, bid adjustment review | MCP + manual |
| Bi-weekly | Ad performance review, pause underperformers | MCP |
| Monthly | Quality Score audit, campaign-level performance vs. KPI, budget realloc. | MCP report |
| Quarterly | Full account audit, bid strategy review, structural changes | Full session |

---

## VARIANTS & ADAPTATIONS

**Per PMI budget <€2k/mese ads:**
- Focus on 1–2 campaigns maximum. Spread budget thin = no campaign gets enough data.
- Skip PMax, Demand Gen, YouTube entirely. Pure Search only.
- Disable Search Partners and Display Network expansion in Search campaigns from day 1.
- Use call extensions aggressively — Italian SME clients often convert on the phone.
- Lead form extensions can replace landing pages if the site is weak.

**Per PMI con team marketing interno:**
- Provide the naming convention doc and label taxonomy as a handoff artifact.
- Set up MCP-based weekly pull report in a shared Google Sheet format.
- Train the internal contact on reading the search term report only — don't delegate
  bid strategy or campaign structure changes without review.
- Create a "no-touch" list: campaigns/keywords they cannot modify without approval.

**Per e-commerce con budget €2k–5k/mese:**
- Product feed hygiene is campaign performance. Audit feed weekly.
- PMax + Search split: 50/50 budget initially, shift toward whichever delivers lower ROAS.
- Segment PMax asset groups by product category (not one blob).
- Brand campaign is mandatory — protect branded terms from PMax cannibalization
  with brand exclusions at the PMax campaign level.

---

## COMPLETE APPLIED EXAMPLE (Italian SME)

**Client:** Idraulico Rossi — Idraulico di emergenza, Milano
**Budget:** €1,200/month Google Ads
**Goal:** Lead generation (phone calls + form fills)
**Current state:** No existing account, starting from zero

**Month 1 — Build & Learn:**
- Campaign 1: `SRC-LG-Emergenza-Milano-ALL` — 5 ad groups, exact+phrase
  Budget: €800/month (€26/day)
  Keywords: "idraulico emergenza Milano", "idraulico notte Milano", etc.
  Bidding: Max Conversions (no target)
  Conversions tracked: Phone call (>60s via GTM), Form fill confirmation page

- Campaign 2: `SRC-LG-Brand-Rossi-ALL` — branded terms
  Budget: €100/month
  Bidding: Target Impression Share 90% top of page

- Remaining €300: reserve for remarketing once pixel pool reaches 1,000 users

**Expected Month 1 outcomes (conservative forecast):**
- Clicks: ~280 (avg CPC €3.5 for local emergency plumber)
- Leads: ~14 (5% CVR on high-intent)
- CPA: ~€57

**Month 3 transition:**
- If ≥30 conversions logged: activate tCPA at €70 (120% of observed €57)
- Review search terms weekly, build negative list (other cities, job terms)
- QS target: 7+ on primary keywords before scaling

**Report template (monthly, for client):**
```
REPORT CAMPAGNE GOOGLE ADS — [Month] [Year]
Client: [Name]

OVERVIEW
- Spesa totale: €___
- Click totali: ___
- Lead totali: ___
- Costo per lead: €___
- vs. obiettivo: ___% (obiettivo €___)

TOP 3 CAMPAGNE (per conversioni)
1. [Name] — [spend] — [conv] — [CPA]
2. ...

AZIONI DEL MESE
- [Action taken and rationale]

PIANO MESE PROSSIMO
- [Next action and expected impact]
```

---

## COMMON MISTAKES

1. **Activating tCPA too early** — before 30 conversions. The algorithm optimizes toward
   noise instead of signal. Result: erratic spend, inflated CPA.

2. **One campaign for everything** — brand + generic + remarketing in one campaign means
   budget goes to the cheapest clicks (not the best), and reporting is unreadable.

3. **Not isolating brand** — competitors bid on your brand name. Without a brand campaign,
   you pay €3–5 to appear for your own name instead of €0.30.

4. **Ignoring Search Partners** — enabled by default, often 2–3× worse CVR than Google
   Search. Disable it and re-enable only if you need volume and accept lower quality.

5. **Broad match without RLSA** — broad match without audience constraint is a budget fire.
   Rule: no broad match keyword unless tCPA + Customer Match or RLSA audience is layered.

6. **Setting tCPA at aspirational target** — setting tCPA at €20 when observed CPA is €60
   causes the algorithm to dramatically underspend. Start at 120% of observed, then
   tighten gradually.

7. **Mixing conversion types in primary conversions** — "add to cart" and "purchase" should
   never both be primary conversions for tROAS. Only the macro-conversion is primary.

---

## NOTES FOR THE ARTISAN

- The MCP Google Ads API integration (`mcp-google-ads v1.6.0`) enables bulk operations:
  use it for label application, negative keyword list updates, and performance pulls.
  Do not use it for bid strategy changes — those require deliberate human confirmation.

- Italian SME decision-makers are skeptical of automated bidding. Frame tCPA not as
  "the AI decides" but as "we set a ceiling on what we pay per lead; Google optimizes
  within it." The control framing reduces resistance.

- Always co-present PPC strategy with tracking verification (tracking-server-side-deep.md).
  A campaign without verified conversion tracking is a liability, not an asset.

- For new accounts: set up conversion-based bidding ONLY AFTER the first 30 conversions
  are verified in Google Ads Conversion Actions — not just in GA4. The two systems must
  be in agreement (see <3% discrepancy target in tracking-server-side-deep.md).

- Quality Score 7+ on 70%+ of spend is not a vanity metric — it directly reduces CPCs.
  A 4-point QS improvement from 3→7 on a €1,000/month account saves approximately
  €250–300/month in wasted spend.
