# SONAR — Client/Project Brief
### Created: 2026-08-17 | Orchestrator

---

## COS'È
SONAR non è un cliente TTP in senso classico: è il documento di progetto (v3.2, 14 agosto 2026, autrice Sara Quinto) che descrive il motore di sourcing, qualificazione e attivazione della pipeline commerciale di **ATMAN**, agenzia digitale per PMI del Nord-Est.

La cartella è stata creata su richiesta di Sara per ospitare l'analisi del documento e la proposta di architettura agentica che ne implementa la logica.

## OGGETTO DEL PROGETTO SONAR (dal documento originale)
Sistema che identifica, ordina e prepara alla lavorazione commerciale le aziende nel perimetro ICP di ATMAN con la maggiore probabilità di aprire una conversazione di acquisto. Output: coda settimanale (max 25 aziende) e mensile (max 100), mappa dei ponti relazionali, registro degli esiti.

**Indicatore di riferimento:** appuntamenti commerciali qualificati fissati e tenuti.

## STATO DICHIARATO NEL DOCUMENTO
- **Fase 1 (in corso/pianificata):** processo manuale → semi-automatico. Sprint 0 (set-ott 2026) → Sprint 1 (nov 2026-gen 2027) → Sprint 2 (da feb 2027).
- **Sviluppo di agenti autonomi:** esplicitamente **fuori perimetro** del documento, rinviato alla "Fase 2" — descritta solo come orizzonte (cap. 15), condizionata al GO del Gate 2 (31 gen 2027) e a 6 prerequisiti espliciti.

## RICHIESTA DI SARA (17 agosto 2026)
Analizzare il documento di progetto e proporre come costruire concretamente un sistema agentico che replichi quanto descritto — cioè disegnare in anticipo l'architettura della "Fase 2", pur senza saltare i prerequisiti che il documento stesso pone.

## FILE DI QUESTA CARTELLA
| File | Contenuto |
|---|---|
| `knowledge_base/SONAR_context.md` | Sintesi strutturata del documento di progetto (34 pagine) per riferimento rapido nelle sessioni future |
| `knowledge_base/programma_segnalatori.md` | Estratto dal materiale commerciale "Presentazione Segnalatori.pdf": le 3 aree, flusso Audit Light/Completo, listino, contatti — cornice commerciale del programma partner, non lo standard tecnico dell'Audit Light |
| `knowledge_base/proposta_codici_ateco_vertical.md` | Proposta codici ATECO 2025 per il vertical pilota (moda/tessile/calzature + meccanica/elettronica leggera), da confermare definitivamente prima di scrivere in `Config_ICP` |
| `knowledge_base/fonti_sourcing_aziende.md` | Confronto di 9 fonti/sistemi per il sourcing (C1): Telemaco, Atoka, Kompass, Cribis, Apollo.io, Google Maps, Europages, Sistema Moda Italia, LinkedIn Sales Navigator — con raccomandazione (Telemaco + Atoka + Kompass incrociati) |
| `projects/sistema_agentico/findings/test_sourcing_kompass_18-08.md` | Primo test reale di sourcing (C1) su Kompass EasyBusiness: filtri usati, universo (2.432 aziende), 2 aziende inserite in `Aziende` (una pulita, una con rischio anti-ICP da verificare), 1 esclusa per rumore di classificazione |
| `projects/sistema_agentico/findings/proposta_architettura_agentica.md` | Proposta di architettura del sistema agentico: mappatura componenti → agenti, stack, guardrail, roadmap |

## SISTEMA OPERATIVO (costruito il 17/08/2026 — niente Airtable/n8n, tutto gestito da Claude Code)
| File | Contenuto |
|---|---|
| `system/data/sonar_registry.xlsx` | Datastore: workbook Excel con schema Allegato B (Aziende, Contatti, Ponti, Segnali, Esiti) + fogli di configurazione trascritti dal documento (pesi FIT/TIMING, soglie instradamento, ICP, anti-ICP, tipologie ponte, mappa segnale→prodotto) + `Portafoglio_Clienti_ATMAN` (foglio di supporto, fuori schema Allegato B: 74 clienti storici da export Ruko, usato per match Ponte "portafoglio_clienti" e anti-ICP "cliente ATMAN attivo") + `Rete_Professionale_Segnalatori` (foglio di supporto: elenco segnalatori attivi, 2 registrati finora) |
| `system/scripts/build_workbook.py` | Genera/inizializza il workbook |
| `system/scripts/sonar_engine.py` | Motore deterministico: `score` (calcola FIT/TIMING/PONTE e instrada in coda A/B/C/D), `queue` (esporta la coda settimanale rispettando il tetto), `check` (validazione coerenza dati). Testato end-to-end il 17/08/2026 |
| `system/scripts/registry_io.py` | Utility per leggere/scrivere righe nel workbook per nome di campo (mai posizionale) — usata da Claude durante il lavoro sulla pipeline |
| `system/automation_readiness.md` | Ledger di maturità: modalità attuale (Guidato/Semi-automatico/Automatico) di ciascun componente C0-C6, soglie oggettive di passaggio, log delle decisioni |
| `system/setup_checklist.md` | Checklist di avvio Sprint 0 (Allegato A del documento), con stato di avanzamento |
| `.claude/skills/sonar-setup/SKILL.md` | Skill Claude Code: wizard guidato per completare la checklist di avvio, un passo alla volta |
| `.claude/skills/sonar-pipeline/SKILL.md` | Skill Claude Code: esecuzione operativa C1-C6 (sourcing, contatti, ponte, segnali, attivazione, esiti) una volta che Sprint 0 è avviato |

**Stato al 18/08/2026:** infrastruttura pronta. Primo dato reale importato e arricchito: 74 clienti storici ATMAN (export Ruko) nel foglio `Portafoglio_Clienti_ATMAN` del workbook, con partita IVA/settore/referente completati via ricerca online dove reperibili con sicurezza (copertura: P.IVA 43/74, settore 64/74, referenti 10/74 — in attesa di revisione a campione di Sara). Registrati anche i primi 2 segnalatori attivi (Fabio Righetto, Alessandro Murador) nel foglio `Rete_Professionale_Segnalatori`. Delle tre condizioni di avvio dello Sprint 0 (par. 2.4), nessuna è ancora "Fatto": l'elenco clienti e i segnalatori sono in corso (parziali), lo standard Audit Light resta da fornire.

## FILE SORGENTE
`C:\Users\saraq\Desktop\Claude code\Progetti lavoro Sara\ATMAN - Progetto\ATMAN - Riempimento pipeline - SONAR\SONAR_Documento_di_Progetto_v3.2.1.pdf`
