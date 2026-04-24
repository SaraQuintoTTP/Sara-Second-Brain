# CHECKPOINT — Knowledge Skills Population (T016)
## Data: 2026-04-24 | Status: IN_PROGRESS (~50% completato)

---

## 1. COSA È STATO FATTO IN QUESTA SESSIONE

### File Knowledge Skills creati/revisionati
| File | Path | Righe | Status |
|------|------|-------|--------|
| swot-quickref.md | /skills/knowledge/analysis/ | 96 | ✅ v2 approvata |
| porter-5forces-quickref.md | /skills/knowledge/analysis/ | 120 | ✅ v3 approvata |
| aida-quickref.md | /skills/knowledge/marketing/ | 31 | ✅ deprecato (status: historical_reference) |
| messy-middle-b2c-quickref.md | /skills/knowledge/marketing/ | 94 | ✅ nuovo, approvato |
| messy-middle-b2c-deep.md | /skills/knowledge/marketing/ | 284 | ✅ nuovo, approvato |
| b2b-buying-journey-quickref.md | /skills/knowledge/marketing/ | 120 | ✅ nuovo, approvato |
| b2b-buying-journey-deep.md | /skills/knowledge/marketing/ | 345 | ✅ nuovo, approvato (include contesto italiano + SMB variant) |

### Meta-deliverable creato
- `/operations/procedure/quickref_protocol.md` — Protocollo v1.1 TTP per Quick References (Checklist 7 criteri + First Principles Thinking)

### File di sistema aggiornati
- `/system/task_list.md` — T011-T013 spostate in COMPLETED (Priorità 2 briefing); T016 aggiunta con progress log
- `/system/session.md` — aggiornato con stato sessione 2026-04-24
- `/system/decisions_log.md` — aggiunte D006-D011
- `/DIARIO_DI_BORDO.md` — aggiornato stato + 6 nuove righe in COMPLETATI + 6 nuove decisioni

---

## 2. QUICKREF PROTOCOL v1.1 (riassunto per future sessioni)

### 7 Criteri obbligatori per ogni quickref
1. **When to use** + **When NOT to use** (entrambi esplicitati)
2. **Matrice/componente principale** con esempi-tipo PMI (no solo descrizione astratta)
3. **Tempo-sforzo** per una sessione PMI dichiarato (differenziare micro / media)
4. **Cross-reference ≥ 4 framework** per pertinenza reale (NO forzature tipo Sportelli)
5. **Errori comuni** ancorati a pattern osservabili nelle PMI italiane
6. **Quick Example PMI concreto** con decisione, numeri, GO/NO-GO
7. **Verificabilità**: ogni affermazione forte citata con fonte OR dichiarata come estrapolazione/corollario TTP; MAI attribuita erroneamente all'autore

### Principio trasversale — First Principles Thinking (FPT)
Quando adatto un framework pensato per grandi imprese a PMI italiane:
1. Identificare le assunzioni del framework originale (risorse, dati, team)
2. Scomporre fino alle verità fondamentali (leggi economiche, pattern comportamentali documentati)
3. Mappare i vincoli PMI (budget, velocità decisionale, owner = operatore)
4. Ricostruire nativamente (non miniaturizzare — redesign per il contesto)

### Budget righe
- Quick Reference: max 120 righe
- Deep Knowledge: max 350 righe
- Deroghe solo con compressione compensativa altrove

---

## 3. COSA RESTA DA FARE — T016

### Quickref restanti (in ordine)
1. `pas-quickref.md` (marketing)
2. `maurya-lean-canvas-quickref.md` (strategy)
3. `deveglia-positioning-quickref.md` (strategy)
4. `christensen-jtbd-quickref.md` (strategy)
5. `miller-storybrand-quickref.md` (marketing)
6. `collins-hedgehog-quickref.md` (strategy)
7. `pestel-quickref.md` (analysis)

### Deep restanti
1. `porter-5forces-deep.md`
2. `christensen-jtbd-deep.md`
3. `miller-storybrand-deep.md`
4. `collins-hedgehog-deep.md`

### Priorità 3 (briefing 2026-04-24) — non ancora affrontata
Decisione sulla SKILL.md Orchestrator (~570 righe, eccede limite 1.500 token):
- **Opzione A**: SNELLIRE portando sotto 1.500 token (spostare F09-F10, Plan Enrichment Rules, Cost Estimates in documento operativo o in PROTOCOLS.md)
- **Opzione B**: ECCEZIONE DOCUMENTATA (tenere lungo + nota nel blueprint v5.0)

### Priorità 4 (nuova) — dopo Priorità 1-3
Knowledge Processing pipeline su libreria Drive "epub Business e Marketing" (98+ epub, accessibile via Drive MCP con ID cartella 1h5xRKtacqSjeUb2Qs2EpSOWqvvpxTqpc). Processo a 5 step previsto:
1. Enumerazione completa (estrarre elenco paginando il Drive)
2. Triage in 4 cluster (A oro / B italiani utili PMI / C valore parziale / D non pertinente)
3. Estrazione batch da .epub (unzip + parsing XHTML)
4. Proposta skill per ogni libro approvato
5. Creazione file solo dopo approvazione

