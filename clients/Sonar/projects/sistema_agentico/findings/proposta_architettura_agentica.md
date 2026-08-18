# SONAR → Sistema Agentico: proposta di architettura
### Orchestrator | 2026-08-17
### Riferimento: SONAR_Documento_di_Progetto_v3.2.1.pdf, cap. 15 "Fasi successive — Fase 2, evoluzione agentica"

---

## 0. Premessa — perché questo non è "iniziare la Fase 2 adesso"

Il documento SONAR è molto esplicito: lo sviluppo di agenti autonomi è **fuori dal perimetro** della Fase 1 ed è condizionato al GO del Gate 2 (31 gennaio 2027) più 6 prerequisiti (cap. 15) — fra cui un registro di esiti etichettati di volume sufficiente e un processo manuale già documentato e funzionante che faccia da "capitolato".

Quello che segue **non è un'istruzione a costruire subito il sistema**, ma la risposta alla domanda che hai fatto: *come si costruirebbe, concretamente, un sistema agentico che fa esattamente quello che è scritto nel documento*. Il valore di farlo ora è che le scelte di Sprint 0 e Sprint 1 (schema Ruko, formula dei punteggi, formato del registro esiti) possono essere disegnate fin da subito in modo compatibile con l'architettura finale, invece di dover essere riscritte più avanti. Il documento lo dice esplicitamente al cap. 3.3: *"il processo manuale documentato costituisce il capitolato per l'automazione"*.

---

## 1. Principio guida: non tutto deve essere un agente LLM

Il documento SONAR, letto con attenzione, è già un capitolato tecnico quasi pronto: definisce formule di punteggio deterministiche (somme pesate con soglie e decadimento), regole di instradamento con soglie numeriche fisse, e un piccolo numero di compiti che richiedono davvero linguaggio naturale o giudizio.

Un errore comune nel costruire "un agente" per un caso come questo è affidare tutto a un LLM. Il sistema giusto è **ibrido**:

| Tipo di logica | Esempio nel documento | Come si implementa |
|---|---|---|
| **Deterministica** (motore di regole/codice) | Calcolo FIT, TIMING, PONTE (cap. 7.2-7.3); soglie anti-ICP; instradamento in coda A/B/C/D (par. 7.4); decadimento dei segnali | Codice puro, non un agente. Prevedibile, verificabile, a costo zero per esecuzione, auditabile |
| **Agentica** (LLM con tool) | Estrarre segnali da testo non strutturato (annunci, siti, news); generare la motivazione in linguaggio naturale; produrre bozze di One Pager e primo messaggio; riconoscere ponti non ovvi da rubriche testuali | Agenti LLM mirati, ciascuno con un compito stretto e un tool-set definito |
| **Umana** (obbligatoria per vincolo esplicito del documento) | Invio del primo contatto (cap. 8.2); richiesta di presentazione tramite ponte (cap. 6.3); ritaratura dei pesi in Fase 1 (par. 7.5) | Nessuna automazione. Coda di approvazione |

Questa distinzione è anche una garanzia di controllo dei costi: interrogare un LLM per ogni azienda su ogni campo del record (centinaia/migliaia di aziende × decine di campi) sarebbe sia costoso sia meno affidabile di un calcolo aritmetico. Gli agenti si usano dove il compito è davvero linguistico o di giudizio, non ovunque.

---

## 2. Mappatura componenti (C0-C6) → moduli del sistema

