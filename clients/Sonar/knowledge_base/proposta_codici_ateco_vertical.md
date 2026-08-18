# SONAR — Proposta codici ATECO per il vertical pilota "Manifattura/produzione B2B"
### Proposta di Orchestrator, da validare con Sara | 2026-08-18

Il documento di progetto (par. 2.2, `Config_ICP`) definisce il settore solo a livello descrittivo ("Manifattura e servizi B2B; produzione B2B...") con fonte "Codice ATECO con verifica sul sito" — cioè i codici precisi non sono mai stati fissati. Questa proposta li ricava incrociando due cose: la classificazione ATECO 2025 (attuale, in vigore dal 1 aprile 2025 — non la 2007) e la composizione reale del portafoglio storico ATMAN appena arricchito (`Portafoglio_Clienti_ATMAN`), che nel vertical scelto mostra due sotto-cluster distinti.

**Non ancora scritta in `Config_ICP`** — è una proposta. Va confermata/corretta da Sara prima di essere usata per il sourcing e prima di modificare il foglio Config (per policy del progetto, i fogli Config_* si toccano solo su richiesta esplicita).

## Sotto-cluster A — Moda / Tessile / Calzature / Pelletteria
Il cluster più rappresentato nel portafoglio (15+ clienti: Rossimoda, Golden Goose, René Caovilla, Loro Piana, Missoni, Lanificio Bottoli, Calzaturificio Maretto, Maglificio Venezia, Fashionart, Atelier Stimamiglio, HIM CO, Costificatore...).

| Codice ATECO 2025 | Descrizione |
|---|---|
| 13.10 | Preparazione e filatura di fibre tessili |
| 13.20 | Tessitura |
| 13.92 | Confezionamento di articoli tessili (esclusi indumenti) |
| 13.99 | Fabbricazione di altri prodotti tessili n.c.a. (pizzi, nastri, ricami) |
| 14.13 | Confezione in serie / su misura di abbigliamento esterno |
| 14.14 | Confezione di camicie, T-shirt, corsetteria e biancheria intima |
| 14.19 | Confezione di altri articoli di abbigliamento e accessori |
| 14.31 | Fabbricazione di articoli di calzetteria in maglia |
| 14.39 | Fabbricazione di pullover, cardigan e altri articoli a maglia |
| 15.12 | Fabbricazione di articoli da viaggio, borse, pelletteria, selleria |
| 15.20 | Fabbricazione di calzature |

## Sotto-cluster B — Meccanica leggera / Elettronica / Impiantistica
Presente nel portafoglio in forma minoritaria ma reale (Axo Light, Equadro, CignoClima, Lux23, Qascom).

| Codice ATECO 2025 | Descrizione |
|---|---|
| 26.12 | Fabbricazione di schede elettroniche assemblate |
| 26.70 | Fabbricazione di strumenti ottici e attrezzature fotografiche |
| 27.40 | Fabbricazione di apparecchiature per illuminazione |
| 28.25 | Fabbricazione di apparecchiature per la refrigerazione e la ventilazione non domestiche |

## Decisione di Sara (18/08/2026)
**Entrambi i sotto-cluster (A + B) inclusi** per il primo test di estrazione, non solo A come inizialmente suggerito.

**Ancora da confermare:** questi codici sono corretti/sufficienti così come proposti, o Sara vuole aggiungerne/toglierne? Una volta confermati definitivamente, vanno scritti in `Config_ICP` (colonna Settore) come riferimento operativo per il sourcing.
