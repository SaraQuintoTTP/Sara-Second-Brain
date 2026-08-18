# SONAR — Ledger di maturità dell'automazione
### Ultimo aggiornamento: 2026-08-17 | Orchestrator

Traccia, per ciascuno dei 7 componenti del sistema (C0-C6), la modalità operativa attuale e la soglia oggettiva che deve essere raggiunta prima di passare al livello successivo. Le soglie sono coerenti con i Gate e i prerequisiti già fissati nel documento di progetto v3.2 (cap. 9, 13, 15) — non ne sono state inventate di nuove.

**Regola di fondo:** nessun componente passa di modalità per decisione unilaterale del sistema. Ogni passaggio è una riga di questa tabella proposta da Claude e confermata da Sara, con data.

---

## Le tre modalità

| Modalità | Cosa significa |
|---|---|
| **Guidato** | Claude prepara/propone (ricerca, calcolo, bozza), ma **ogni singolo output** passa da conferma esplicita di Sara prima di essere scritto nel registro o usato |
| **Semi-automatico** | Claude esegue ed scrive direttamente nel workbook secondo le regole concordate; Sara rivede a campione o in retrospettiva periodica, non riga per riga |
| **Automatico** | Gira secondo cadenza propria (cap. 4.4 / 9.3) senza revisione preventiva, salvo eccezioni esplicitamente segnalate (es. anti-ICP in quarantena) |

Due componenti hanno un tetto strutturale che il documento pone indipendentemente dai dati raccolti (non è un gate che si "supera": è un vincolo permanente):
- **C5 — invio del primo contatto**: resta umano per sempre (cap. 8.2, cap. 15 tabella Attivazione: "approvazione umana obbligatoria" anche nella visione di Fase 2 matura)
- **C6 — modifica dei pesi**: resta umana in Fase 1 (par. 7.5); dopo il GO al Gate 2 può diventare "proposta con soglie di controllo pre-approvate", mai libera

---

## Stato per componente

| # | Componente | Modalità attuale | Criterio oggettivo di passaggio | Evidenza raccolta finora |
|---|---|---|---|---|
| C0 | Governance dati | Guidato | Regole scritte + blocco tecnico automatico da subito (non richiede dati); il giudizio umano su casi ambigui si riduce quando <1 caso ambiguo ogni 50 record per 4 settimane consecutive | 0 record trattati |
| C1 | Sourcing | Guidato | → Semi-automatico dopo 100 record (Sprint 0) con errore di classificazione ATECO/area sotto il 5% verificato a campione | 2 record (primo test 18/08/2026, Kompass EasyBusiness — vedi `projects/sistema_agentico/findings/test_sourcing_kompass_18-08.md`). 1 record su 3 estratti scartato per errore di classificazione (33%, sopra soglia 5%) — campione troppo piccolo per essere significativo, ma segnala il rischio |
| C2 | Contatti | Guidato | → Semi-automatico quando il tasso di contatti errati (L2/L3 non validi) su un campione verificato a mano è sotto il 10% | 0 contatti |
| C3 | Ponte — match societario | Guidato | → Automatico appena l'incrocio soci/amministratori è scriptato e testato su un campione (previsto da Sprint 1 nel documento) | Non ancora scriptato. Test 18/08/2026 su 2 aziende reali: amministratori non reperibili gratuitamente online (dietro visura a pagamento) — probabile che l'automazione richieda comunque una fonte a pagamento (Telemaco/visura), non solo script |
| C3 | Ponte — match assistito (rete professionale, segnalatori, storie personali) | Guidato | Non passa mai oltre "Guidato con proposta assistita": la fonte primaria è la memoria del team, non automatizzabile. Claude può solo strutturare la domanda periodica e raccogliere risposte | Test 18/08/2026 (vedi `test_sourcing_kompass_18-08.md`): verificate le 3 fonti su 2 aziende reali, 0 Ponti trovati — perimetro di rete ATMAN attuale (74 clienti + 3 segnalatori) ancora troppo stretto rispetto al vertical moda/pelletteria. Rafforza la priorità di completare la checklist voce 2 (rete professionale) |
| C4 | Segnali — scoring (FIT/TIMING/PONTE, motore deterministico) | **Automatico** | Già testato end-to-end (2026-08-17, 3 record sintetici, 3/3 corretti) — nessun gate ulteriore: è aritmetica, non richiede giudizio | Test di validazione superato |
| C4 | Segnali — scanner (raccolta da fonti non strutturate: annunci, fiere, news) | Guidato | → Semi-automatico quando il tasso di falsi positivi su un campione verificato è sotto il 15%, concordato con Sara | 2 aziende reali verificate (18/08/2026, vedi `test_sourcing_kompass_18-08.md`): **0 segnali TIMING validi trovati su entrambe**. Non per assenza di ricerca: trovati 2 eventi reali per Audes Group (cambio sede, lancio prodotto Clolife) ma entrambi fuori dalla finestra di validità di 180 giorni. Prima evidenza concreta che la raccolta segnali richiede ricerca mirata per azienda ed è normale un esito "nessun segnale" — utile per calibrare le aspettative sul volume di lavoro umano/agentico di questo componente |
| C5 | Attivazione — bozze (One Pager, script) | Guidato | → Semi-automatico quando le bozze superano la revisione senza correzioni sostanziali per 3 cicli settimanali consecutivi | 0 bozze prodotte |
| C5 | Attivazione — invio | **Sempre Guidato/umano** | Nessun passaggio previsto. Vincolo permanente del documento | — |
| C6 | Esiti — sincronizzazione registro | Guidato (in attesa di collegamento Ruko) | → Automatico appena definito il canale di lettura degli esiti da Ruko (Input mancante, par. 2.4) | 0 esiti |
| C6 | Esiti — ritaratura pesi | **Sempre umana in Fase 1** | Diventa "proposta con soglie di controllo" solo dopo GO Gate 2 (31 gen 2027) e i 6 prerequisiti di Fase 2 (cap. 15) | — |

---

## Log delle decisioni

| Data | Decisione | Con chi |
|---|---|---|
| 2026-08-17 | Creato il sistema operativo (workbook `sonar_registry.xlsx`, motore `sonar_engine.py`, questo ledger). Nessun dato reale ancora caricato — tutti i componenti in modalità Guidato salvo il motore di scoring, testato e già affidabile per costruzione (è codice deterministico, non un modello). | Sara + Orchestrator |

*Ogni volta che un componente cambia modalità, si aggiunge una riga qui con data, cosa è cambiato, evidenza a supporto e conferma di Sara.*