---

## 4. LESSONS LEARNED (per Artisan future sessions)

1. **Non fidarsi della prima stesura** — Sara ha chiesto "è il meglio che puoi fare?" due volte (SWOT e Porter). Risposta onesta con audit rigoroso → scoperta di miglioramenti sostanziali. Integrare audit preventivo come parte del processo.

2. **Attribuzioni rigorose** — scoperto errore attribuzione Porter ("concentrati su una forza" non è Porter, è estrapolazione TTP). Risolto con citazione Porter HBR 2008 + 80/20 Koch + Goldratt TOC dichiarati. Applicare Criterio 7 sistematicamente.

3. **Framework obsoleti** — AIDA come caso studio: Sara ha giustamente insistito per sostituirlo. Quando un framework è intrinsecamente datato, proporre sostituzione moderna invece di applicare Checklist su un fondamento debole.

4. **Contesto italiano specifico** — importanza di dedicare sezioni dedicate (distretti, agenti, fiere, commercialisti gatekeeper, pagamenti lunghi, LLM in italiano) per ogni framework B2B/B2C. NON è cosmetico: è il cuore del valore TTP.

5. **Step-by-step approvato** — ritmo "1 file alla volta, approvazione prima del successivo" funziona. Tentativo "2 in blocco" (SWOT + Porter inizialmente proposto) rigettato da Sara. Rispettare ritmo lento.

6. **Rendimenti decrescenti** — dopo 2-3 iterazioni di audit su un file, riconoscere la zona di rendimenti decrescenti e proporre di fermarsi (vedi Porter v3 → v4: applicati 3 gap su 10 identificati, altri rigettati per over-engineering).

---

## 5. FILE DI RIFERIMENTO PER LA PROSSIMA SESSIONE

### Documenti di sistema da leggere all'inizio
- `/knowledge_base/ttp_internal/TTP_Agency_Operative_v5.0.md` — documento operativo (sezione 11 sui 2-tier knowledge)
- `/operations/procedure/quickref_protocol.md` — Checklist v1.1 + FPT (obbligatorio)
- `/system/task_list.md` — progress log T016
- `/system/session.md` — stato sessione
- `/system/progress/knowledge_skills_population_checkpoint_2026-04-24.md` — questo file
- `/skills/knowledge/strategy/sportelli-connection-funnel-quickref.md` — benchmark qualitativo italiano

### Benchmark di qualità (file già approvati da Sara)
- `/skills/knowledge/analysis/swot-quickref.md` (v2) — struttura con TOWS-centric, domande-trigger
- `/skills/knowledge/analysis/porter-5forces-quickref.md` (v3) — DOMANDA-FILO FPT, LIMITI empirici + qualitativi, esempi settori diversi
- `/skills/knowledge/marketing/b2b-buying-journey-deep.md` — modello di deep ricco con contesto italiano e varianti

### Regole linguistiche
- **Italiano** per contenuto quickref/deep (come Sportelli benchmark)
- **Inglese** per file infrastrutturali (task_list, session, decisions_log, protocol)
- Termini inglesi standard mantenuti se diffusi (customer journey, value proposition, buyer, etc.)

---

## 6. AUTORIZZAZIONI DISPONIBILI

- **Google Drive** (sara.quinto87@gmail.com) — accesso verificato a cartella "Formazione" (ID 1PvqJIjQeEtAbQePYnqoTjDXiKbd6AWko) e sottocartella "epub Business e Marketing" (ID 1h5xRKtacqSjeUb2Qs2EpSOWqvvpxTqpc, 98+ epub). Trigger Drive tools: load via ToolSearch con "select:mcp__b670e5e3-b519-4971-b059-35fc0e7f7f1e__*"
- **WebSearch** — on-demand per verificare framework, con fonti super attendibili (HBR, McKinsey, Gartner, Forrester, Stanford, Think with Google, fs.blog). NO blog SEO-driven.
- **Shell sandbox** — disponibile per manipolazione file .epub (unzip + parsing) in Priorità 4

---

## 7. METRICHE DELLA SESSIONE

- Durata sessione: ~1 giornata lavorativa equivalente
- File creati: 7 (5 quickref + 2 deep)
- File revisionati: 1 (AIDA sfoltito)
- Meta-deliverable creati: 1 (quickref_protocol.md)
- File di sistema aggiornati: 4 (task_list, session, decisions_log, DIARIO_DI_BORDO)
- Ricerche WebSearch: 8+ (tutte con fonti primarie attendibili)
- Iterazioni di revisione su singolo file: fino a 4 (SWOT) per raggiungere qualità attesa
- Progresso T016: 5/~15 quickref + 2/4 deep = ~40-50% completato
