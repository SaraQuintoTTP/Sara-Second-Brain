---
framework: Paid Social Strategy (Meta-First Full-Funnel)
author: msitarzewski/agency-agents
type: deepknowledge
category: paid-media
status: active
agents: [Measurer]
---

# Paid Social Strategy (Meta-First Full-Funnel) — Deep Knowledge
## Source: msitarzewski/agency-agents — Paid Social Strategist (John Williams @itallstartedwithaidea)

---

## CONTEXT & PRINCIPLES

Paid social is interruption-based advertising, not intent-based. You are not answering a query — you are inserting yourself into a scroll. This creates two non-negotiable requirements: (1) creative must earn attention in the first 2 seconds, and (2) audience engineering must be precise enough to justify the interruption.

**Core philosophy:** Each platform is its own ecosystem. Meta ≠ LinkedIn ≠ TikTok. User behavior, algorithm mechanics, and creative language differ radically. Repurposing the same asset across platforms is the single most common waste of paid social budget.

**For Italian SMEs (€500–3k/month ads):** Meta is the default primary channel. LinkedIn only if B2B with clear title/sector targeting and minimum €800/month budget. TikTok only if audience is under 35 and creative production capacity exists for native-format video. With limited budgets, platform discipline is more valuable than platform breadth.

**Why creative dominates now:** In automated bidding environments (Advantage+, CBO), the algorithm handles bids, targeting expansion, and budget distribution. What you actually control is creative. Creative quality is the primary performance lever.

**Key algorithm insight (Meta 2024+):** Meta's algorithm optimizes for engagement signals before conversion signals. An ad with poor hook/body/CTA structure will be deprioritized regardless of bid, because the system predicts low conversion likelihood from early engagement data.

---

## EXTENDED OPERATIVE RECIPE

### Step 1 — Audience Architecture (before touching Ads Manager)

Map three tiers before creating any campaign:

**Tier 1 — Cold Prospecting (new users):**
- Interest-based audiences (Meta broad + interest stacking)
- Lookalike audiences: 1–3% LAL from best customer list (min. 300 matched records for reliable LAL)
- Broad targeting with Advantage+ Audience enabled (let Meta expand beyond seed)
- For Italian SMEs: start with 1% LAL from purchasers/leads + broad fallback

**Tier 2 — Warm Engagement:**
- Video viewers (25%+ or 75%+ of key videos)
- Page engagers (30-day or 60-day window)
- Lead form openers (did not complete)
- Website visitors (30-day, all pages)

**Tier 3 — Hot Retargeting:**
- Website visitors (7-day, key product/service pages)
- Add-to-cart / Initiate checkout (ecommerce)
- CRM custom audiences (existing leads, past clients)
- Always exclude: past purchasers from prospecting campaigns

**Exclusion strategy:** Cross-exclude Tier 3 from Tier 1 at all times. This prevents wasted impressions on users already in the funnel and inflated cost-per-result in prospecting campaigns.

### Step 2 — Campaign Structure: CBO vs ABO Decision

**CBO (Campaign Budget Optimization):** Budget set at campaign level. Meta distributes across ad sets automatically.
- Use when: 3+ ad sets with similar audiences and objectives, trusting Meta's distribution
- Advantage: algorithm finds best-performing ad set combinations dynamically
- Risk for SMEs: one ad set can consume 80%+ of budget, starving test ad sets

**ABO (Ad Set Budget Optimization):** Budget set at ad set level. Manual control.
- Use when: testing new audiences against each other with equal spend, protecting specific segments (e.g., retargeting must not lose budget to prospecting)
- Advantage: predictable spend per audience tier, essential for budget-constrained PMI
- Rule for SMEs (€500–3k/month): **Default to ABO** until you have enough data (1,000+ conversions/month) to trust CBO distribution

