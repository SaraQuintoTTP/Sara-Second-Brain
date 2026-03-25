# DIARIO DI BORDO — Costruzione TTP AI Agency v5.0

## Stato attuale
- **Fase:** Sprint 0 — COMPLETATO
- **Ultimo aggiornamento:** 2026-03-25
- **Prossimo step:** Sprint 1 — SKILL.md dei 4 agenti core (Orchestrator, Strategist, God Mode, Sparring Partner) + test flusso
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
- [ ] SKILL.md Strategist
- [ ] SKILL.md God Mode
- [ ] SKILL.md Sparring Partner
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

---

## DECISIONI PRESE

| # | Data | Decisione | Motivazione | Alternativa scartata |
|---|------|-----------|-------------|---------------------|
| D001 | 2026-03-25 | Creare diario di bordo prima di Sprint 0 | Sara vuole tracciabilita' tra sessioni | Affidarsi solo alla memoria di Claude Code |
| D002 | 2026-03-25 | DIARIO_DI_BORDO.md resta nella root | E' un meta-documento sulla costruzione, non un file operativo dell'agenzia | Metterlo in /system/ |
| D003 | 2026-03-25 | Knowledge Skills: solo placeholder, contenuti in sessione dedicata | Sara vuole approfondire uno per uno con sessione ad hoc | Popolare tutto subito con framework pubblici |
| D004 | 2026-03-25 | Convenzione lingua: EN per infrastruttura, IT per output cliente/Sara | LLM piu' precisi con prompt inglesi; inglese ~25% piu' conciso per contenuto tecnico | Tutto in italiano |
| D005 | 2026-03-25 | No Art Director dedicato: scope visual direction assorbito dal Narrator | PMI italiane affidano visual identity a designer esterni; Narrator puo' produrre brief e mood board testuali | Aggiungere 23esimo agente Art Director |

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
