---
framework: Paid Media Account Audit
author: msitarzewski/agency-agents
type: deepknowledge
category: paid-media
status: active
agents: [Measurer, God Mode]
---

# Paid Media Account Audit — Deep Knowledge
## Source: John Williams (@itallstartedwithaidea), msitarzewski/agency-agents

---

## CONTEXT & PRINCIPLES

The forensic account audit is TTP's primary **pre-sales tool** with new Italian SME prospects. A free audit
surfaces concrete waste (typically 15-30% efficiency recovery) and establishes credibility before any contract.
The framework covers 200+ checkpoints across 8 domains, combining structural, technical, and strategic analysis.

**Strategic rationale for Italian SMEs:**
- Most SME accounts are managed by generalist freelancers or micro-agencies without systematic methodology.
- Structural and tracking gaps are the norm, not the exception.
- A single audit finding (e.g., uncapped CPA, missing CAPI, zero negative keyword list) is often enough to close the deal.
- Severity scoring translates technical findings into business language the owner understands.

**Core principle:** Every finding must include severity level, estimated business impact (€ or % waste), and
a remediation step. No finding without a fix.

---

## EXTENDED OPERATIVE RECIPE

### Step 1 — Pre-Audit Data Collection

**Access required:**
- Google Ads: Read-only Manager access (MCC preferred)
- Meta Ads: Business Manager Ad Account Analyst role
- GA4: Viewer access
- Google Tag Manager: Read access (if used)

**Baseline data pull (export before starting):**
1. Last 90-day campaign performance report (all campaigns)
2. Search term report (last 30 days, Google Ads only)
3. Conversion action list with attribution windows
4. Change history log (last 90 days)
5. Audience list inventory
6. Asset (extension) performance report

---

### Step 2 — Domain 1: Account Structure

**Checkpoints:**
- [ ] Campaign naming convention: consistent taxonomy (platform_objective_targeting_date)?
- [ ] Ad group granularity: max 10-15 keywords per ad group?
- [ ] Single keyword ad groups (SKAGs) vs. theme-based — appropriate for account maturity?
- [ ] Device bid adjustments: are they data-driven or default zero?
- [ ] Geographic targeting: explicit inclusion/exclusion vs. "presence or interest"?
- [ ] Audience layering: observation audiences attached to all campaigns?
- [ ] Budget allocation: is spend concentrated in highest-ROAS campaigns or spread randomly?

**Severity flags:**
- CRITICAL: No naming convention → impossible to scale or hand off
- HIGH: "Presence or interest" geographic targeting on local SME → waste
- MEDIUM: No audience observation → no data for future optimization

---

### Step 3 — Domain 2: Tracking & Measurement

**Checkpoints:**
- [ ] Primary conversion action defined (purchases, leads, calls)?
- [ ] Duplicate conversion actions (e.g., GA4 import + tag-based) inflating conversion count?
- [ ] Attribution model: still on last-click vs. data-driven?
- [ ] GA4 cross-platform verification: do GA4 sessions match Ads clicks (within 10-15%)?
- [ ] **Enhanced Conversions (Google):** configured and verified?
  - Check: Settings > Conversions > Enhanced conversions for web
  - Match rate should be >40%; below 20% is CRITICAL
- [ ] **Conversion API / CAPI (Meta):** server-side events active?
  - Check: Events Manager > Event Match Quality score
  - Score should be ≥6.0; below 5.0 is CRITICAL
  - EMQ below 5.0 = significant audience targeting degradation post-iOS14
- [ ] Call tracking: calls from ads measured separately from organic calls?
- [ ] Micro-conversions tracked (page views, time on site, scroll depth)?

**Severity flags:**
- CRITICAL: No primary conversion action → bidding strategies are blind
- CRITICAL: CAPI EMQ <5.0 → Meta audience signal loss, CPL inflation
- HIGH: Duplicate conversions → inflated ROAS, incorrect bid signals

