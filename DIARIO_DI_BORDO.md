# DIARIO DI BORDO — Costruzione TTP AI Agency v5.0

## Stato attuale
- **Fase:** Sprint 0 — COMPLETATO
- **Ultimo aggiornamento:** 2026-03-25
- **Prossimo step:** Sprint 1 — SKILL.md dei 3 agenti core (Orchestratore, Stratega, God Mode) + test flusso
- **Blocchi:** Nessuno

---

## BACKLOG — Cosa resta da fare

### Sprint 0 — Infrastruttura — COMPLETATO
- [x] **A) Struttura directory** — Creata
- [x] **A) CLAUDE.md** — Posizionato in `.claude/CLAUDE.md`
- [x] **A) Spostare documenti** — Copiati in `/knowledge_base/ttp_internal/`
- [x] **A) File di sistema** — `task_list.md`, `sessione.md`, `decisions_log.md` creati
- [x] **B) Knowledge Skills** — 44 file placeholder creati in `/skills/knowledge/` (contenuti da popolare in sessione dedicata)
- [x] **C) Catalogo Flussi** — `catalogo_flussi.md` + 8 file flusso creati in `/operations/procedure/`
- [x] **D) SKILL.md Artigiano** — Creata in `/skills/artigiano/SKILL.md` (blueprint v5.0, 8 sezioni, 2 modalita')
- [x] **E) Report finale Sprint 0** — Fatto

### Sessione dedicata — Popolamento Knowledge Skills (da pianificare)
- [ ] Popolare le 44 Quick Reference e Deep Knowledge con contenuti reali
- [ ] Priorita': framework usati da piu' agenti (SWOT, Porter, AIDA, PAS, Lean Canvas)
- [ ] I corsi di Sara (Aliotta, Abate) richiedono i suoi materiali/appunti

### Sprint 1 — Core strategico
- [ ] SKILL.md Orchestratore
- [ ] SKILL.md Stratega
- [ ] SKILL.md God Mode
- [ ] SKILL.md Sparring Partner
- [ ] Test flusso hub-and-spoke

### Sprint 2 — Revenue (Architetto, Esploratore, Calcolatore)
### Sprint 3 — Content (Voce, Editore, Narratore)
### Sprint 4 — Execution (Regista, Misuratore, Tecnico Web, Ottimizzatore)
### Sprint 5 — Support (Commercialista, Legale, Admin, Formatore)
### Sprint 6 — Advisory + audit (Mentore, Sparring Partner, Economo, Manutentore)

---

## COMPLETATI

| Data | Cosa | Note |
|------|------|------|
| 2026-03-25 | Lettura e analisi completa dei 4 file di progetto | Quadro completo acquisito |
| 2026-03-25 | Creazione DIARIO_DI_BORDO.md | Richiesto da Sara per tracciabilita' tra sessioni |
| 2026-03-25 | Sprint 0A — Struttura directory | 15+ cartelle create, CLAUDE.md posizionato, doc copiati, file di sistema inizializzati |
| 2026-03-25 | Sprint 0B — Knowledge Skills placeholder | 44 file .md creati (6 categorie). Contenuti rimandati a sessione dedicata |
| 2026-03-25 | Sprint 0C — Catalogo Flussi | catalogo_flussi.md + 8 file procedura (flusso_01 a flusso_08) |
| 2026-03-25 | Sprint 0D — SKILL.md Artigiano | Prima SKILL.md del sistema, blueprint v5.0, 8 sezioni, 2 modalita' |

---

## DECISIONI PRESE

| # | Data | Decisione | Motivazione | Alternativa scartata |
|---|------|-----------|-------------|---------------------|
| D001 | 2026-03-25 | Creare diario di bordo prima di Sprint 0 | Sara vuole tracciabilita' tra sessioni | Affidarsi solo alla memoria di Claude Code |
| D002 | 2026-03-25 | DIARIO_DI_BORDO.md resta nella root | E' un meta-documento sulla costruzione, non un file operativo dell'agenzia | Metterlo in /system/ |
| D003 | 2026-03-25 | Knowledge Skills: solo placeholder, contenuti in sessione dedicata | Sara vuole approfondire uno per uno con sessione ad hoc | Popolare tutto subito con framework pubblici |

---

## PROPOSTE E ALTERNATIVE DISCUSSE

| # | Data | Proposta | Scelta di Sara |
|---|------|----------|----------------|
| P001 | 2026-03-25 | Dove mettere il diario: root (A) vs /system/ (B) | A — root |
| P002 | 2026-03-25 | Knowledge Skills: popolare subito vs placeholder + sessione dedicata | Sessione dedicata |

---

## NOTE E OSSERVAZIONI

- Sara vuole essere coinvolta nelle decisioni: proporre alternative con spiegazioni chiare, lasciarla scegliere
- Il progetto e' ambizioso ma ben documentato — i 3 file coprono architettura, operativo e setup
- I materiali proprietari di Sara (corsi, template, metodologie) verranno caricati dopo
- I file originali (CLAUDE_TTP_Agency.md, TTP_Agency_Operative, Architecture) restano nella root come backup — possono essere rimossi quando Sara vuole
- L'architettura ha un graceful degradation: se le Quick Reference non esistono, gli agenti procedono con conoscenze base e segnalano
