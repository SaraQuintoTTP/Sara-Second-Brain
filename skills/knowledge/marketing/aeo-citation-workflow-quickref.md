---
framework: AEO/GEO Citation Workflow (Answer Engine Optimization / Generative Engine Optimization)
author: msitarzewski/agency-agents
type: quickref
category: marketing
status: active
agents: [Web Tech, Editor]
---

# AEO/GEO CITATION WORKFLOW — Quick Reference

**When to use**: Client asks "why doesn't our brand appear when people ask AI assistants about [category]?"

**When NOT to use**:
- Pure Google rankings problem → `seo-audit` + `seo-fundamentals`
- Client has zero online content to optimize (build content first)
- Budget <€500/month total marketing: AEO ROI horizon is 3-6 months, not justified

**Effort-time PMI italiana**: 3-5h initial audit + fix pack (40 prompts, 4 platforms). Recheck: 1h every 14 days. Total 30-day: ~8-10h.

---

## THE 5-PHASE WORKFLOW

**Phase 1 — Discovery (45 min)**: Define brand, domain, 2-4 competitors, ICP. Generate 20-40 prompts in 4 intent buckets (10 each): Recommendation ("Miglior [cat] per [use case]"), Comparison ("[A] vs [B]"), How-to ("Come scegliere [prodotto]"), Best-of ("Top [cat] in Italia 2026").

**Phase 2 — Audit (90 min)**: Query all 4 platforms (ChatGPT, Claude, Gemini, Perplexity). Record: brand cited? competitor cited? positioning? citation format? Run each prompt 2x; use less favorable result for conservative baseline. Non-deterministic warning: results vary run-to-run.

**Phase 3 — Analysis (45 min)**: Map competitor content format advantages. Identify gaps: missing pages, schema, entity signals. Score: citation rate % per platform + per intent bucket. Category average = mean of top-3 competitors' rates (TTP extrapolation).

**Phase 4 — Fix Pack (60 min)**: Prioritize by expected citation impact (P1=7 days, P2=30 days, P3=backlog). Generate assets: FAQPage schema blocks, comparison page outlines. Schedule 14-day recheck. Never guarantee outcomes: say "improve citation likelihood."

**Phase 5 — Recheck & Iterate (60 min at day 14, then monthly)**: Re-run identical prompt set. Measure delta per platform + per intent bucket. Remaining gaps → next fix pack. Track over time: citation behavior shifts with model updates.

---

## KEY TEMPLATES

**Citation Audit Scorecard**:
| Platform | Prompts | Brand Cited | Competitor | Citation Rate | Gap |
|----------|---------|-------------|------------|---------------|-----|
| ChatGPT | 40 | XX | XX | XX% | -XX% |
| Claude | 40 | XX | XX | XX% | -XX% |
| Gemini | 40 | XX | XX | XX% | -XX% |
| Perplexity | 40 | XX | XX | XX% | -XX% |

**Lost Prompt Log**: `| Prompt | Platform | Who Cited | Why They Win | Priority |` — fill per prompt; P1 = high-volume queries with clear competitor content advantage.

**Fix Pack entry**: `Fix N: [action] → Target prompts: X → Expected impact: +XX% citation rate (TTP extrapolation) → Implementation: [schema / content / entity step]`

---

## PLATFORM CITATION PREFERENCES
| Platform | Wins With |
|----------|-----------|
| ChatGPT | FAQ pages, comparison tables, how-to guides |
| Claude | Detailed analysis, pros/cons, sourced content |
| Gemini | Schema-rich pages, Google Business Profile |
| Perplexity | News mentions, blog posts, real-time sources |

Source: msitarzewski/agency-agents. TTP extrapolation: preferences shift with model updates — revalidate quarterly.

**Entity optimization**: consistent brand name across all owned content + Organization/Product schema + GBP verified + cross-references in authoritative third-party sources.

---

## COMMON MISTAKES — PMI ITALIANA PATTERN
- **Testa 1 sola piattaforma**: tipicamente solo ChatGPT → miss del 60-70% del quadro. Sempre tutte e 4.
- **Ottimizza senza baseline**: implementa fix senza misurare prima → non può dimostrare impatto a cliente.
- **Confonde ranking Google con AI citation**: top-3 su Google può avere 0% citation rate su Claude. Metriche separate.
- **Timeline irrealistiche**: AEO = 30-90 giorni. Gestire l'aspettativa del cliente PMI è critico.
- **FAQ generiche**: il modello cita FAQ che matchano ESATTAMENTE il pattern della query. Reverse-engineer dal prompt set.
- **Ignora entity signals**: PMI locale senza Crunchbase/Wikidata → ambiguità entità per ChatGPT. Un profilo base risolve.

---

## QUICK EXAMPLE — PMI ITALIANA

**Ottica Visione Chiara**, Torino, 8 dipendenti, €1.8M fatturato. Competitor GrandOttica domina AI citation.

Audit: 20 prompts → citation rate Visione Chiara 15% vs. GrandOttica 70%.
Gap analysis: GrandOttica ha FAQ schema "Come scegliere lenti progressive" + comparison page "Ottici Torino" + 12 citazioni locali. Visione Chiara: nessuna.

Fix Pack P1 (7 giorni): (1) Pagina FAQ lenti progressive + FAQPage schema → target 6 how-to prompts. (2) Organization schema + GBP verificato → boost Gemini. (3) 3 citazioni su directory ottici locali → entity signal.

**GO**: citation rate ≥35% su ≥2 piattaforme in 30 giorni. **NO-GO**: nessun movimento → audit content quality o brand authority.

---

## CROSS-REFERENCES
- `geo-fundamentals` (Web Tech) — principi GEO/AEO base
- `seo-fundamentals` — technical signals che influenzano AI citation (schema, E-E-A-T)
- `schema-markup` — implementazione FAQPage, Organization, Product schema
- `content-creator` — produzione FAQ e comparison content AI-optimized
- `seo-technical-audit-deep` — CWV e technical foundation complementare

*Source: msitarzewski/agency-agents, marketing-ai-citation-strategist.md. PMI adaptation, effort estimates, GO/NO-GO: TTP extrapolation.*
