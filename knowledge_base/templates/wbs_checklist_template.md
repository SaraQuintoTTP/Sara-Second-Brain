---
status: template
category: project-management
based_on: skills/knowledge/project-management/wbs-stage-gate-quickref.md, skills/knowledge/project-management/kanban-checklist-quickref.md
last_updated: 2026-07-27
---
# [NOME PROGETTO] — WBS & CHECKLIST OPERATIVA

> Deriva dal Project Charter (`project_charter_template.md`). Ogni riga è un'attività Kanban: colonne fisse, stato sempre aggiornato. I GATE separano le fasi e vanno attraversati consapevolmente — non si passa alla fase dopo senza che qualcuno lo approvi esplicitamente.

## Legenda colonne
| Colonna | Significato |
|---|---|
| Priorità | Alta / Media / Bassa |
| Effort | Ore stimate (±20%, si ritara a consuntivo) |
| Owner | Chi risponde del risultato (Accountable — una sola persona) |
| Operativo | Chi esegue materialmente (Responsible) |
| Stato | Da fare → In corso → Completato (max 2-3 "In corso" per persona — WIP limit) |
| Completamento % | Legato a criteri verificabili, non a sensazione |
| Note | Blocchi/dipendenze espliciti — se un'attività è bloccata, va scritto qui il motivo e la condizione di sblocco |

---

## FASE 0 — Pre-Sales / Scoping *(non fatturata)*

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

**▸ GATE 1 — [criterio di uscita, es. "Firma contratto + acconto"] — Approvatore: [ ] — Trigger commerciale: [ ]**

---

## FASE 1 — Concept & Kickoff

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

**▸ GATE 2 — [criterio di uscita, es. "Approvazione concept"] — Approvatore: [ ] — Trigger commerciale: [ ]**

---

## FASE 2 — Sviluppo / Produzione

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

**▸ GATE 3 — [criterio di uscita, es. "Pre-produzione chiusa, GO esecutivo"] — Approvatore: [ ] — Trigger commerciale: [ ]**

---

## FASE 3 — Rollout / Delivery

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

**▸ GATE 4 — [criterio di uscita, es. "Chiusura formale progetto"] — Approvatore: [ ] — Trigger commerciale: [ ]**

---

## FASE 4 — Verifica / Retrospettiva

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | Raccolta dati + consuntivo ore vs preventivo | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |
| [ ] | [ ] | Retrospettiva interna (lessons learned) | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

---

## FASE 5 — Upsell / Terzo livello *(opzionale, solo se rilevante)*

| Task Principale | Priorità | Descrizione Attività | Effort (h) | Owner | Operativo | Data Inizio | Data Fine | Stato | % | Note |
|---|---|---|---|---|---|---|---|---|---|---|
| [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | Da fare | 0% | [ ] |

---

## CHECK EFFORT (riepilogo costo)

> Nota: questo blocco in .md richiede ricalcolo manuale. Per il calcolo automatico (somma ore per fase e totale, costo, menu a tendina Stato/Priorità, colori Kanban) usa la versione gemella `/knowledge_base/templates/project_wbs_kanban_template.xlsx` — stessa struttura, formule live. Questo file .md resta il riferimento testuale che l'agente Director legge/scrive in autonomia.

| Voce | Valore |
|---|---|
| Ore Totali Progetto | [somma manuale colonna Effort di tutte le fasi] |
| Costo €/ora | [ ] |
| Costo ore | [ore × €/ora] |
| Altri costi (tool, campagne, ecc.) | [ ] |
| **TOTALE COSTO** | [ ] |

---
*Template — parte del framework `wbs-stage-gate-quickref.md` + `kanban-checklist-quickref.md`. Aggiungere/rimuovere righe e fasi secondo la scala reale del progetto — il pattern a 5 fasi è un punto di partenza, non un obbligo.*