**Recommended structure for Italian SME (€1,500/month Meta budget):**
```
Campaign 1 — Prospecting (ABO, €800/month)
  Ad Set 1A: Broad + Advantage+ (€400/month)
  Ad Set 1B: 1% LAL from best clients (€400/month)

Campaign 2 — Warm Retargeting (ABO, €400/month)
  Ad Set 2A: Website visitors 30-day (€200/month)
  Ad Set 2B: Video viewers 75% + Page engagers 60-day (€200/month)

Campaign 3 — Hot Retargeting (ABO, €300/month)
  Ad Set 3A: Website visitors 7-day + cart abandoners (€300/month)
```

### Step 3 — Advantage+ Configuration

**Advantage+ Shopping Campaigns (ASC):** For ecommerce. Fully automated — Meta controls audiences, placements, and creative combinations.
- When to use: ecommerce with pixel fully trained (500+ purchase events), creative library with 5+ distinct formats
- SME caveat: requires sufficient conversion volume. If under 50 purchases/month, stick to manual structure.

**Advantage+ Audience:** Audience targeting suggestion, not mandate. Meta can expand beyond defined audience signals.
- Toggle ON for prospecting campaigns as exploration layer
- Toggle OFF for retargeting (you need precision, not expansion)

**Advantage+ Creative:** Auto-enhances creatives (brightness, music, text overlays)
- SME recommendation: toggle OFF unless you have full brand alignment control. Auto-enhancements can look off-brand for professional services.

### Step 4 — Frequency Management

Frequency = average number of times each unique user has seen your ad within the reporting window.

| Funnel Stage | Target Frequency (7-day) | Action if Exceeded |
|---|---|---|
| Prospecting | 1.5 – 2.5 | Refresh creative immediately |
| Warm Retargeting | 3 – 5 | Acceptable, monitor CTR drop |
| Hot Retargeting | 5 – 8 | Acceptable for 7-day window |

**Fatigue signals:** CPM rising + CTR falling + Frequency above target = creative burnout. Refresh before ROAS collapses, not after.

**Monitoring cadence for SMEs:**
- Weekly: check frequency by ad set
- If prospecting frequency > 2.5 in 7 days → pause ad set or swap creative within 48 hours

### Step 5 — Measurement & CAPI Implementation

**Meta Pixel alone is insufficient post-iOS 14.5.** Browser-based tracking loses 20–40% of events depending on vertical and audience demographics.

**Conversions API (CAPI) — implementation priority for SMEs:**
- CAPI sends server-side events directly from your server to Meta, bypassing browser restrictions
- Minimum viable setup: server-side purchase + lead events with email match parameter
- Event Match Quality (EMQ) target: 6.0+ out of 10
- For SMEs without developer resources: use Meta's partner integrations (Shopify native CAPI, WooCommerce plugin, Zapier-to-CAPI for lead events)

**SKAdNetwork (iOS attribution):** Meta uses aggregated SKAdNetwork data for iOS campaign reporting. Accept that iOS conversion numbers will be modeled, not exact. Do not optimize campaigns solely based on iOS-attributed data.

**Attribution windows:** Default to 7-day click + 1-day view for most campaigns. Use 1-day click only for last-touch attribution analysis to reduce over-crediting.

**Incrementality check:** Before scaling any social campaign, validate that conversions are incremental. Simple method for SMEs: run a 2-week holdout test on 10% of retargeting audience. If conversion rate in holdout is within 15% of exposed group, social may be claiming credit for organic conversions.

### Step 6 — LinkedIn (B2B SME Context)

**Use LinkedIn only when:**
- Target audience is defined by professional attributes (job title, seniority, company size, industry)
- Minimum budget: €800/month (CPCs of €5–15 make LinkedIn unusable below this threshold)
- Offer is B2B with clear professional value proposition

**Campaign types for Italian SME B2B:**
- Sponsored Content (single image): awareness + lead gen
- Lead Gen Forms: higher completion rates than landing page (pre-filled data)
- Document Ads: for lead magnets, ebooks, guides (white-collar professional verticals)

