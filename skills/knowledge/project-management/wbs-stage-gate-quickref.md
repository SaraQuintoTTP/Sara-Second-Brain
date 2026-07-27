---
framework: WBS & Stage-Gate
author: Work Breakdown Structure — origine attribuita a PERT/DoD-NASA anni '50-'60, formalizzata da Project Management Institute (PMBOK Guide); cronologia esatta non verificata da fonte primaria in questa sessione. Stage-Gate — Robert G. Cooper, "Winning at New Products" (1986) e "Stage-Gate Systems: A New Tool for Managing New Products" (1990). Il pattern di fasi specifico (Pre-Sales→Kickoff→Sviluppo→Rollout→Retrospettiva) NON è di Cooper — è un'osservazione TTP da 2 modelli operativi reali di Sara, vedi Core Thesis.
type: quickref
category: project-management
status: active
---
# WBS & STAGE-GATE — Quick Reference
## Source: PMI, *PMBOK Guide* (Work Breakdown Structure). Robert G. Cooper, *Winning at New Products* (1986); "Stage-Gate Systems", *Business Horizons*, 1990. Adattamento TTP: derivato dall'analisi di due modelli operativi reali di Sara (Project Charter + Checklist a fasi/gate; WBS a pacchetti con gate legati a incassi).
## When to use: All'avvio di ogni progetto multi-fase con più persone/agenti coinvolti — prima di iniziare l'esecuzione. **Sessione tipica PMI: 1-2h per costruire charter + WBS a fasi di un progetto medio.**

## WHEN NOT TO USE
- Task singolo con un solo owner e una sola consegna → è overhead, usa direttamente una riga di checklist (`kanban-checklist-quickref.md`)
- Progetto già in corso senza charter iniziale → serve prima un audit dello stato attuale, non un nuovo WBS da zero
- Retainer continuativo senza fasi distinte (es. gestione social mensile ricorrente) → usa solo `kanban-checklist-quickref.md`, i gate non si applicano a un flusso continuo
- Decisione strategica su COSA fare (non COME organizzarlo) → framework di Strategist, non questo

## CORE THESIS
Un progetto multi-fase non fallisce per mancanza di piano — fallisce per mancanza di **punti di controllo espliciti** dove qualcuno decide GO/NO-GO prima di spendere altro tempo o budget. Il WBS risponde a "cosa va fatto, in che ordine, chi lo fa"; lo Stage-Gate risponde a "quando possiamo davvero passare alla fase dopo".

**Nota di attribuzione (Criterio 7):** i gate di Cooper (Stage-Gate Systems, 1990) sono decisioni GO/NO-GO di sviluppo prodotto (continuare a investire in un nuovo prodotto o fermarsi) — non trigger di fatturazione. Il collegamento "gate approvato → milestone di pagamento sbloccata" **è un corollario TTP**, non un'idea di Cooper: nasce dall'osservazione di due modelli operativi reali di Sara dove i gate coincidono spesso con acconto/saldo. È un'estensione legittima e utile per un'agenzia di servizi, ma va trattata come tale, non come principio originale della fonte citata.

## FIRST PRINCIPLES THINKING (adattamento PMI)
1. **Assunzioni del framework originale**: Cooper scrive per team R&D strutturati con più stage-gate reviewer dedicati, cicli di mesi/anni, portafogli di più prodotti in parallelo.
2. **Verità fondamentale**: un progetto costa meno fermarlo presto (prima che il lavoro sia investito) che tardi — motivo per cui un punto di controllo esplicito, prima di procedere, ha valore economico reale, non solo procedurale.
3. **Vincoli PMI**: chi approva il gate spesso è la stessa persona che vende E gestisce il progetto (il titolare); non ci sono "gate review board" dedicati; il tempo per una revisione formale è quasi zero.
4. **Ricostruzione nativa TTP**: il gate resta (perché la verità fondamentale al punto 2 vale anche per una PMI), ma si riduce a una domanda esplicita con risposta scritta da qualcuno — anche se quel qualcuno è la stessa persona che ha eseguito il lavoro, l'atto di scriverlo esplicitamente (invece di procedere senza pensarci) è già la maggior parte del valore.

## STRUTTURA A 2 LIVELLI

**Livello 1 — WBS (scomposizione)**: progetto → fasi → macro-attività → sotto-attività. Ogni sotto-attività ha: chi ne risponde (Accountable), chi la esegue (Responsible — vedi `raci-quickref.md`), ore stimate, durata.

**Livello 2 — Gate (controllo)**: checkpoint tra una fase e la successiva. Un gate NON è una data sul calendario — è una domanda: "cosa deve essere vero per procedere?". Ha sempre: un criterio di uscita verificabile, un approvatore (spesso il titolare/cliente, non chi ha eseguito il lavoro), e — quando il progetto è a pagamento — un evento commerciale collegato.

## PATTERN DI FASI OSSERVATO (adattabile, non rigido)

| Fase | Contenuto tipico | Gate successivo | Trigger commerciale tipico |
|---|---|---|---|
| **Fase 0 — Pre-Sales/Scoping** | Call di scoping, sopralluogo/analisi, documento di fattibilità | **GATE 1** — firma contratto | Acconto (es. 30%) |
| **Fase 1 — Concept & Kickoff** | Charter definitivo, kickoff cliente, concept, iterazioni (max N round) | **GATE 2** — approvazione concept | Milestone (es. 40%) |
| **Fase 2 — Sviluppo/Produzione** | Coordinamento fornitori/team, produzione, reporting periodico | **GATE 3** — pre-produzione chiusa | Nessun pagamento (GO esecutivo) |
| **Fase 3 — Rollout/Delivery** | Esecuzione, test, messa in produzione/consegna | **GATE 4** — chiusura formale | Saldo (es. 30%) |
| **Fase 4 — Verifica/Retrospettiva** | Raccolta dati, consuntivo vs preventivo, lessons learned | — | — |
| **Fase 5 — Upsell (opzionale)** | Servizi post-consegna a fee, terzo livello | — | Nuova proposta |

