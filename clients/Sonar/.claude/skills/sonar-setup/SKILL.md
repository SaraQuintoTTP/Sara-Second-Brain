---
name: sonar-setup
description: Use when setting up, resuming, or checking progress on the SONAR Sprint 0 onboarding for ATMAN (Sara's client project). Trigger on "Sonar", "riprendi Sonar", "checklist Sprint 0", "Allegato A", or when Sara wants to provide inputs the system is waiting on (elenco clienti, rete professionale ATMAN, segnalatori, standard Audit Light, vertical, pesi). This is the guided step-by-step wizard — use sonar-pipeline instead once Sprint 0's three condizioni di avvio are done and real company data is being worked.
---

# SONAR — Wizard di avvio guidato

Guida Sara, un passo alla volta, attraverso la checklist di Sprint 0 del progetto SONAR (motore commerciale di ATMAN). Non è un generatore di documenti: è un percorso decisionale — ogni passo richiede una risposta reale da Sara, non solo un "ok, andiamo avanti".

## Prima di rispondere a qualunque cosa

Leggi in quest'ordine:
1. `clients/Sonar/system/setup_checklist.md` — qual è lo stato di ogni voce
2. `clients/Sonar/system/automation_readiness.md` — modalità attuale di ciascun componente
3. `clients/Sonar/knowledge_base/SONAR_context.md` — se serve richiamare una regola del documento originale (soglie, pesi, definizioni)

Non rileggere il PDF di 34 pagine: la sintesi in `SONAR_context.md` basta per il 95% dei casi. Torna al PDF originale solo se la sintesi non copre il dettaglio che serve.

## Regola operativa: un passo alla volta

Non elencare mai tutti gli 11 punti della checklist insieme e non chiedere più di una decisione reale per turno. Segui questo ordine di priorità:

1. **Le tre condizioni di avvio (par. 2.4, righe 1-3 della checklist)** — bloccano tutto il resto, vanno chiuse per prime:
   - Elenco storico clienti (ragione sociale, P.IVA, settore, referenti, periodo)
   - Rubrica rete professionale ATMAN + elenco segnalatori attivi
   - Standard minimo Audit Light per le tre aree (contenuto, durata, deliverable, responsabile erogazione)
2. Vertical del pilota e priorità province (riga 4) — sblocca il perimetro di sourcing
3. Workshop pesi (riga 5) — se Sara vuole discostarsi dai pesi di default del documento (già caricati in `Config_Pesi_FIT`/`Config_Pesi_TIMING`), altrimenti si può confermare "usiamo i pesi del documento" e passare oltre
4. Capacità (righe 6-7): giornate commerciali allocate, filone sospeso
5. Responsabile conformità (riga 9)
6. Verbalizzazione soglie gate (riga 11) — già scritte nel documento, serve solo conferma

Per ogni voce:
- Se è una scelta fra opzioni chiuse (es. vertical da scegliere fra i settori ICP, priorità provincia) → usa **AskUserQuestion**
- Se è dato grezzo da acquisire (elenco clienti, rubrica rete professionale) → chiedi a Sara come vuole fornirlo (incollare qui, file da leggere, foglio già esistente da importare) e poi procedi tu a strutturarlo nel workbook
- Non passare alla voce successiva finché quella corrente non è "Fatto" o esplicitamente rimandata da Sara con un motivo (in tal caso segna "Non applicabile" con la nota del motivo, non lasciarla ambigua)

Dopo ogni risposta:
1. Aggiorna la riga corrispondente in `setup_checklist.md` (Stato + Risposta/Nota con data)
2. Se il dato alimenta il registro (es. elenco clienti → futuri candidati Ponte "portafoglio_clienti"; rete professionale/segnalatori → idem), scrivilo nel workbook usando `system/scripts/registry_io.py` (mai a mano, mai posizionale — vedi l'esempio nel file)
3. Di' in una riga cosa hai appena chiuso e qual è il prossimo passo — non fare un resoconto lungo ad ogni micro-passo

## Quando le tre condizioni di avvio sono chiuse

Proponi esplicitamente a Sara di passare alla skill `sonar-pipeline` per iniziare il sourcing reale (C1) sul perimetro/vertical scelto. Non iniziare a caricare aziende vere di tua iniziativa dentro questo skill: è il confine fra "setup" e "pipeline operativa".

## Aggiornare il ledger di automazione

Ogni volta che raccogli evidenza rilevante per una soglia descritta in `automation_readiness.md` (es. hai validato 100 record senza errori di classificazione), non cambiare la modalità da solo: proponilo a Sara con il numero che hai osservato, e solo dopo la sua conferma aggiungi la riga al log delle decisioni in quel file.

## Cosa NON fare

- Non inventare dati mancanti (elenco clienti, pesi, soglie di capacità) per "andare avanti più veloce": sono decisioni reali di Sara/ATMAN
- Non modificare i fogli `Config_*` del workbook senza che Sara l'abbia esplicitamente chiesto o confermato — sono trascritti 1:1 dal documento di progetto
- Non proporre di installare tool esterni (n8n, SaaS, ecc.): il sistema gira interamente dentro Claude Code — Python, il workbook Excel, e Claude stesso per le parti agentiche. Se serve davvero una skill Claude Code aggiuntiva (es. per una fonte dati specifica), proponila esplicitamente a Sara e attendi la sua validazione prima di usarla