**LinkedIn targeting precision:** Job title targeting is the most reliable. Company industry + seniority combinations can work but inflate audience size with low-fit users. For SMEs: be narrow and expensive rather than broad and cheap.

### Step 7 — Weekly Performance Review Cycle

Run this review every Monday morning:

1. Pull campaign-level ROAS/CPA vs. target
2. Check frequency by ad set (flag any prospecting > 2.5)
3. Review CTR trends by creative (identify declining assets)
4. Check Event Match Quality in Meta Events Manager
5. Review audience overlap warnings
6. Adjust budgets: shift toward best-performing ad sets (within ABO constraints)
7. Flag creative refresh needs for next 7 days

---

## VARIANTS & ADAPTATIONS

**Per PMI budget <€1k/mese ads:**
- One campaign only: combine prospecting + warm retargeting in separate ad sets under one campaign
- Max 2 active creatives per ad set (avoid fragmentation)
- Skip LinkedIn entirely. Allocate 100% to Meta.
- Prioritize Conversions API setup over any creative expansion — bad measurement kills optimization
- Use LAL from CRM list (even 100 past clients is enough for Italian geo-restricted targeting)

**Per PMI con team creativo interno:**
- Give internal team the Hook-Body-CTA brief template (see Applied Example below)
- Run 3 creative variants per ad set (test hook variations, not full concept variations)
- Establish a creative calendar: new creative batch every 3 weeks
- Internal teams should produce UGC-style content for Meta prospecting (performs 30–40% better than polished studio content in most Italian SME verticals)
- Reserve polished brand content for retargeting (users who already know the brand)

---

## COMPLETE APPLIED EXAMPLE (Italian SME)

**Client:** Studio dentistico in Milano, 4 poltroni, focus su implantologia e sbiancamento. Budget Meta: €1,200/mese.

**Audience Architecture:**
- Prospecting: LAL 1% da lista pazienti (800 record → buona base) + Broad 35–60, Milano +30km, interessi salute/benessere
- Warm: Website visitors 30-day + Video viewers 50%+
- Hot: Website visitors 7-day + chi ha cliccato su "Prenota Visita"

**Campaign Structure (ABO):**
- Camp. 1 Prospecting €650/mese: Ad Set A (LAL 1%, €350) / Ad Set B (Broad, €300)
- Camp. 2 Warm €300/mese: Ad Set A (Visitors 30d + Video viewers, €300)
- Camp. 3 Hot €250/mese: Ad Set A (Visitors 7d + intent signals, €250)

**Creative by funnel stage:**
- Prospecting: UGC-style testimonial video (paziente reale), hook "Ho aspettato 10 anni prima di sistemare i denti — non avrei dovuto", duration 30–45s
- Warm: Carousel "Prima/Dopo" con 3 casi clinici reali, CTA "Scopri se sei un buon candidato"
- Hot: Single image con offerta specifica ("Visita implantologia gratuita, fino al 30 giugno"), CTA urgency-driven

**CAPI Setup:** Shopify non applicabile. Usa integrazione nativa del CMS prenotazioni (o Zapier: "Lead completato → Meta CAPI lead event con email hash"). Target EMQ ≥ 6.0.

**Frequency targets:** Prospecting max 2.0/7gg. Hot retargeting accettabile fino a 7/7gg (audience piccola per geo).

---

## WEEKLY REPORT TEMPLATE

