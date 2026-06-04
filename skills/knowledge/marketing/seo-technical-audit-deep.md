---
framework: SEO Technical Audit — Advanced Complement
author: msitarzewski/agency-agents
type: deepknowledge
category: marketing
status: active
agents: [Web Tech]
---

# SEO TECHNICAL AUDIT — Deep Knowledge
## Complement to `seo-audit` + `seo-fundamentals` (do NOT duplicate those)

> **Loading note**: Load this file ONLY when the task requires (a) cannibalization audit, (b) Core Web Vitals audit with explicit thresholds, or (c) algorithm update recovery. For general SEO work, `seo-audit` + `seo-fundamentals` are sufficient.

**What this file adds that existing skills do NOT cover**:
1. Cannibalization audit as a mandatory blocker (Phase 2.5)
2. Technical SEO audit template with exact CWV thresholds
3. Algorithm penalty recovery workflow
4. Link authority building tactics (PMI-scoped)

---

## CONTEXT & PRINCIPLES

### Why Cannibalization Is the #1 Overlooked Risk in PMI SEO
Most Italian PMEs run content without a formal content architecture. Over 12-24 months, multiple pages accumulate targeting the same keywords — blog posts, product pages, and landing pages competing for the same queries. Google splits crawl budget and ranking signals across multiple pages, reducing the authority of each. The result: the client has 3 pages on "consulenza marketing Milano" and none ranks in top 10.

**Fundamental truth** (Google Search Central documentation): Google assigns ranking signals at the page level. When multiple pages compete for the same query, PageRank is diluted across all of them rather than concentrated on one. Canonical tags and internal linking consolidate these signals. Source: Google Search Central, "Consolidate duplicate URLs", developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls.

**PMI-specific constraint**: Small teams publish reactively (new service → new page) without cross-checking existing content. A 3-year-old PMI website typically has 5-15 cannibalization conflicts undetected. This must be resolved BEFORE adding new content — adding optimized content on top of a cannibalization conflict amplifies the conflict.

### Core Web Vitals — Why These Exact Thresholds
Google confirmed CWV as a ranking signal in the Page Experience Update (June 2021, verified). Thresholds below are Google's official "Good" band (source: web.dev/vitals, google.com/search/docs/appearance/core-web-vitals):

- **LCP (Largest Contentful Paint)**: < 2.5s = Good | 2.5-4.0s = Needs Improvement | >4.0s = Poor
- **INP (Interaction to Next Paint)**: < 200ms = Good | 200-500ms = Needs Improvement | >500ms = Poor
  - Note: INP replaced FID as the official CWV metric in March 2024 (Google announcement, web.dev/inp)
- **CLS (Cumulative Layout Shift)**: < 0.1 = Good | 0.1-0.25 = Needs Improvement | >0.25 = Poor

---

## EXTENDED OPERATIVE RECIPE

### BLOCKER: Phase 2.5 — Cannibalization Audit
**Must complete before ANY title tag, H1, meta description, or content change.**

**Step 1 — Cross-Page Query Map**
Query Google Search Console with dimensions: `[page, query]` filtered to the target keyword cluster.
Export to spreadsheet. Flag any query where 2+ pages appear in the same export.

```markdown
# Cannibalization Audit: [Target Keyword Cluster]

## Cross-Page Query Map
| Query | Page A (URL) | Page A Pos | Page A Clicks | Page B (URL) | Page B Pos | Page B Clicks | Conflict? |
|-------|-------------|------------|---------------|-------------|------------|---------------|-----------|
| [kw1] | /page-a     | X.X        | XX            | /page-b     | X.X        | XX            | YES/NO    |
```

**Step 2 — Ownership Assignment**
For each conflicting query, assign ONE owner page based on:
- Which page has the most clicks/impressions on that query (data-driven)
- Which page's topic is the closest semantic match (intent alignment)
- Which page is the designated pillar/satellite for that topic (architecture)

```markdown
## Ownership Assignment
| Query | Current Winner (GSC) | Designated Owner | Action Required |
|-------|---------------------|-----------------|-----------------|
| [kw1] | /page-a             | /page-b         | consolidate / redirect / rewrite |
```