---

### Step 4 — Domain 3: Bidding & Budget

**Checkpoints:**
- [ ] Bidding strategy appropriate for account maturity (manual CPC for new accounts <30 conversions/month)?
- [ ] Smart bidding targets (tCPA/tROAS): are they set to historical averages or aspirational?
  - tCPA set 10-20% above current CPA = safe; 50%+ below = system instability
- [ ] Portfolio bid strategies: multiple campaigns sharing a strategy correctly?
- [ ] Budget pacing: campaigns hitting 100% budget utilization (capped spend)?
- [ ] Shared budgets: used correctly or masking individual campaign waste?
- [ ] Seasonality adjustments: scheduled for known peaks (e.g., Italian summer slowdown, Christmas)?

**Severity flags:**
- CRITICAL: tCPA target set 40%+ below actual CPA → system cannot deliver
- HIGH: Budget capped on best-performing campaigns → lost impression share
- MEDIUM: Smart bidding on account with <30 conversions/month → insufficient data

---

### Step 5 — Domain 4: Keyword & Targeting

**Checkpoints:**
- [ ] Match type distribution: broad match % and its share of spend?
  - Broad match >60% of spend without robust negatives = HIGH risk
- [ ] Negative keyword lists: shared lists attached to all campaigns?
- [ ] Search term waste ratio: % of spend on irrelevant queries (see search query audit)?
- [ ] Quality Score distribution: avg QS across account?
  - QS <5 on keywords driving >10% of spend = HIGH
- [ ] Keyword duplication across ad groups/campaigns: cannibalizing own auctions?
- [ ] BMM migration complete (BMM deprecated 2021 → should be phrase or broad)?

**Severity flags:**
- CRITICAL: No negative keyword list → systematic waste
- HIGH: Keyword cannibalization → bidding against own account

---

### Step 6 — Domain 5: Creative Audit (RSA Pin Strategy)

**RSA Ad Strength checklist:**
- [ ] All RSAs at "Good" or "Excellent" ad strength?
- [ ] Minimum 3 RSAs per ad group (Google recommendation)?
- [ ] Headlines: 15 unique headlines populated (not duplicated)?
- [ ] Descriptions: 4 unique descriptions populated?
- [ ] **Pin strategy audit:**
  - Pins should be used sparingly (only legally required claims, brand name)
  - Pinning >3 headlines = defeats RSA machine learning
  - Flag: are pins limiting system optimization?
- [ ] Asset performance labels: are "Low" performing assets paused/replaced?
  - Assets labeled "Low" for 30+ days should be replaced
- [ ] Extensions/Assets: sitelinks (min 4), callouts (min 4), structured snippets active?
- [ ] Call extensions with business hours set?

**Severity flags:**
- CRITICAL: <3 RSAs per ad group → limited auction flexibility
- HIGH: >50% of headlines pinned → RSA performance degraded
- MEDIUM: No asset rotation review in 60+ days → stale creatives

**Meta creative audit additions:**
- [ ] Advantage+ catalog campaigns: feed quality checked?
- [ ] Creative fatigue: frequency >3 for prospecting audiences → creative refresh needed
- [ ] Video creative: >50% of spend on static images with no video tested?

---

### Step 7 — Domain 6: Shopping & Feed (if applicable)

**Checkpoints:**
- [ ] Disapproval rate: >5% of products disapproved = HIGH
- [ ] Custom labels: 0-4 used for segmentation (margin, bestseller, seasonality)?
- [ ] Feed freshness: last update timestamp?
- [ ] Title optimization: primary keyword in first 70 characters?
- [ ] GTIN/MPN coverage: missing GTINs on brand products?

---

### Step 8 — Domain 7: Competitive Positioning (Auction Insights)

