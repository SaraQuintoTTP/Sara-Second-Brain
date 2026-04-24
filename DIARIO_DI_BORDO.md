# DIARIO DI BORDO — Costruzione TTP AI Agency v5.0

## Stato attuale
- **Fase:** Sessione manutenzione — Popolamento Knowledge Skills (T016) — ~50% completato
- **Ultimo aggiornamento:** 2026-04-24
- **Completato:** Sprint 0 ✓ + Sprint 1 ✓ + Popolamento priorità Knowledge Skills (5 quickref + 2 deep completate — 2026-04-24)
- **Prossimo step:** Completare T016 (quickref restanti: pas, lean canvas, positioning, jtbd, storybrand, hedgehog, pestel + 3 deep mancanti) + Priorità 3 (SKILL.md Orchestrator decision)
- **Blocchi:** Nessuno

---

## BACKLOG — Cosa resta da fare

### Sprint 0 — Infrastruttura — COMPLETATO
- [x] **A) Struttura directory** — Creata
- [x] **A) CLAUDE.md** — Posizionato in `.claude/CLAUDE.md`
- [x] **A) Spostare documenti** — Copiati in `/knowledge_base/ttp_internal/`
- [x] **A) File di sistema** — `task_list.md`, `session.md`, `decisions_log.md` creati
- [x] **B) Knowledge Skills** — 48 file placeholder creati in `/skills/knowledge/` (contenuti da popolare in sessione dedicata)
- [x] **C) Catalogo Flussi** — `flow_catalog.md` + 8 file flusso creati in `/operations/procedure/`
- [x] **D) SKILL.md Artigiano** — Creata in `/skills/artigiano/SKILL.md` (blueprint v5.0, 8 sezioni, 2 modalita')
- [x] **E) Report finale Sprint 0** — Fatto
- [x] **F) Conversione EN** — Tutti i file infrastrutturali convertiti in inglese (decisione D004)
- [x] **G) Pulizia root** — Rimossi 3 file duplicati (CLAUDE_TTP_Agency.md, TTP_Agency_Operative, Architecture)
- [x] **H) .gitignore** — Creato per secrets, OS files, IDE folders

### Sessione dedicata — Popolamento Knowledge Skills (da pianificare)
- [ ] Popolare le 48 Quick Reference e Deep Knowledge con contenuti reali
- [ ] Priorita': framework usati da piu' agenti (SWOT, Porter, AIDA, PAS, Lean Canvas)
- [ ] I corsi di Sara (Aliotta, Abate) richiedono i suoi materiali/appunti

### Sprint 1 — Core strategico
- [x] SKILL.md Orchestrator (SKILL.md + PROTOCOLS.md — architettura a 2 file)
- [x] SKILL.md Strategist
- [x] SKILL.md God Mode
- [x] SKILL.md Sparring Partner
- [ ] Test flusso hub-and-spoke

### Sprint 2 — Revenue (Architect, Explorer, Calculator)
### Sprint 3 — Content (Voice, Editor, Narrator)
### Sprint 4 — Execution (Director, Measurer, Web Tech, Optimizer)
### Sprint 5 — Support (Accountant, Legal, Admin, Trainer)
### Sprint 6 — Advisory + audit (Mentor, Sparring Partner, Economist, Maintainer)

---

## COMPLETATI