**Step 3 — Resolution Plan (one action per conflict)**
| Conflict Type | Resolution |
|---------------|------------|
| Two pages, same primary keyword, similar content | 301 redirect weaker page to owner |
| Two pages, same keyword, different intent | Rewrite non-owner to target a different subtopic; update title/H1 |
| Pillar + satellite targeting same head term | Remove head term from satellite title/H1; add internal link to pillar |
| Split impressions, both position 8-15 | Consolidate content into owner; canonical non-owner to owner |

**Step 4 — Sign-Off Gate**
- [ ] No two pages in cluster share same primary keyword in title tag or H1
- [ ] Canonical tags verified: all non-owner pages self-referencing OR canonicalized to owner
- [ ] Internal links: non-owner pages link TO owner for conflicting queries
- [ ] Cannibalization map signed off → proceed to Phase 3

---

### Technical SEO Audit Template (CWV-complete)

```markdown
# Technical SEO Audit: [Client] — [Date]

## 1. Crawlability & Indexation
- Robots.txt: allowed paths / blocked paths / sitemap declared?
- XML Sitemap: total URLs | indexed URLs (GSC) | coverage ratio | issues (404s, non-canonical URLs)
- Crawl waste: parameter URLs, faceted navigation, thin content pages → noindex/canonical/robots directives

## 2. Site Architecture
- Max click depth from homepage: X (target: ≤3 for key pages)
- Orphaned pages (0 internal links): count + list
- Redirect chains: identify and flatten (max 1 redirect hop)

## 3. Core Web Vitals (Field Data — GSC / PageSpeed Insights)
| Metric | Mobile | Desktop | Target | Status |
|--------|--------|---------|--------|--------|
| LCP    | X.Xs   | X.Xs    | <2.5s  | ✅/❌  |
| INP    | Xms    | Xms     | <200ms | ✅/❌  |
| CLS    | X.XX   | X.XX    | <0.1   | ✅/❌  |

**PMI quick wins for LCP**:
- Image optimization: WebP/AVIF format, compress hero image <100KB, add `fetchpriority="high"` to LCP element
- Hosting: shared hosting with LCP >3.5s → upgrade to VPS or managed WordPress hosting
- Remove render-blocking third-party scripts (cookie banners, chat widgets loaded synchronously)

**PMI quick wins for INP**:
- Defer non-critical JavaScript (analytics, social widgets)
- Avoid heavy WordPress page builders with inline JS on every page

**PMI quick wins for CLS**:
- Add explicit width/height to all `<img>` tags
- Reserve space for late-loading ads or banners with `min-height`

## 4. Structured Data
- Schema types present: [Article, Product, FAQ, HowTo, Organization, LocalBusiness]
- Validation: check via Google Rich Results Test (search.google.com/test/rich-results)
- Missing opportunities: [recommended schema for content types present]

## 5. Mobile & International
- Mobile-friendly: pass/fail (Google Mobile-Friendly Test)
- Hreflang: [only if multilingual — verify lang + region tags]
```

---

### Algorithm Recovery Workflow

**Step 1 — Identify Penalty Type**
| Signal | Likely Cause |
|--------|-------------|
| Traffic drop correlated with known Google update date | Core Update or Helpful Content Update |
| Manual Action in GSC | Link scheme, cloaking, thin content |
| Traffic drop + rankings stable but CTR collapsed | Title/description update by Google |
| Sudden loss on exact date, not update date | Technical issue (crawl block, accidental noindex) |

Source for confirmed update dates: Google Search Status Dashboard (status.search.google.com). Never attribute a drop to an algorithm update without checking the dashboard first.

**Step 2 — Remediation by Type**

*Core Update / Helpful Content recovery*:
- Audit flagged pages for E-E-A-T gaps: missing author bio, no cited sources, thin word count relative to top-ranked competitors
- Add: author credentials, editorial policy page, external citations, first-hand experience signals (photos, case studies, dates)
- Do NOT add thin content to boost word count — add only if it genuinely improves the page