**Checkpoints:**
- [ ] Impression share (Search): target >70% for branded terms, >40% for non-brand?
- [ ] Lost IS (Budget) vs. Lost IS (Rank): which is limiting growth?
  - Lost IS Budget → increase budget
  - Lost IS Rank → improve QS or increase bids
- [ ] Top-of-page rate: >50% for core campaigns?
- [ ] Auction Insights report: who are the consistent competitors? Any overlap >80%?
- [ ] **IVT (Invalid Traffic) rate:**
  - Check: Campaigns > Columns > Competitive metrics > Invalid clicks
  - IVT >3% of total clicks = flag for IP exclusion or placement exclusion review
  - Display/YouTube accounts more susceptible than Search

**Severity flags:**
- CRITICAL: IVT >5% → significant budget waste to non-human traffic
- HIGH: Lost IS Budget >50% on top campaigns → budget reallocation needed

---

### Step 9 — Domain 8: Landing Page

**Checkpoints:**
- [ ] PageSpeed Insights score: mobile >70?
- [ ] LCP (Largest Contentful Paint): <2.5s?
- [ ] Message match: ad headline keywords reflected on landing page?
- [ ] CTA above the fold on mobile?
- [ ] Form length: >5 fields on lead gen page = friction
- [ ] HTTPS / trust signals visible?
- [ ] Heatmap or session recording active (Hotjar, Microsoft Clarity)?

---

### Step 10 — Severity Scoring & Impact Estimation

**Severity matrix:**
| Severity | Definition | Action |
|----------|------------|--------|
| CRITICAL | Blocking correct measurement or wasting >10% of budget | Fix within 1 week |
| HIGH | Reducing efficiency 5-10% | Fix within 30 days |
| MEDIUM | Optimization opportunity, <5% impact | Fix in next cycle |
| LOW | Best practice gap, minimal current impact | Backlog |

**Impact estimation formula (for SME prospect):**
```
Monthly waste estimate = Monthly spend × waste_percentage
Typical ranges:
- Missing negatives: 8-15% waste
- Duplicate conversions: distorts ROAS by 20-40%
- CAPI EMQ <5: 15-25% CPL increase (Meta)
- Budget capped on top campaigns: 10-20% lost revenue
```

---

### Step 11 — Deliverable Assembly

**Structure the audit report in 3 tiers:**
1. **Executive Summary (1 page):** Total findings by severity, single headline impact number, top 3 priorities
2. **Finding Sheets (1 per CRITICAL/HIGH finding):** Issue, evidence, impact, fix
3. **Full Checklist (appendix):** All 8 domains, all checkpoints, RAG status

---

## VARIANTS & ADAPTATIONS

**Per PMI budget <€1k/mese ads:**
- Skip Shopping/Feed domain unless e-commerce
- Compress audit to domains 1, 2, 3, 5, 8 (5 core domains)
- Focus pre-sales message on: tracking fix + creative refresh = quick wins
- Do not overwhelm prospect with 200 findings — lead with top 5

**Per PMI con account ads recente (<6 mesi):**
- Domain 1 (Structure) and Domain 2 (Tracking) are almost always CRITICAL
- Smart bidding likely not appropriate yet → recommend manual CPC + target impression share
- No historical data for auction insights → skip Domain 7
- RSA audit: likely only 1 RSA per ad group → immediate opportunity
- Focus on foundation building, not optimization

**Per account Meta-only (no Google):**
- Remove domains 4 (Keywords), 6 (Shopping/Feed partial)
- Add: Pixel health check, Event deduplication audit, Catalog feed audit
- CAPI verification becomes the single most important technical check

**Per account Google-only (no Meta):**
- Full 8-domain coverage applies
- Add Microsoft Ads parity check if running both

---

## COMPLETE APPLIED EXAMPLE (Italian SME)

**Scenario:** Artigiano del Legno Srl, furniture manufacturer, €2.5k/month Google Ads spend, B2C e-commerce.
Account age: 18 months. Managed by web agency. Sara doing a pre-sales audit.