| Componente doc. | Nome modulo | Natura | Trigger | Umano nel loop |
|---|---|---|---|---|
| C0 Governance | **Compliance Gate** | Regole deterministiche + agente di eccezione | Ad ogni scrittura di record | Solo su casi ambigui segnalati |
| C1 Sourcing | **Sourcing Agent** | Agente con tool su fonti camerali/open data | Batch periodico (cap. 4.4) | No (fonti ufficiali) |
| C2 Contatti | **Contact Enrichment Agent** | Agente con tool di ricerca | Su record che entrano in coda | Verifica a campione |
| C3 Ponte | **Bridge Matcher** | Motore deterministico (match esatto P.IVA/soci) + agente per match "morbidi" (nomi, storie professionali) | Ad ogni nuovo cliente/segnalatore/ingresso in lista (cap. 4.4) | Sì, sui match deboli |
| C4 Segnali | **Signal Scanner** (agente) + **Scoring Engine** (deterministico) | Ibrido | Scanner mensile (FIT) / settimanale su bacino alto-FIT (TIMING) | No sul calcolo, sì sulla ritaratura pesi |
| C5 Attivazione | **Activation Drafting Agent** | Agente generativo, output = bozza, mai invio | Su ingresso in coda A/B/D | **Obbligatorio** — revisione e invio umani (vincolo esplicito cap. 8.2) |
| C6 Esiti | **Outcomes Sync + Analytics** | Deterministico (ETL da Ruko) + agente per reportistica in linguaggio naturale | Continuo / retrospettiva sprint | Sì sulla retrospettiva (par. 9.3) |

Il tutto orchestrato da un **Orchestratore SONAR** che sequenzia C1→C2→C3→C4→C5→C6 e applica i gate — concettualmente lo stesso pattern hub-and-spoke che usiamo in TTP: un coordinatore che decide *chi* fa cosa e *in che ordine*, agenti specializzati che eseguono, un datastore condiviso come canale asincrono.

---

## 3. Datastore: il cuore del sistema, non un dettaglio

Lo schema del record (Allegato B del documento) è già una specifica di database pronta all'uso: identificazione, classificazione, dimensione, digitale, presenza, contatti, ponte, segnali, punteggi, relazione, esito, governance.

**Raccomandazione:** implementare questo schema come tabelle relazionali (o Airtable/base dati leggera in Sprint 0-1, Postgres quando si scala) fin da subito, anche nella fase manuale — è lo stesso schema che serve agli agenti in Fase 2. Campi critici da NON trattare come opzionali fin dall'inizio, perché sono la spina dorsale della tracciabilità richiesta dal cap. 3.3 ("tracciabilità del dato"):

- `fonte_puntuale` + `data_rilevazione` su ogni campo popolato da fonte esterna
- `stato_utilizzo` sul ponte (per rispettare la regola "un ponte si usa una sola volta", par. 6.3)
- `riserva_confronto` (booleano) per non perdere la possibilità di validare il modello (par. 7.5)
- `profilo_segnali_snapshot` — congelare lo stato dei segnali al momento del contatto, non solo il valore corrente (par. 9.2)

Ruko resta il sistema di riferimento per la relazione commerciale (owner, storico contatti, esiti) come dichiarato nel documento (cap. 11) — il datastore SONAR *estende* Ruko con i campi punteggio/ponte/segnali via API o webhook, non lo duplica. Questo evita la violazione esplicita del perimetro ("no alla sostituzione o duplicazione del CRM in uso").

---

## 4. I singoli moduli

