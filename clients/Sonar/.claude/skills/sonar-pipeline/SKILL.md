---
name: sonar-pipeline
description: Use when running or resuming day-to-day SONAR work for ATMAN once Sprint 0 setup is underway — sourcing new companies (C1), enriching contacts (C2), mapping bridges/ponti (C3), scanning and scoring signals (C4), building the weekly queue and drafting outreach material (C5), or logging outcomes (C6). Trigger on "aggiorna Sonar", "cerca aziende Sonar", "calcola i punteggi", "genera la coda della settimana", "prepara il One Pager per [azienda]", "registra l'esito di [azienda]". Do not use for initial setup decisions still pending in setup_checklist.md — use sonar-setup for that.
---

# SONAR — Pipeline operativa (C1-C6)

Esegue il ciclo del sistema SONAR per ATMAN. Ogni componente ha una modalità (Guidato / Semi-automatico / Automatico) registrata in `clients/Sonar/system/automation_readiness.md`: **controllala sempre prima di agire** su quel componente, perché determina se puoi scrivere direttamente nel registro o devi prima mostrare a Sara cosa stai per registrare.

Riferimento tecnico completo: `clients/Sonar/projects/sistema_agentico/findings/proposta_architettura_agentica.md`.
Riferimento sintetico del documento originale: `clients/Sonar/knowledge_base/SONAR_context.md`.

## Principio: non tutto è un compito da LLM

- **Calcolo (FIT, TIMING, PONTE, instradamento in coda)**: mai a mano, mai "a occhio". Sempre `python system/scripts/sonar_engine.py score`. È aritmetica deterministica — se il numero non torna, è un bug nello script o un dato sbagliato in input, non un giudizio da rifare.
- **Lettura/estrazione da fonti non strutturate** (annunci di lavoro, siti, news, elenchi fiere): questo è compito tuo (ricerca + WebFetch/WebSearch + lettura), poi scrivi il risultato come riga in `Segnali` con `registry_io.py`.
- **Scrittura di record nel workbook**: sempre tramite `system/scripts/registry_io.py` (funzioni `add_row`, `update_row`, `find_rows`, `next_id`), mai editando l'xlsx a mano con Write o con codice posizionale — è la fonte di errori più probabile (schema con ~60 colonne in Aziende).

## C1 — Sourcing

1. Perimetro attivo: vedi `setup_checklist.md` riga 4 (vertical) e `Config_ICP` nel workbook per i criteri completi
2. Prima di aggiungere un'azienda, controlla sempre la deduplica: `find_rows(wb, 'Aziende', partita_iva=...)`. Chiave primaria P.IVA, secondaria dominio (par. 4.4 del documento) — non creare mai un secondo record per la stessa azienda
3. Per ogni azienda nuova: assegna `azienda_id` con `next_id`, compila i campi identificativi/classificazione, e **i 9 flag booleani `fit_*`** e **i 6 flag `anti_icp_*`** — sono quelli che il motore userà per il punteggio. Se non sei sicuro di un flag, lascialo vuoto piuttosto che indovinare: il motore tratta vuoto come "non verificato" (= 0 punti), che è più sicuro di un falso positivo
4. Fonti coerenti col documento (cap. 4.1): Registro Imprese/open data camerali per identificazione e classificazione; analisi del dominio per i campi digitali

## C2 — Contatti

Per ogni azienda in lavorazione, cerca e classifica contatti sulla scala L0-L4 (definita in `SONAR_context.md`), scrivili nel foglio `Contatti` con `azienda_id` come chiave esterna. Non serve enrichment su tutto l'universo — solo sulle aziende che sono già passate dal filtro anti-ICP.

## C3 — Ponte

Due percorsi diversi, non confonderli:
- **Match societario/deterministico** (soci, amministratori in comune): se hai dati camerali strutturati, puoi calcolarlo direttamente e scrivere in `Ponti` con `sorgente` coerente
- **Match assistito** (rete professionale, segnalatori, storie personali): proponi il candidato di ponte a Sara con il grado di confidenza — **non registrarlo come `stato_utilizzo=usato` mai di tua iniziativa**. L'attivazione di un ponte (la richiesta di presentazione) è sempre un atto umano fatto da chi detiene la relazione (par. 6.3 del documento)