**Key findings discovered:**

CRITICAL — Duplicate conversions:
- "Purchase" tracked via GA4 import AND Google tag simultaneously
- Reported ROAS: 8.2x | Actual ROAS (corrected): ~4.1x
- Agency has been optimizing toward false signal for 12 months
- Impact: tROAS target of 700% is unreachable → system constantly underdelivers

CRITICAL — Missing Enhanced Conversions:
- No email hashing configured
- Match rate: 12% (benchmark: >40%)
- Impact: smart bidding lacks 88% of customer signal

HIGH — RSA pin abuse:
- 6/8 ad groups have all 15 headlines pinned to position 1
- Ad strength: "Poor" on 5 ad groups
- Impact: RSA machine learning completely neutralized

HIGH — No negative keyword lists:
- 0 shared negative lists attached
- Search term report shows 23% of spend on irrelevant queries (DIY terms, competitor brand names)
- Monthly waste: €575/month

MEDIUM — Budget capped on top campaign:
- "Cucine su misura" campaign (highest ROAS) hitting budget cap daily at 14:00
- Lost IS (Budget): 38%
- Opportunity: reallocate €300/month from lowest-ROAS campaign

**Executive summary headline:**
"Abbiamo identificato €575/mese di spreco immediato e una distorsione del ROAS del 50% che impedisce all'algoritmo di ottimizzare correttamente. Con 3 interventi tecnici nelle prime 2 settimane, stima recupero efficienza: 25-35%."

---

## COMMON MISTAKES

1. **Leading with LOW findings in the pre-sales report.** Only show CRITICAL and HIGH to the prospect.
   Full checklist goes in appendix for after the contract is signed.

2. **Estimating impact without showing the math.** Always show: spend × waste% = monthly waste.
   Concrete numbers close deals; percentages do not.

3. **Auditing without access.** Never audit from screenshots or client-provided exports only.
   Request direct read-only access. Insist on it — it is non-negotiable for a credible audit.

4. **Conflating CAPI with Pixel.** CAPI is server-side; Pixel is browser-side. Both can coexist.
   The audit checks both and their deduplication setup.

5. **Ignoring the change history log.** The most revealing signal in any account. Who changed bids?
   When? What happened to performance after? Essential for diagnosing inherited account problems.

6. **Treating "ad strength" as a vanity metric.** Google uses asset coverage for auction eligibility.
   Poor ad strength = fewer auctions entered = lower impression share at same budget.

---

## NOTES FOR THE ARTISAN

**God Mode QA checklist (use before delivering audit to Sara):**
- [ ] Ad Strength: all RSAs reported with actual label (Poor/Good/Excellent), not assumed
- [ ] CAPI Match Rate: actual EMQ score from Events Manager, not estimated
- [ ] IVT rate: pulled from Competitive Metrics column, last 30 days
- [ ] Duplicate conversions: verified by comparing "all conversions" vs. "conversions" column
- [ ] Enhanced Conversions match rate: verified in Conversions > Settings, not assumed

**Pre-sales delivery format:**
Sara presents the Executive Summary (1 page max) in the prospect meeting.
Full audit report is the onboarding deliverable after contract signing.
Never send the full checklist to a prospect — it overwhelms and gives away the methodology.

**Italian SME psychology note:**
Italian SME owners respond to: "stai sprecando X euro al mese" not "your ROAS is suboptimal."
Always translate every finding into euros and timeframe. Concrete, not abstract.

**Integration with Measurer agent:**
After audit findings, Measurer validates tracking fixes and sets up ongoing KPI monitoring
against the benchmarks established in this audit. The audit is the baseline; Measurer owns ongoing measurement.

**Typical audit timeline:**
- Data collection + access: 30-60 min
- Domain 1-4 audit: 90 min
- Domain 5-8 audit: 60 min
- Report writing: 60 min
- Total: 4-5 hours per account (billable or pre-sales)