### 4.1 Compliance Gate (C0)
Non un agente "intelligente": un set di regole eseguite prima di qualunque scrittura/lettura. Verifica base giuridica del campo, scadenza di conservazione, stato di opposizione (**blocco tecnico**, come richiesto esplicitamente dal documento — non una nota). Un piccolo agente entra in gioco solo per classificare casi ambigui (es. un'opposizione espressa in linguaggio naturale in una email, non in un modulo strutturato) e li mette in coda per revisione umana. Girare questo controllo *prima* di ogni altro modulo, non dopo.

### 4.2 Sourcing Agent (C1)
Tool: query strutturate su Registro Imprese / open data camerali (ATECO, provincia, fascia addetti), deduplica su P.IVA (chiave primaria) e dominio (chiave secondaria), come da par. 4.4. Qui l'LLM serve poco: è principalmente integrazione API + regole di normalizzazione/deduplica. Un agente diventa utile per la classificazione settoriale quando il codice ATECO da solo non basta a distinguere l'area di intervento (par. 2.3.1) — es. leggere la descrizione attività e il sito per capire se un'azienda "manifatturiera" ha anche una componente e-commerce rilevante.

### 4.3 Contact Enrichment Agent (C2)
Compito: dato un record azienda, trovare e classificare contatti sulla scala L0-L4 (par. 5.1). Tool: ricerca web, analisi di profili pubblici, verifica formato email/telefono. Qui l'agente ha senso perché il compito è di ricerca e giudizio (distinguere un decisore da un influenzatore) più che di query strutturata. Vincolo di costo: attivarlo solo sui record che hanno superato il Compliance Gate e sono candidati a entrare in coda — non su tutto l'universo indirizzabile.

### 4.4 Bridge Matcher (C3) — il pezzo più delicato
Questo è il componente che il documento chiama "distintivo" ed è anche quello con il rischio più alto di essere sotto-progettato. Va diviso in due livelli:

1. **Match deterministico**: incrocio soci/amministratori in comune tra clienti e aziende in lista via dati camerali (già previsto come automatizzabile dallo Sprint 1, par. 6.2 punto 3) — pura logica di join, nessun LLM necessario.
2. **Match assistito da agente**: incrocio dei passaggi di persone fra aziende (par. 6.2 punto 4), rete professionale, segnalatori — dati spesso non strutturati (rubriche, LinkedIn, ricordi del team). Qui un agente può proporre candidati di match con un punteggio di confidenza, ma **non deve mai auto-registrare un ponte come attivo**: il documento è chiaro che i ponti si registrano anche quando non attivati, ma l'attivazione (la richiesta di presentazione) resta un atto umano fatto da chi detiene la relazione (par. 6.3). L'agente qui è un assistente di ricognizione, non un decisore.

Nota realistica: la sessione di ricognizione col team ("chi conosciamo qui dentro", par. 6.2 punto 7) resta strutturalmente umana — nessun agente ha accesso alla memoria relazionale non documentata del team ATMAN. Il sistema agentico può solo strutturare la domanda periodicamente (es. mandare in automatico la lista dei nuovi ingressi al team ogni settimana) e raccogliere le risposte.

### 4.5 Signal Scanner + Scoring Engine (C4)
- **Scanner (agente)**: monitora fonti eterogenee — portali annunci di lavoro, elenchi espositori fiere, stampa locale, elenchi beneficiari bandi, analisi tecnica dei domini (par. 4.1 livello 3). Compito tipico da agente: leggere un annuncio di lavoro e stabilire se corrisponde al segnale S3 "assunzione in area marketing/e-commerce/IT" — è classificazione di testo non strutturato con contesto, non lookup.
- **Scoring (motore deterministico)**: applica esattamente le tabelle dei par. 7.2-7.3 — somma punti, applica decadimento in base a `data_rilevazione` e finestra di validità, limita a 100, applica le regole anti-ICP prima del calcolo (par. 7.3). Questo NON deve essere delegato a un LLM: è aritmetica con regole fisse, e deve essere riproducibile bit-per-bit per essere auditabile e ritarabile (par. 7.5).
- **Motivazione (agente)**: genera le 2-3 frasi in linguaggio naturale richieste dal par. 7.3 punto 5, citando segnali con data e fonte — compito di generazione testuale a valle di un calcolo già fatto, non di giudizio.

### 4.6 Activation Drafting Agent (C5)
Genera bozze: One Pager a 4 quadranti (par. 8.3), script di richiesta di appuntamento coerente col prodotto di frontend indicato dalla regola del par. 2.3.6, primo messaggio sul canale assegnato (cap. 8.2). Input: il posizionamento ATMAN (par. 2.1) come riferimento di tono/registro, il profilo segnali del record, il cluster di messaggio (par. 8.4). Il controllo di qualità del quadrante 1 ("nessuna affermazione non verificata almeno due volte e priva di data", par. 8.3) è implementabile come check automatico che l'agente deve superare prima di proporre la bozza — non solo una linea guida.

**Questo è il modulo dove il vincolo umano è più forte e non negoziabile**: il documento chiede esplicitamente "bozza generata e instradata, revisione e invio umani" anche nella visione di Fase 2 più matura (tabella cap. 15, riga Attivazione: "approvazione umana obbligatoria"). Il sistema deve rendere impossibile, non solo sconsigliato, l'invio automatico — es. l'agente non ha accesso agli strumenti di invio (email, telefono, messaggistica), solo a uno strumento "salva bozza in coda di approvazione".

### 4.7 Outcomes Sync + Analytics (C6)
ETL che legge gli esiti da Ruko (registrati dal commerciale entro 24 ore, par. 8.5) e li scrive nel registro esiti (par. 9.2) con lo snapshot dei segnali al momento del contatto. Un agente leggero genera il report di retrospettiva sprint (par. 9.3) in linguaggio naturale a partire dai numeri, ma la proposta di modifica pesi resta — per esplicito vincolo del documento in Fase 1 — una decisione umana in retrospettiva. In una futura Fase 2 matura (oltre Gate 2), un agente potrebbe *proporre* una ritaratura entro soglie di controllo pre-approvate (cap. 15, riga Punteggi), sempre con validazione umana.

---

## 5. Orchestrazione

Un **Orchestratore SONAR** (agente o semplice scheduler con logica di stato) sequenzia i moduli secondo le cadenze già definite dal documento — non serve inventarne di nuove:

| Ciclo | Cadenza | Moduli coinvolti |
|---|---|---|
| Aggiornamento anagrafica/classificazione | Semestrale | C1 |
| Aggiornamento dimensione/bilanci | Annuale (post-deposito) | C1 |
| Segnali digitali | Mensile sul bacino attivo | C4 (FIT) |
| Segnali di movimento | Settimanale sul bacino ad alto FIT | C4 (TIMING) |
| Mappa dei ponti | Ad ogni nuovo cliente/segnalatore/variazione rete/ingresso lista | C3 |
| Verifica recapiti | Alla lavorazione + ogni 6 mesi | C2 |
| Costruzione coda settimanale | Settimanale | C4→C5, con tetto di erogazione (par. 8.5) |
| Registrazione esiti | Continuo, entro 24h dal commerciale | C6 |
| Retrospettiva | Ogni 4 settimane | C6 + revisione pesi umana |

Il tetto di erogazione (par. 8.5 — non superare la capacità di audit dichiarata dall'area tecnica) va implementato come **hard limit nel codice dell'orchestratore**, non come istruzione all'agente: se il numero di record instradabili in coda A/B supera la capacità settimanale, i record eccedenti restano in coda, punto — nessun agente decide di "spingere comunque".

---

## 6. Stack tecnologico concreto

Coerente con le scelte già fatte nel documento per la Fase 1 (cap. 11: preferenza per soluzioni semplici, "il valore risiede nella matrice, non nello strumento"):

| Livello | Scelta consigliata | Perché |
|---|---|---|
| Datastore | Postgres (o Airtable in Sprint 0-1 se il volume è sotto 1.000 record) con lo schema dell'Allegato B | Query relazionali per join P.IVA/soci, audit trail nativo |
| CRM di riferimento | Ruko, esteso via API/webhook | Vincolo esplicito del documento: non duplicare il CRM |
| Motore deterministico (scoring, routing, decadimento) | Codice (Python/TypeScript), non un agente | Riproducibilità, costo zero per esecuzione, auditabilità |
| Agenti LLM (scanner, enrichment, bridge assistito, drafting) | Claude Agent SDK — stesso framework che già usiamo per l'architettura TTP, con agenti stretti a compito singolo e tool espliciti | Coerenza con lo stack che già padroneggiamo; permette guardrail chiari (nessun tool di invio dato all'agente di attivazione) |
| Orchestrazione/scheduling | n8n (basso costo, adatto a un'agenzia con budget contenuto, già nel perimetro "pragmatico" della tua cliente ATMAN) oppure cron job + coda se si resta nel mondo Claude Agent SDK | Evita di introdurre un motore di workflow enterprise sproporzionato al volume (400-600 aziende in Sprint 1) |
| Fonti dati | API/open data camerali per anagrafica; script interno per analisi tecnica domini (già previsto cap. 11); tool di ricerca web per segnali non strutturati | Riuso di quanto già scelto nel documento |

Non introdurrei un orchestratore "enterprise" (Temporal, ecc.) a questo volume: il documento stesso segnala che lo strumento non è il punto, lo è la matrice di regole. Un errore comune sarebbe sovra-ingegnerizzare l'infrastruttura prima di aver validato i pesi.

---

## 7. Guardrail non negoziabili (dal documento, non aggiunti da me)

1. **Nessun invio automatico del primo contatto** — solo bozza in coda di approvazione (par. 8.2, cap. 15)
2. **Opposizione registrata = blocco tecnico**, non filtro applicativo bypassabile (par. 2.2)
3. **Un ponte si usa una sola volta per azienda** — va tracciato lo stato di utilizzo, l'agente non può riattivarlo (par. 6.3)
4. **Tetto di erogazione settimanale hard-coded**, non "best effort" di un agente (par. 8.5)
5. **Ritaratura dei pesi sempre con soglie di controllo e validazione umana**, mai libera (cap. 15, prerequisito 4)
6. **Riserva di confronto** (10-15% random fuori ordinamento) sempre attiva, altrimenti il sistema non è mai verificabile (par. 7.5)
7. **Email a freddo su lista costruita**: il documento la marca esplicitamente come "non attivabile senza parere legale e decisione esplicita della direzione" (par. 8.2) — nessun agente deve avere accesso a questo canale finché quella decisione non è presa

---

## 8. Come si innesta nella roadmap esistente (senza contraddirla)

Non sostituire Sprint 0/1: usarli per costruire, con la disciplina manuale richiesta dal documento, i due asset che rendono il sistema agentico possibile e sicuro in Fase 2:

- **Il registro esiti etichettato** (prerequisito 1 di Fase 2) — è il dataset su cui qualunque agente di ritaratura dovrà lavorare. Se lo schema è quello dell'Allegato B fin da Sprint 0, non c'è debito tecnico da recuperare dopo.
- **Il processo manuale documentato** (prerequisito 3) — ogni regola applicata a mano in Sprint 0-1 (cap. 12: matrice segnali, mappa dei ponti, procedura di lavorazione) è letteralmente la specifica funzionale degli agenti descritti sopra. Più è precisa la documentazione umana, meno ambiguità c'è nel prompt/tool-design degli agenti.

**Sequenza consigliata:**
1. Sprint 0-1 (come da documento): esecuzione manuale/semi-automatica, ma con lo schema dati e le formule già implementate in codice (non in un foglio ricalcolato a mano ogni volta) — questo è "semi-automazione" vera, non uno step in più.
2. Durante Sprint 1: costruire e testare in ombra (senza metterli in produzione) i moduli C1, C2, C4-scoring, C6-sync — sono i più deterministici e a minor rischio.
3. Dopo Gate 2 GO: introdurre gli agenti generativi (C3 assistito, C4 scanner, C5 drafting) con i guardrail del par. 7 attivi fin dal primo giorno, non aggiunti dopo un incidente.

---

## 9. Prossimi passi consigliati

1. Validare con ATMAN lo schema dati (Allegato B) come specifica tecnica dello Sprint 0, non solo come tabella descrittiva
2. Decidere ora dove vivrà il datastore (Airtable vs Postgres) in base al volume atteso di Sprint 1 (400-600 record) — evita una migrazione a metà progetto
3. Chiarire con la direzione ATMAN il punto sospeso su email a freddo (par. 8.2) prima che diventi un blocco in fase di attivazione degli agenti
4. Quando si arriva a Gate 2, ripartire da questo documento per lo sprint di design dettagliato di ciascun agente (prompt, tool-set, criteri di successo per modulo)