*Link penalty (manual action)*:
- Export full backlink profile (Google Disavow Tool compatible export via GSC)
- Identify toxic links: exact-match anchor text at scale, link farms, irrelevant directories
- Disavow file format: domain-level disavow for mass toxic sources, URL-level for individual bad links
- Resubmit reconsideration request with documented cleanup evidence

*Accidental technical block*:
- Check: robots.txt blocking Googlebot, noindex tag added accidentally (common after CMS migration), canonical pointing to wrong URL
- Verify in GSC URL Inspection tool — "Crawled" status + canonical resolved correctly

**Step 3 — Recovery Timeline Expectations**
- Technical issues: recovery within 1-2 crawl cycles (days to 2 weeks)
- Helpful Content / Core Update: 2-6 months after remediation (confirmed Google guidance)
- Manual action (link): 30-90 days after reconsideration request approval
- TTP extrapolation: PMI sites with <500 pages typically see faster crawl-and-recovery than large sites; set client expectation at lower end of ranges above

---

### Link Authority Building (PMI-Scoped)

**Context**: Standard link-building playbooks assume budget for digital PR agencies and data research teams. PMI italiana has neither. The following is a TTP-reconstructed approach for solo/small team execution.

**Realistic PMI link acquisition (monthly)**:
| Tactic | Target Links/Month | Effort | Notes |
|--------|-------------------|--------|-------|
| Supplier/partner directory listings | 2-4 | Low | Suppliers often have partner pages; ask directly |
| Local press / trade association mentions | 1-3 | Medium | Communicate study/data/news via email pitch |
| Broken link reclamation | 1-2 | Low | Find broken links on industry sites pointing to defunct resources; offer replacement |
| Unlinked brand mentions | 1-3 | Low | Monitor with Google Alerts; email to request link |
| Guest posts on Italian sector blogs | 1-2 | High | Quality over quantity; focus on DR40+ Italian domains |

**NOT recommended for PMI** (cost/effort too high vs. benefit):
- Paying for link insertions (risky, Google-penalizable)
- Full digital PR campaigns (budget >€2k/month minimum viable)
- Creating linkable data assets (requires research budget and design)

**Toxic link ratio**: if >5% of backlink profile is toxic (GSC + Ahrefs/Semrush assessment), create disavow file BEFORE any new link building. Source: Google Webmaster Guidelines on link schemes.

---

## VARIANTS & ADAPTATIONS