| Data | Cosa | Note |
|------|------|------|
| 2026-03-25 | Lettura e analisi completa dei 4 file di progetto | Quadro completo acquisito |
| 2026-03-25 | Creazione DIARIO_DI_BORDO.md | Richiesto da Sara per tracciabilita' tra sessioni |
| 2026-03-25 | Sprint 0A — Struttura directory | 15+ cartelle create, CLAUDE.md posizionato, doc copiati, file di sistema inizializzati |
| 2026-03-25 | Sprint 0B — Knowledge Skills placeholder | 48 file .md creati (7 categorie). Contenuti rimandati a sessione dedicata |
| 2026-03-25 | Sprint 0C — Catalogo Flussi | flow_catalog.md + 8 file procedura |
| 2026-03-25 | Sprint 0D — SKILL.md Artigiano | Prima SKILL.md del sistema, blueprint v5.0, 8 sezioni, 2 modalita' |
| 2026-03-25 | Verifica struttura + pulizia | Rimossi 3 duplicati dalla root, creato .gitignore |
| 2026-03-25 | Conversione EN di tutto il sistema | CLAUDE.md, Operativo, system/, operations/, skills/ — tutti in inglese |
| 2026-03-25 | Sprint 1 — SKILL.md Orchestrator | Architettura a 2 file: SKILL.md (core) + PROTOCOLS.md (on-demand). Aggiornato doc operativo con F09, F10, scope Narrator |
| 2026-03-26 | Test Flow 01 — BRAMO (cibo per cani fittizio) | Sistema testato end-to-end con 8 agenti, 6 fasi. Score finale: 7.3/10. v2 con pivot umoristico raggiunge score simile. Agenti lavorano con base knowledge (no SKILL.md ancora). |
| 2026-04-23 | Aggiornamento model ID → versioni correnti | opus-4 → claude-opus-4-6, sonnet-4 → claude-sonnet-4-6, haiku-4.5 → claude-haiku-4-5-20251001. Aggiornati: orchestrator/SKILL.md, artigiano/SKILL.md, TTP_Operative_v5.0.md, Architecture.md. Aggiornati session.md e task_list.md. |
| 2026-04-23 | Sprint 1 — SKILL.md Strategist | Creata in /skills/strategist/SKILL.md. 8 sezioni v5.0, modello Opus 4 fisso, 6 Quick Reference assegnate + Sara's proprietary KB, 5 output type. |
| 2026-04-23 | Sprint 1 — Strategist v5.1 update | Rivisto quickref stack: rimossi Collins/Lafley da quickref (declassati a deep), aggiunti Sportelli ConnectionFunnel® e Hormozi Offers. Aggiunta First Principles Rule in OPERATIVE FRAMEWORKS e QUALITY CHECKLIST. |
| 2026-04-23 | Sprint 1 — SKILL.md God Mode | Creata in /skills/god_mode/SKILL.md. Modello Opus 4 fisso, no Task tool, 7-dimension scorecard, verdetti PASS/PASS WITH RESERVATIONS/FAIL. First Principles Audit Rule integrata come lente trasversale sul scorecard. |
| 2026-04-23 | Sprint 1 — SKILL.md Sparring Partner | Creata in /skills/sparring_partner/SKILL.md. Modello Opus 4 fisso, sequenza 4 tool (First Principles + Pre-Mortem + Inversion + Steel Man). First Principles come primo tool della challenge sequence. Strategic Validation Mode (CONFERMATO/SCONSIGLIATO) per validazioni non pianificate. |
| 2026-04-23 | KB — sportelli-connection-funnel-quickref.md | Creata in /skills/knowledge/strategy/. Basata sul libro reale (Il Succo del Web Marketing, 2018). Include ConnectionFunnel®, Domanda Consapevole®, Domanda Latente®, sequenza 5 passi, 7 fasi progetto. Nota anti-allucinazione: "Strategia Invisibile" non è un framework Sportelli. |
| 2026-04-24 | Quickref Protocol v1.1 | Creato /operations/procedure/quickref_protocol.md. Checklist 7 criteri (when-not-to-use, esempi PMI, tempo-sforzo, cross-ref pertinenza, errori reali, quick example, verificabilità) + First Principles Thinking come metodo trasversale per destrutturare framework complessi per PMI italiane. Worked example: Porter 5 Forze adattato. |
| 2026-04-24 | SWOT quickref v2 | Popolata /skills/knowledge/analysis/swot-quickref.md (96 righe). Incluso: MATRICE TOWS come cuore operativo, 6 passi DA SWOT A TOWS, stress-test strategico (no pre-mortem), esempio ristorante Milano. Citazioni: Harvard Business Policy 1965, Weihrich 1982 (TOWS), Hill & Westbrook 1997. |
| 2026-04-24 | Porter 5 Forze quickref v3 | Popolata /skills/knowledge/analysis/porter-5forces-quickref.md (120 righe — saturo). DOMANDA-FILO FPT, LIMITI DEL FRAMEWORK (empirico McGahan-Porter 1997 + qualitativi), Corollario TTP dichiarato, 2 esempi (studio commercialista-startup + tornitura Brescia 18 dip.), scala score 1-5, nota 6ª forza Brandenburger-Nalebuff. |
| 2026-04-24 | AIDA deprecato (Opzione A2) | /skills/knowledge/marketing/aida-quickref.md ridotto a 31 righe come riferimento storico (status: historical_reference). Motivazione: framework 1898, superato da evidenza empirica Google 2020 + Gartner/Forrester 2024-2025. Uso residuo ammesso come ponte didattico con cliente. |
| 2026-04-24 | Messy Middle B2C — quickref + deep | Creati 2 file in /skills/knowledge/marketing/. Quickref (94 righe): 5 componenti (Trigger → Exploration ↔ Evaluation → Purchase → Experience) + 6 bias cognitivi Google + attention economy + flywheel + 2 esempi PMI (caseificio Asiago + brand outdoor). Deep (284 righe): fonti estese, 4 approfondimenti (Attention, ZMOT, Flywheel/Community McKinsey, Paid Loyalty), Complete Applied Example (detergenti eco €7M). |
| 2026-04-24 | B2B Buying Journey — quickref + deep | Creati 2 file in /skills/knowledge/marketing/. Quickref (120 righe — saturo): buying committee 6-13 ruoli, 6 jobs Gartner, dark funnel (G2/community/LLM), 5 framework combinati (ABM, Intent Data, Challenger, JOLT, Revenue Waterfall), 2 esempi (SaaS commesse + macchinari packaging). Deep (345 righe): 15 sezioni, Challenger + JOLT applicati, Adattamento contesto B2B italiano (8 punti: distretti, agenti, relazioni lunghe, fiere, commercialisti, pagamenti, preventivo, LLM italiano), variante SMB italiano transazionale <€5k ACV. |

