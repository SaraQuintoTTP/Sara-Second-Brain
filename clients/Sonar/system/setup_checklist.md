# SONAR — Checklist di avvio Sprint 0
### Fonte: Allegato A del documento di progetto v3.2 | Stato aggiornato: 2026-08-17

Colonna **Stato**: `Da fare` / `In corso` / `Fatto` / `Non applicabile (motivare)`
Colonna **Risposta/Nota**: quello che Sara ha deciso o fornito, con data.

| # | Voce | Responsabile (da doc.) | Stato | Risposta/Nota |
|---|---|---|---|---|
| 1 | Elenco storico dei clienti consolidato: ragione sociale, partita IVA, settore, referenti, periodo | Commerciale + Direzione | In corso — arricchimento completato, in attesa di conferma Sara | 2026-08-18 — importato l'export Ruko "Clienti ATMAN attivi.xlsx" (74 clienti) nel foglio `Portafoglio_Clienti_ATMAN`. Arricchimento con ricerca online (partita IVA da registri camerali pubblici, settore dedotto da nome/sito/progetti, referente dove reperibile con sicurezza). Copertura finale: ragione sociale 74/74, periodo 74/74, **partita IVA 43/74, settore 64/74, referenti 10/74** (i referenti mancano quasi sempre per SRL/SPA — il legale rappresentante non è pubblico gratuitamente; presente solo per ditte individuali). Per ~8 aziende esistono più omonimi e la P.IVA trovata è stata scartata per sede incoerente col Nord-Est (segnalato in `note` per verifica manuale). Non segnato "Fatto": copertura parziale, richiede revisione a campione di Sara prima di considerarlo definitivo |
| 2 | Rubrica della rete professionale ATMAN ed elenco dei segnalatori attivi disponibili | Direzione + Commerciale | In corso — 3 segnalatori registrati | 2026-08-18 — Sara ha fornito 3 nominativi: Fabio Righetto (Account Manager, Zucchetti S.p.A., Padova/Triveneto — verificato online), Alessandro Murador (Rappresentante vendita, Rapax Mangimi, area Favaro Veneto — identità confermata da Sara dopo omonimia ambigua), Valeria Apolloni (Account Manager ATMAN, ex cliente — chiarito che non è omonimia: stessa persona transitata da cliente a interno, utilizzabile come segnalatore). Strutturati nel foglio `Rete_Professionale_Segnalatori` del workbook. Manca ancora: l'elenco completo di direzione (rubrica rete professionale + altri segnalatori attivi) |
| 3 | Standard minimo dell'Audit Light sulle tre aree definito: contenuto, durata, deliverable, responsabile di erogazione | Direzione + area tecnica | **Fatto** | 2026-08-18 — Fonti: "Presentazione Segnalatori.pdf" (contenuto/flusso) + risposta diretta di Sara (durata/deliverable/responsabili), estratto completo in `knowledge_base/programma_segnalatori.md`. **Contenuto:** check-up gratuito + diagnosi stato attuale + proposta soluzione, su una delle 3 aree (Tecnologia/Marketing & Comunicazione/Processi Aziendali). **Durata:** 4 ore standard. **Deliverable:** PDF + presentazione PPT, in incontro ad hoc (nota di Sara: l'Audit Light è soprattutto lo strumento per vendere il servizio successivo, non solo consegna tecnica). **Responsabili:** commerciale sempre Emanuele Turcato; tecnico per area — Tecnologia: Carloalberto Fornea, Marketing & Comunicazione: Greta Moschetta, Processi Aziendali: Sara Quinto |
| 4 | Vertical del pilota scelto e priorità delle province confermata (par. 2.2) | Direzione | **Fatto** | 2026-08-18 — Vertical scelto: **Manifattura/produzione B2B** (moda, tessile, calzature, industria) — cluster più ampio nel portafoglio storico ATMAN (15+ clienti su 74, es. Rossimoda, Golden Goose, Loro Piana, Missoni, Lanificio Bottoli, Calzaturificio Maretto). Priorità province **confermata come da documento**: P1 Padova/Venezia/Treviso/Vicenza → P2 Verona/Rovigo/Belluno → P3 FVG |
| 5 | Workshop di definizione dei pesi calendarizzato (2 ore) | Conduzione | **Fatto** (non applicabile — pesi confermati senza workshop) | 2026-08-18 — Sara conferma di usare i pesi di default già trascritti dal documento nel workbook (`Config_Pesi_FIT`, `Config_Pesi_TIMING`), senza workshop dedicato di 2 ore |
| 6 | Otto giornate commerciali allocate e protette | Direzione | **Fatto** | 2026-08-18 — Sara conferma: le 8 giornate commerciali sono già allocate e protette in agenda per il pilota |
| 7 | Filone di attività sospeso per liberare capacità, individuato | Direzione | **Fatto** (non applicabile) | 2026-08-18 — Sara conferma: la capacità per il pilota c'è già, non è necessario sospendere alcun filone di attività |
| 8 | Foglio di lavoro predisposto secondo lo schema del par. 4.3 | Conduzione | **Fatto** | 2026-08-17 — sostituito da `sonar_registry.xlsx`, schema Allegato B implementato in pieno (vedi `system/data/`) |
| 9 | Responsabile della conformità individuato (al più tardi prima dello Sprint 1) | Direzione | **Fatto** | 2026-08-18 — Sara conferma: Massimiliano Losego, titolare ATMAN |
| 10 | Repository documentale creato con accessi definiti | Conduzione | **Fatto** (parziale) | 2026-08-17 — repository creato in `clients/Sonar/`. Accessi: da definire se ATMAN deve poter accedere direttamente o solo tramite Sara |
| 11 | Soglie dei tre gate approvate e verbalizzate | Direzione + Conduzione | **Fatto** | 2026-08-18 — Sara conferma le soglie del documento (cap. 13) come definitive, senza modifiche: Gate 1 (31/10/2026) ≥20 conversazioni/100, ≥5 appuntamenti, 2 preventivi; Gate 2 (31/01/2027) costo/appuntamento < baseline, ≥8 appuntamenti tenuti, ≥1 contratto, esiti compilati ≥80%; Gate 3 (31/07/2027) economics positiva 2 trimestri, ≥4 ricorsivi, ciclo completo senza conduzione, precisione punteggio > riserva di confronto |

---

## Le tre condizioni di avvio vere e proprie (par. 2.4)

Il documento è esplicito: questi tre input sono **condizione di avvio dello Sprint 0**, non solo elementi utili — senza, non si parte:

1. Elenco storico completo dei clienti gestiti (voce 1 sopra)
2. Elenco della rete professionale ATMAN e dei segnalatori attivi (voce 2 sopra)
3. Standard minimo dell'Audit Light sulle tre aree (voce 3 sopra)

**Stato al 18/08/2026: 1 su 3 condizioni soddisfatta** (voce 3, Standard Audit Light). Voce 1 (elenco clienti) e voce 2 (rete professionale/segnalatori) sono in corso ma parziali — mancano rispettivamente la revisione a campione dei dati arricchiti e l'elenco completo lato direzione ATMAN. Restano la priorità del percorso guidato (skill `sonar-setup`).