Forza del ponte: usa la tabella `Config_Ponte_Tipologie` nel workbook, non inventare valori.

## C4 — Segnali e punteggi

1. Scanner (agentico): leggi le fonti per famiglia di segnale (S1-S6, vedi `Config_Pesi_FIT`/`Config_Pesi_TIMING`), scrivi ogni segnale rilevato come riga in `Segnali` con `codice_segnale` esatto (deve corrispondere a uno di quelli in `Config_Pesi_TIMING` per contribuire al TIMING), `data_rilevazione` e `fonte_url` sempre valorizzati — senza data e fonte il segnale non è utilizzabile (par. 3.3, tracciabilità del dato)
2. Scoring (deterministico): `python system/scripts/sonar_engine.py score` — ricalcola tutto, o `--id AZ-000123` per una sola azienda
3. Motivazione (agentico, dopo lo scoring): per le aziende che entrano in coda A/B/D, scrivi 2-3 frasi in linguaggio naturale nel campo `motivazione` di `Aziende`, citando i segnali determinanti con data e fonte — è un passo esplicitamente richiesto dal documento (par. 7.3, punto 5) e non va saltato

## C5 — Attivazione (coda + bozze)

1. `python system/scripts/sonar_engine.py queue --cap 25` — genera l'export della coda della settimana (rispetta il tetto, par. 3.3/8.5: non proporre mai di alzare il cap "per stavolta" senza che Sara lo decida esplicitamente)
2. Per ogni azienda in coda, prodotto di frontend da proporre: guarda `Config_Segnale_Prodotto` (segnale dominante -> area -> frontend) incrociato con la regola di instradamento par. 2.3.6 (coda A con ponte e necessita' dichiarata -> contatto diretto; coda A senza necessita' -> Audit Light; coda B -> Audit Light o Completo secondo rilevanza; coda D -> solo Audit Light via presentazione)
3. One Pager e primo messaggio: bozza sempre. **Non esiste, in nessuna modalità, un percorso che invia qualcosa al posto di Sara/del commerciale.** Prepara il testo, segnalalo come bozza pronta per revisione, fermati lì
4. Controllo qualità del quadrante 1 dello One Pager (par. 8.3): ogni affermazione deve avere almeno due fonti verificate e una data — se non ce l'ha, non includerla nella bozza

## C6 — Esiti

1. Quando Sara riporta un esito (appuntamento, rifiuto, contratto...), registralo in `Esiti` con lo snapshot dei punteggi al momento del contatto (`fit_snapshot`, `timing_snapshot`, `ponte_snapshot` — copia i valori correnti da `Aziende`, non ricalcolare a posteriori: il documento vuole la fotografia del momento, par. 9.2)
2. Non modificare mai i pesi in `Config_Pesi_FIT`/`Config_Pesi_TIMING` in autonomia, nemmeno "solo per vedere l'effetto": è un vincolo esplicito del documento (par. 7.5) finché non c'è GO al Gate 2. Se i dati suggeriscono che un peso è sbagliato, scrivilo come osservazione e portalo a Sara in retrospettiva

## Ad ogni sessione di lavoro sulla pipeline

Chiudi con un riepilogo breve: quante aziende trattate, quante in ciascuna coda, cosa è in attesa di revisione di Sara (bozze, ponti da confermare, casi anti-ICP in quarantena). Se hai accumulato evidenza utile per far avanzare un componente da Guidato a Semi-automatico (soglie in `automation_readiness.md`), segnalalo esplicitamente invece di aspettare che Sara lo chieda.

## Se ti serve una skill Claude Code che non hai

Non installare nulla in autonomia. Se durante il lavoro ti accorgi che una skill esistente (es. per una fonte dati specifica, un formato di export) risolverebbe un passo meglio di come lo stai facendo a mano, proponila a Sara per nome con una riga sul perché — la valida lei prima che tu la usi.