### Budget <€500/month total SEO (micro-PMI, solo professionista)
- Skip full crawl tools (Screaming Frog license €/year) → use free GSC data + Ahrefs free tier or Ubersuggest
- Prioritize only: cannibalization audit (free, GSC only) + CWV fixes (free, PageSpeed Insights) + 1-2 schema additions
- Cannibalization fix alone often recovers 20-40% of "lost" rankings with zero budget (TTP extrapolation from Sara's consulting patterns)
- Link building: focus exclusively on supplier listings + unlinked mentions (zero-cost tactics)

### With Internal Team (PMI 5-20 employees, fatturato 3-12M€)
- Full Screaming Frog crawl + monthly rank tracking tool justified
- Assign content owner to maintain cannibalization map as content is published
- Monthly CWV check via PageSpeed Insights batch + GSC Core Web Vitals report
- Digital PR: 1-2 data studies/year (product certifications, customer surveys) → outreach to trade press
- Target: 5-10 quality links/month at this team size

---

## COMPLETE APPLIED EXAMPLE — Italian SME

**Client**: Studio Legale Marchetti & Associati, Bologna. 6 avvocati, fatturato €1.4M. Settore: diritto del lavoro + diritto societario.

**Problem**: 3 pages competing for "avvocato diritto del lavoro Bologna":
- /servizi/diritto-lavoro (main service page)
- /blog/licenziamento-illegittimo-bologna (blog post)
- /blog/diritto-lavoro-cosa-sapere (blog post)

GSC shows all 3 ranking between position 12-18, combined clicks < the single top competitor page at position 4.

**Cannibalization audit findings**:
- Owner: /servizi/diritto-lavoro (highest impressions + closest semantic match)
- Both blog posts: remove "Bologna" + "avvocato diritto del lavoro" from title/H1; redirect them to target long-tail subtopics only (licenziamento + contratto apprendistato respectively)

**CWV audit**:
| Metric | Mobile | Desktop | Status |
|--------|--------|---------|--------|
| LCP | 4.1s | 2.8s | ❌ Mobile |
| INP | 180ms | 90ms | ✅ |
| CLS | 0.05 | 0.03 | ✅ |

Fix: hero image (380KB PNG) → WebP 65KB + fetchpriority="high" → LCP mobile drops to ~2.2s.

**Structured data**: Add LocalBusiness + LegalService schema to /servizi pages (currently no schema). Add FAQPage schema to blog posts targeting how-to queries.

**Link building (month 1-3)**:
- 4 supplier/partner directory listings (Camere di Commercio, Confindustria Bologna directory, Ordine Avvocati)
- 2 unlinked mentions found via Google Alerts → converted to links (local press articles)

**GO/NO-GO at 90 days**:
- GO if: /servizi/diritto-lavoro moves from position 14 to ≤8; organic clicks +30% vs. baseline
- NO-GO trigger: rankings drop further after cannibalization fix → escalate (possible content quality issue requiring deeper rewrite)

---

## COMMON MISTAKES

- **Ottimizza prima di risolvere la cannibalizzazione**: aggiunge contenuto ottimizzato su una pagina già in conflitto. Amplifica il problema. Regola: cannibalization audit è un BLOCKER.
- **Usa solo dati lab (Lighthouse) invece di field data (GSC CWV)**: Lighthouse è utile per diagnosi, ma Google usa i CrUX field data per il ranking. Un sito può avere Lighthouse 90 e CWV "Needs Improvement" in field data per utenti reali su connessioni lente.
- **Attribuisce ogni calo a un algorithm update**: spesso è un accidentale noindex o un redirect rotto. Verificare GSC URL Inspection PRIMA di dichiarare penalty.
- **Punta a link ad alto DR subito**: con un budget PMI, meglio 5 link da directory/trade press italiane realmente pertinenti che nessun link perché la strategia è troppo ambiziosa.
- **Considera INP irrilevante**: molti SEO italiani non hanno ancora aggiornato le metriche da FID a INP (cambio ufficiale marzo 2024). INP >200ms conta come "Needs Improvement" per Google.
- **Non monitora CWV su mobile**: le PMI italiane hanno spesso 60-70% di traffico mobile. Un sito con mobile LCP 4s e desktop LCP 1.8s ha un problema CWV reale nonostante sembri performante su desktop.

---

## NOTES FOR THE ARTISAN

- **Cannibalization template** in this file is the original Phase 2.5 BLOCKER from msitarzewski/agency-agents — this is the most operationally distinctive element vs. standard SEO knowledge. Preserve it intact in future updates.
- **CWV thresholds** (LCP <2.5s, INP <200ms, CLS <0.1) are sourced from Google's official documentation and are periodically updated by Google. Flag if updated.
- **INP replacing FID**: confirmed March 2024. Existing TTP clients audited before that date may have outdated CWV reports using FID. If Sara brings a legacy audit, rerun with INP.
- **Algorithm Recovery timelines**: based on Google's documented guidance, NOT on case studies. PMI recovery speed extrapolated as TTP operational corollary (smaller sites = faster crawl cycles).
- **Link building approach for PMI**: intentionally scaled down from the source file. The original targets 20-33 links/month — unrealistic for Italian SME without dedicated budget. TTP version targets 5-12 links/month with zero-budget-first tactics. This is a TTP First Principles reconstruction, not a miniaturization.

---

*Source: msitarzewski/agency-agents, marketing-seo-specialist.md — Phase 2.5 cannibalization BLOCKER, Technical SEO Audit Template, Algorithm Recovery, Link Building strategy. CWV thresholds: Google Search Central / web.dev/vitals. PMI scope constraints, effort estimates, and GO/NO-GO criteria: TTP extrapolation.*