Il pattern a 5-6 fasi è un punto di partenza, non un dogma (vedi FPT sopra): il principio che non si tocca è "ogni fase finisce con un criterio di uscita verificabile e un approvatore nominato", non il numero di fasi.

## MODALITÀ LEAN (soglia concreta, non solo "proporzionato")
Per progetti sotto **~20 ore totali o ~€3.000** (tipico per un libero professionista o una PMI micro): salta il charter formale e le 5 fasi. Usa solo:
1. Una riga di scopo (2-3 frasi: cosa, per chi, entro quando)
2. Un solo gate: "cliente approva prima di fatturare il saldo"
3. Direttamente `kanban-checklist-quickref.md` per il tracciamento

Sopra questa soglia (o se il progetto ha più di 2 persone coinvolte, anche se il budget è piccolo), il charter completo e le fasi tornano a valere la pena: la ragione non è il valore assoluto del progetto, è il numero di persone che devono restare allineate senza doversi risentire ogni volta.

## GUIDING QUESTIONS (da fare prima di costruire il WBS)
- "Se dovessimo fermarci a metà, in quale punto perderemmo meno lavoro?" → lì probabilmente serve un gate
- "Chi approva l'uscita da questa fase — è la stessa persona che ha fatto il lavoro?" → se sì, il gate non ha valore di controllo reale
- "Questo gate sblocca un pagamento o solo un via libera tecnico?" → dichiaralo esplicitamente nel charter

## EXPECTED OUTPUT
1. Project Charter compilato — vedi `/knowledge_base/templates/project_charter_template.md` (o il foglio "Project Charter" in `project_wbs_kanban_template.xlsx`)
2. WBS a fasi con gate espliciti — vedi `/knowledge_base/templates/wbs_checklist_template.md` (o il foglio "WBS Checklist" in `project_wbs_kanban_template.xlsx`, con somme automatiche per fase)
3. Per ogni gate: criterio di uscita, approvatore, trigger commerciale (se presente)

## ERRORI COMUNI NELLE PMI
- Gate "silenziosi": si passa alla fase dopo senza che nessuno l'abbia formalmente approvata — il gate esiste solo se qualcuno lo attraversa consapevolmente
- Approvatore del gate = stesso esecutore della fase → non è un controllo, è un'autocertificazione
- Charter scritto e mai più consultato — se le sotto-attività non derivano dal charter, il charter è decorativo
- Troppe fasi per progetti piccoli — la disciplina del gate ha un costo di gestione, va proporzionato alla scala del progetto

## QUICK EXAMPLE (PMI italiana — agenzia di comunicazione eventi, progetto fiera di settore €12.000)
**Decisione**: come strutturare un progetto di partecipazione fieristica per un cliente manifatturiero?

**Fase 0** (scoping gratuito): call + sopralluogo → **GATE 1**: firma contratto → acconto 30% (€3.600).
**Fase 1** (kickoff + concept stand): charter definitivo, presentazione concept, 2 round di revisione max → **GATE 2**: cliente approva il concept → milestone 40% (€4.800).
**Fase 2** (produzione: fornitori allestimento, grafica, contenuti) → **GATE 3**: pre-produzione chiusa, tutto pronto per il giorno fiera (nessun pagamento, solo GO/NO-GO interno).
**Fase 3** (rollout: allestimento, presidio giornata fiera, disallestimento) → **GATE 4**: chiusura formale → saldo 30% (€3.600).
**Fase 4** (retrospettiva: contatti raccolti, consuntivo ore vs preventivo).

**GO/NO-GO su Gate 2**: se il cliente chiede più di 2 round di revisione sul concept, il progetto esce dallo scope firmato — si quota a parte, non si assorbe silenziosamente.

## QUICK EXAMPLE 2 — MODALITÀ LEAN (libero professionista solo, es. commercialista con sito personale, revisione sito web €1.200)
**Decisione**: un cliente chiede il refresh dei testi del proprio sito (5 pagine), consegna in 10 giorni, nessun team coinvolto oltre al professionista stesso.

Sotto soglia lean (€1.200, ~15 ore, 1 persona): niente charter, niente 5 fasi. Riga di scopo: "Refresh copy 5 pagine sito [cliente], consegna [data], approvazione cliente prima di fattura saldo." Un solo gate: "cliente approva i testi" → fattura a saldo. Il resto è direttamente checklist Kanban (`kanban-checklist-quickref.md`): 5 righe, una per pagina.

**GO/NO-GO**: se durante il lavoro emerge che il cliente vuole anche restyling grafico (non solo testi), si esce dalla modalità lean — il progetto cambia scala e vale la pena riaprire un charter minimo con un gate in più.

## CROSS-REFERENCE
- `raci-quickref.md` — per assegnare Accountable/Responsible a ogni sotto-attività del WBS
- `kanban-checklist-quickref.md` — per il tracciamento operativo giorno-per-giorno dentro ogni fase
- `/knowledge_base/templates/project_charter_template.md` — template .md compilabile (agente)
- `/knowledge_base/templates/wbs_checklist_template.md` — template .md compilabile (agente)
- `/knowledge_base/templates/project_wbs_kanban_template.xlsx` — stesso contenuto in Excel con formule live (somma ore per fase/totale, calcolo costo, menu a tendina, colori Kanban) — per l'uso diretto di Sara
- `director/SKILL.md` — agente TTP che applica questo framework per ogni nuovo progetto multi-agente
- `architect/SKILL.md` — usa il project charter come input per la proposta commerciale
