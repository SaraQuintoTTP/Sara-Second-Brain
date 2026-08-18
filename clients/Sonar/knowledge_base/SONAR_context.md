# SONAR — Sintesi del documento di progetto v3.2
### Fonte: SONAR_Documento_di_Progetto_v3.2.1.pdf (34 pag., 14 ago 2026) | Sintesi: 2026-08-17

---

## 1. Obiettivo e perimetro
Sistema di ascolto del mercato per l'acquisizione di clienti nuovi ATMAN (agenzia digitale PMI Nord-Est). Output in ordine di priorità: (1) coda settimanale max 25 aziende + mensile max 100, con motivazione documentata; (2) percorso di presentazione via rete relazionale (ponte) dove esiste; (3) registro esiti per ritarare i criteri nel tempo.

**Dentro il perimetro:** acquisizione nuovi clienti, sourcing/qualificazione/mappatura relazionale/preparazione al contatto, definizione criteri, documentazione, Fase 1 manuale/semi-automatica.
**Fuori dal perimetro:** gestione portafoglio esistente, trattativa/chiusura (resta all'area commerciale), sostituzione CRM (Ruko resta il sistema), **sviluppo agenti autonomi (rinviato a Fase 2)**, commercializzazione a terzi (Fase 3).

## 2. ICP e Anti-ICP
- **Geografia:** Veneto (P1: Padova/Venezia/Treviso/Vicenza; P2: Verona/Rovigo/Belluno; P3: FVG)
- **Dimensione:** fatturato €500K–20M, addetti 10–50
- **Settore:** manifattura/servizi B2B, studi professionali, medicale/odontoiatrico, food/commercio locale, pet
- **Anti-ICP (esclusione se ≥2 regole attivate, quarantena umana se 1):** sotto soglia fatturato, marketing/IT interna strutturata, contratto manutenzione attivo recente, cliente ATMAN attivo, conflitto interesse, opposizione registrata (blocco tecnico, non annotazione)

## 3. Catalogo offerta
**3 aree di intervento:** Tecnologia, Marketing e comunicazione, Processi aziendali.
**4 livelli:** Frontend (Contatto diretto / Audit Light gratuito / Audit Completo 500-1000€ scomputabile — unico livello proponibile al primo contatto) → Core (progetto, 1-3 mesi) → Ricorsivo (contratti, obiettivo economico primario) → Accessori (coltivazione coda C).
Tabella segnale→area→frontend→core→ricorsivo atteso è al par. 2.3.5 del documento originale.

## 4. Architettura: 7 componenti (C0-C6)
| # | Componente | Risponde a | Output | Automazione Fase 1 |
|---|---|---|---|---|
| C0 | Governance dati | Base giuridica, conservazione | Registro fonti, blocchi | Regole scritte, controllo manuale |
| C1 | Sourcing | Quali aziende esistono nel perimetro | Anagrafica dedup | Manuale → semi-automatico |
| C2 | Contatti | Chi decide, come si raggiunge | Contatti classificati L0-L4 | Manuale → semi-automatico |
| C3 | Ponte | Chi in rete ATMAN può presentarci | Mappa collegamenti + forza | Manuale, incroci societari automatizzati Sprint 1 |
| C4 | Segnali | FIT (quanto in target) + TIMING (quanto è il momento) | Punteggi + motivazione | Manuale → semi-automatico |
| C5 | Attivazione | Cosa dire, su che canale | Coda, One Pager, appuntamento | Bozza generata, revisione/invio umani |
| C6 | Esiti | Cosa ha funzionato | Registro etichettato, pesi ritarati | Manuale → semi-automatico |

Flusso lineare C1→C2→C3→C4→C5→C6, con retroazione di C6 sui pesi di C4.

## 5. Punteggi (cap. 7)
- **FIT** (0-100, somma pesata, 6 famiglie di segnali S1-S6, varia in mesi, ricalcolo mensile)
- **TIMING** (0-100, con finestre di decadimento per segnale — pieno entro la finestra, metà fino al doppio, zero oltre; ricalcolo settimanale sul bacino ad alto FIT)
- **PONTE** (0-100, max fra i collegamenti rilevati; cumulativo, non decade)
- **Instradamento code:** A = ponte≥50 & FIT≥60 (presentazione, no freddo); B = FIT≥60 & TIMING≥60 & ponte<50 (contatto diretto); C = FIT≥60 & TIMING<60 (coltivazione, no proposta); D = FIT 30-59 lavorabile solo con ponte≥60; Fuori = FIT<30 o anti-ICP o opposizione.
- Pesi iniziali da ricostruzione a ritroso di 20 clienti recenti. Ritaratura richiede: etichette esito, volume minimo, riserva di confronto (10-15% random fuori ordinamento).

## 6. Il Ponte (C3) — elemento distintivo
3 sorgenti da tenere distinte: portafoglio clienti (forza 100 se persona transitata), rete professionale ATMAN (commercialista/avvocato/consulenti/fornitori, forza 70), programma segnalatori (accordo con ritorno previsto, forza 90). Regola chiave: la richiesta di presentazione la fa sempre chi detiene la relazione, non chi lavora il prospect; un ponte si usa una sola volta per azienda.

## 7. Stack tecnologico dichiarato per la Fase 1 (cap. 11)
Foglio strutturato (Sprint 0) → Ruko esteso con campi punteggio/ponte (Sprint 1+). Fonti camerali/open data per anagrafica. Script interno per analisi tecnica domini. Foglio di calcolo/script per punteggi. Modelli manuali + assistenza automatica con **revisione umana obbligatoria prima di ogni invio**.

## 8. Roadmap e gate
| Sprint | Periodo | Bacino | Automazione | Gate |
|---|---|---|---|---|
| 0 — pilota manuale | set-ott 2026 | 100 aziende (40 vertical + 60 generalista, 12 riserva) | Nessuna | 31 ott 2026 |
| 1 — semi-automazione | nov 2026-gen 2027 | 400-600 aziende | Raccolta e segnali automatizzati, giudizio umano | 31 gen 2027 |
| 2 — industrializzazione | da feb 2027 | secondo dimensionamento universo | Ciclo chiuso, sequenze parzialmente automatiche | 31 lug 2027 |

Gate 1 GO: ≥20 conversazioni/100, ≥5 appuntamenti, 2 preventivi. Gate 2 GO: costo/appuntamento < baseline, ≥8 appuntamenti tenuti, ≥1 contratto, esiti compilati ≥80%. Gate 3 GO: economics positiva 2 trimestri, ≥4 ricorsivi, un ciclo completo senza conduzione, precisione punteggio > riserva di confronto.

## 9. Fase 2 — evoluzione agentica (cap. 15, fuori perimetro del documento)
| Componente | Fase 1 | Fase 2 |
|---|---|---|
| Sourcing | Interrogazioni periodiche su fonti definite | Esplorazione autonoma nuove fonti + proposta ampliamento |
| Segnali | Elenco chiuso a priori | Proposta nuovi segnali predittivi, validazione umana |
| Punteggi | Pesi fissi, ritaratura manuale | Ritaratura continua entro vincoli/soglie di controllo |
| Ponte | Incroci manuali/semi-automatici | Aggiornamento continuo mappa + proposta percorsi |
| Attivazione | Bozze assistite, invio umano | Generazione/instradamento estesi a tutta la sequenza, **approvazione umana obbligatoria** |

**6 prerequisiti espliciti per la Fase 2:** (1) registro esiti etichettati di volume sufficiente, (2) definizione stabile di cliente di valore, (3) processo manuale documentato e funzionante (capitolato), (4) soglie di controllo con arresto automatico, (5) quadro di conformità completo, (6) esito GO al Gate 2.

## 10. Input mancanti (par. 2.4) — non prodotti dal progetto, servono comunque
Elenco storico clienti; rubrica rete professionale + segnalatori; standard Audit Light per area; indice tipo Audit Completo; capacità di erogazione mensile; regole di scomputo; listino ricorsivi; marginalità reale; valore giornata commerciale/tecnica; stato anagrafiche Ruko; esiti campagne a pagamento.