---

## DECISIONI PRESE

| # | Data | Decisione | Motivazione | Alternativa scartata |
|---|------|-----------|-------------|---------------------|
| D001 | 2026-03-25 | Creare diario di bordo prima di Sprint 0 | Sara vuole tracciabilita' tra sessioni | Affidarsi solo alla memoria di Claude Code |
| D002 | 2026-03-25 | DIARIO_DI_BORDO.md resta nella root | E' un meta-documento sulla costruzione, non un file operativo dell'agenzia | Metterlo in /system/ |
| D003 | 2026-03-25 | Knowledge Skills: solo placeholder, contenuti in sessione dedicata | Sara vuole approfondire uno per uno con sessione ad hoc | Popolare tutto subito con framework pubblici |
| D004 | 2026-03-25 | Convenzione lingua: EN per infrastruttura, IT per output cliente/Sara | LLM piu' precisi con prompt inglesi; inglese ~25% piu' conciso per contenuto tecnico | Tutto in italiano |
| D005 | 2026-03-25 | No Art Director dedicato: scope visual direction assorbito dal Narrator | PMI italiane affidano visual identity a designer esterni; Narrator puo' produrre brief e mood board testuali | Aggiungere 23esimo agente Art Director |
| D006 | 2026-04-24 | Quickref Protocol v1.1 (7 criteri + FPT) | Servono criteri standard per tutte le quickref per qualità omogenea + FPT come metodo trasversale per destrutturare framework complessi per PMI | Lasciare ogni quickref senza standard |
| D007 | 2026-04-24 | "Stress-test strategico" sostituisce "pre-mortem" | Preferenza terminologica Sara | Mantenere "pre-mortem" Klein |
| D008 | 2026-04-24 | Deprecare AIDA, sostituirlo con Messy Middle B2C + B2B Buying Journey | AIDA 1898 obsoleto; evidenza empirica Google/Gartner/Forrester 2020-2025 | Mantenere AIDA come framework operativo del 2026 |
| D009 | 2026-04-24 | Aggiungere 2 quickref nuove (messy-middle-b2c + b2b-buying-journey) con deep | Lista Sprint 1 originale non copriva framework moderni | Tenere solo i 10 framework della lista originale |
| D010 | 2026-04-24 | Autorizzato accesso Drive Sara per libreria "epub Business e Marketing" | Knowledge Processing pipeline futura (Priorità 4) su 98+ libri | Mantenere solo framework già identificati |
| D011 | 2026-04-24 | Rigor verificabilità: ogni affermazione forte citata o dichiarata come estrapolazione TTP | Prevenire allucinazioni da sintesi fluida (caso Porter Core Thesis risolto con citazione Porter HBR 2008 + 80/20 Koch + Goldratt TOC) | Accettare attribuzioni imprecise nel testo |

---

## PROPOSTE E ALTERNATIVE DISCUSSE

| # | Data | Proposta | Scelta di Sara |
|---|------|----------|----------------|
| P001 | 2026-03-25 | Dove mettere il diario: root (A) vs /system/ (B) | A — root |
| P002 | 2026-03-25 | Knowledge Skills: popolare subito vs placeholder + sessione dedicata | Sessione dedicata |
| P003 | 2026-03-25 | Lingua sistema: EN infrastruttura + IT output (A) vs tutto IT (B) | A — convenzione bilingue |
| P004 | 2026-03-25 | Art Director dedicato (A) vs scope visual assorbito dal Narrator (B) | B — niente Art Director, Narrator esteso |

---

## NOTE E OSSERVAZIONI

- Sara vuole essere coinvolta nelle decisioni: proporre alternative con spiegazioni chiare, lasciarla scegliere
- Il progetto e' ambizioso ma ben documentato — i 3 file coprono architettura, operativo e setup
- I materiali proprietari di Sara (corsi, template, metodologie) verranno caricati dopo
- L'architettura ha un graceful degradation: se le Quick Reference non esistono, gli agenti procedono con conoscenze base e segnalano
- Convenzione nomi file: EN per file infrastrutturali (flow_catalog.md, session.md), IT per file Sara-facing (DIARIO_DI_BORDO.md)