```
WEEKLY PAID SOCIAL REPORT — [CLIENT] — settimana [DATE]

PERFORMANCE SUMMARY
------------------
Spesa totale: €___  (budget: €___)
Leads/Conversioni totali: ___
CPL/CPA medio: €___  (benchmark: €___)
ROAS totale: ___x  (target: ___x)

PER CAMPAGNA
-----------
[Prospecting]  Spesa: €___ | Reach: ___ | Freq: ___ | CPL: €___
[Warm]         Spesa: €___ | Reach: ___ | Freq: ___ | CPL: €___
[Hot]          Spesa: €___ | Reach: ___ | Freq: ___ | CPL: €___

CREATIVE PERFORMANCE (top 3 ad)
-------------------------------
1. [Ad Name] — CTR: ___% | CPC: €___ | Conv: ___ | Status: ACTIVE/FATIGUE
2. [Ad Name] — CTR: ___% | CPC: €___ | Conv: ___ | Status: ACTIVE/FATIGUE
3. [Ad Name] — CTR: ___% | CPC: €___ | Conv: ___ | Status: ACTIVE/FATIGUE

ALERTS THIS WEEK
----------------
[ ] Frequency alert: [Ad Set] a ___ (soglia: 2.5) → azione: ___
[ ] Creative fatigue: [Ad] CTR sceso da ___% a ___% → refresh entro ___
[ ] EMQ: ___ (target ≥6.0) → azione se <6.0: ___

AZIONI SETTIMANA PROSSIMA
-------------------------
1. ___
2. ___
3. ___
```

---

## COMMON MISTAKES

1. **CBO troppo presto:** Con budget €500–1.5k/mese e pochi dati di conversione, CBO porta Meta a concentrare tutto su un ad set. Usare ABO fino a 500+ conversioni/mese.

2. **LAL su liste troppo piccole:** Lookalike sotto i 100 record producono audience instabili. Minimo 300 per LAL affidabile. Se lista piccola: usa engagement audiences come seed.

3. **Nessuna esclusione cross-funnel:** Mostrare annunci prospecting a clienti già acquisiti o a chi è in hot retargeting brucia budget e distorce i dati.

4. **Ignorare la frequenza in prospecting:** Frequency 4+ su prospecting = brand burnout + CPM in aumento + algoritmo che fatica a trovare nuovi utenti validi. Monitorare settimanalmente.

5. **Vantaggio+ Creative attivato senza controllo brand:** Le ottimizzazioni automatiche (colori, testi overlay) possono compromettere visual identity in settori professionali (legale, medico, finance).

6. **Solo pixel senza CAPI:** Post-iOS 14, il pixel da solo perde fino al 30–40% degli eventi. Senza CAPI, Meta ottimizza su dati incompleti.

7. **Testare tutto contemporaneamente:** Cambiare audience + creative + offerta nella stessa settimana rende impossibile capire cosa ha funzionato. Isolare una variabile per test.

8. **Attribution window a 28 giorni per decisioni settimanali:** Crea double-counting con le finestre default. Usare 7-day click + 1-day view come standard.

---

## NOTES FOR THE ARTISAN

- **Meta vs LinkedIn budget split:** Se cliente ha budget <€1.5k/mese totale, scegliere UN solo canale. Dividere è peggio che concentrare.
- **iOS modeled data:** Accettare che i numeri iOS siano modellati. Non ottimizzare su di essi in isolamento — usare CRM-verified conversions come source of truth.
- **Advantage+ Shopping:** Potente per ecommerce con storico consolidato. Per PMI che inizia, è una black box senza abbastanza dati. Iniziare manuale, poi testare ASC dopo 3 mesi di dati.
- **TikTok per PMI italiane:** Valutabile solo per B2C con audience 18–35. Richiede una creatività completamente nativa (non adattata da Meta). Budget minimo consigliato: €800/mese su TikTok in isolamento.
- **Incrementality per PMI:** Il test holdout formale è spesso impraticabile con audience piccole. Soluzione pragmatica: osservare se le conversioni organic/direct aumentano proporzionalmente quando spesa social sale. Correlazione sospetta = attribuire con cautela.
- **Agent handoff:** Questo file informa il Measurer nella fase di setup e monitoring campagne. Per la produzione di copy ads, passare a `paid-creative-strategy-deep.md`.
