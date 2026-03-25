# ORGANIGRAMMA AI AGENCY — TRUST THE PROCESS
## v5.0 — Agent Swarm Architecture (Revised)
## Agenzia di marketing, digital marketing e comunicazione per PMI italiane

**Preparato per:** Sara Quinto — Marketing Consultant & Fractional CMO
**Data:** 25 Marzo 2026
**Versione:** 5.0 — Knowledge System a 2 livelli, Catalogo Flussi, Output Persistence per-progetto, Blueprint SKILL.md v5.0, Artigiano Knowledge Processing

---

# CHANGELOG v4.0 → v4.1

| Area | v4.0 | v4.1 | Motivazione |
|------|------|------|-------------|
| Comunicazione inter-agente | Sistema mailbox (22 file .md, UNREAD/READ) | Hub-and-spoke via Task tool + file condivisi | Mailbox simulava messaging su un sistema che non lo supporta. Overhead di token enorme per read/write/parse senza benefici reali. |
| Agent Loop | 10 step per ciclo | 4 step (Read context → Execute → Write output → Report) | 10 step = 10 tool call per unita' di lavoro = migliaia di token di burocrazia. |
| Task Tool Prompt | Non formalizzato | Task Tool Prompt Protocol con template strutturato | Il prompt del Task tool e' il punto dove si vince o si perde. Merita una sezione dedicata. |
| Error handling | Assente | Retry + escalation a Sara (mai auto-esecuzione) | Il happy path non basta. Serve graceful degradation con Sara nel loop decisionale. |
| Anti-context rot | Agente dedicato (Economo) + Context Health Score | 3 regole embedded nei system prompt + file checkpoint | L'Economo consumava token per risparmiare token. Paradosso risolto. |
| Allocazione LLM | 11 Opus, 10 Sonnet, 1 Haiku | 4 Opus fissi + 4 dual-mode + 13 Sonnet + 1 Haiku | Opus dove sbagliare costa caro o dove la qualita' di ragionamento e' non negoziabile. Risparmio stimato 35-55%. |
| Pre-sales | Gap — solo charter/proposta | Workflow completo: qualificazione → discovery → pricing → proposta → obiezioni → close | La negoziazione commerciale era il pezzo mancante del sistema. |
| Ruolo Stratega | Confuso con Orchestratore | Distinto: Stratega = cervello strategico, Orchestratore = coordinatore operativo | Lo Stratega guida le decisioni, l'Orchestratore le esegue come flusso di lavoro. |
| File di sistema | task_list + status_board + 22 mailbox + context_state + decisions_log | task_list + findings/ + clients/ | Status board ridondante (l'Orchestratore sa gia' chi fa cosa). Mailbox eliminate. |

# CHANGELOG v4.1 → v5.0

| Area | v4.1 | v5.0 | Motivazione |
|------|------|------|-------------|
| Knowledge System | Framework copiati dentro SKILL.md dall'Artigiano | Sistema a 2 livelli: Quick Reference (sempre in contesto) + Deep Knowledge (on-demand) | Elimina duplicazione, rende SKILL.md piu' snelle, aggiornamento centralizzato, scalabilita' |
| Blueprint SKILL.md | 6 sezioni, framework embedded, max 2.000 token | 8 sezioni (+ Prerequisiti + Checklist Qualita'), framework come riferimenti esterni, max 1.500 token | Input Validation previene lavoro su dati mancanti, Quality Checklist riduce carico God Mode |
| Task Tool Prompt Protocol | 7 sezioni | 8 sezioni (+ Knowledge Skills con safety check) | Garantisce che l'agente carichi i framework prima di lavorare |
| Flussi operativi | 2 flussi (progetto + pre-sales) | Catalogo Flussi in /operations/procedure/ (8+ flussi + protocollo fallback) | Copertura completa dei tipi di richiesta, meno improvvisazione |
| Output persistence | /system/findings/ generico | Per-progetto in /clients/[cliente]/progetti/[nome]/ con output per agente | Tracciabilita' totale, riproducibilita', storico per God Mode |
| File di sistema | task_list + decisions_log | + sessione.md (stato corrente), + /operations/procedure/ | Ripresa sessione piu' rapida, flussi operativi codificati |
| Artigiano | Solo Skill Maintenance | 2 modalita': Skill Maintenance + Knowledge Processing | Pipeline scalabile per processare libri, corsi, metodologie proprietarie |
| Agent Loop | READ → EXECUTE → WRITE → REPORT | READ (incluse Quick Reference) → EXECUTE → WRITE → REPORT | Le Quick Reference vengono caricate come primo step |

---

# PARTE I — ARCHITETTURA SWARM

## 1.1 PRINCIPI ARCHITETTURALI

L'agenzia opera come un **agent swarm hub-and-spoke**: un insieme di agenti specializzati coordinati dall'Orchestratore, che comunica con ognuno di loro attraverso il Task tool di Claude Code e attraverso file condivisi nel file system.

**Principi fondamentali:**

1. **Hub-and-spoke** — L'Orchestratore e' l'hub. Spawna agenti, passa contesto, riceve output. Gli agenti non comunicano tra loro via mailbox — usano file condivisi come canale asincrono e il Task tool come canale sincrono.
2. **Esecuzione parallela** — Quando i task sono indipendenti, piu' agenti lavorano contemporaneamente via Task tool.
3. **File system come memoria condivisa** — I file in `/system/` e `/clients/` sono il "disco" del sistema. Il contesto e' la "RAM". Le informazioni importanti vanno SEMPRE scritte su file.
4. **Agent loop snello (4 step)** — Read context (incluse Quick Reference) → Execute → Write output → Report. Niente burocrazia.
5. **Anti-context rot embedded** — 3 regole nei system prompt, nessun agente dedicato.
6. **Task Tool Prompt Protocol (8 sezioni)** — Il prompt passato al Task tool e' il punto critico del sistema. Deve essere strutturato, completo, e ottimizzato. Include la sezione KNOWLEDGE SKILLS con safety check.
7. **Fail-safe con Sara nel loop** — Se qualcosa fallisce, si escala a Sara con contesto e opzioni. Mai auto-esecuzione su fallimento.
8. **Stratega come cervello strategico** — Lo Stratega NON e' un esecutore. Guida le decisioni strategiche coordinandosi con gli operativi per informarsi, poi decide la direzione. L'Orchestratore traduce le decisioni strategiche in task operativi.
9. **(NUOVO v5.0) Knowledge System a 2 livelli** — Quick Reference (max 120 righe, sempre caricate) + Deep Knowledge (max 350 righe, on-demand). Le SKILL.md referenziano i framework, non li contengono.
10. **(NUOVO v5.0) Output persistence per-progetto** — Ogni output agente e' tracciato in `/clients/[cliente]/progetti/[nome]/findings/[agente]_[tipo].md`. Storico completo per God Mode e audit.
11. **(NUOVO v5.0) Catalogo Flussi** — Le procedure operative sono codificate in `/operations/procedure/`. Richieste non mappate seguono il protocollo fallback (Orchestratore propone → Sara decide → opzionalmente si mappa).

## 1.2 FILE DI SISTEMA (SHARED MEMORY)

```
/system/
├── task_list.md            # Task list condivisa — SOLO l'Orchestratore scrive
├── sessione.md             # (NUOVO v5.0) Stato sessione corrente: progetto attivo, ultimo task, prossimo step, blocchi
├── decisions_log.md        # Log decisioni strategiche (per audit trail)
├── findings/               # Scoperte e ricerche di sistema (NON legate a un progetto specifico)
│   └── [topic]_findings.md
└── progress/               # Checkpoint di avanzamento per progetto
    └── [progetto]_progress.md

/clients/[nome_cliente]/
├── brief.md
├── positioning.md
├── messaging.md
├── charter.docx
├── presales/               # Materiali pre-sales
│   ├── qualification.md
│   ├── discovery_prep.md
│   ├── objection_map.md
│   └── negotiation_strategy.md
├── progetti/               # (NUOVO v5.0) Output persistence per-progetto
│   └── [nome_progetto]/
│       ├── README.md       # Brief progetto, agenti attivati, stato, date
│       ├── findings/       # Output per-agente: [agente]_[tipo].md
│       └── SINTESI_FINALE.md  # Deliverable sintetizzato dall'Orchestratore
└── deliverables/           # Deliverable finali consegnati al cliente

/knowledge_base/
├── frameworks/             # Metodologie proprietarie Sara
│   ├── piano_marketing_piccole_imprese.md
│   ├── piano_marketing_strutturate.md
│   ├── metodo_snello.md
│   ├── brief_format.md
│   ├── key_action_template.md
│   ├── sprint_ttp.md
│   └── project_charter_template.md
├── corsi/                  # Principi estratti dai corsi
│   ├── aliotta_positioning.md
│   ├── abate_strategy.md
│   └── [altri_corsi].md
├── brand_guidelines/[cliente]/
│   ├── brand_guide.md
│   ├── tone_of_voice.md
│   └── assets/
├── templates/              # Template operativi
│   ├── battlecard_template.md
│   ├── ped_template.xlsx
│   ├── dashboard_template.xlsx
│   ├── contratto_servizio_template.docx
│   ├── privacy_policy_template.md
│   ├── nda_template.docx
│   └── fattura_template.md
├── benchmark/              # Dati di riferimento settoriali
│   ├── benchmark_social_italia.md
│   ├── benchmark_email.md
│   ├── benchmark_cro.md
│   └── [settore]_benchmark.md
├── storico/                # Output passati come reference
│   ├── piani_marketing/
│   ├── charter/
│   ├── analisi_competitor/
│   └── coaching_sessions/
└── ttp_internal/           # Documentazione interna TTP
    ├── listino_servizi.md
    ├── processi_interni.md
    ├── parametri_fiscali_sara.md
    ├── obiettivi_annuali.md
    └── AI_Agency_TTP_v5.0_Swarm_Architecture.md

/skills/
├── [nome_teammate]/SKILL.md  # 22 SKILL.md (una per teammate)
└── knowledge/                # (NUOVO v5.0) Sistema a 2 livelli
    ├── strategy/             # Quick Reference + Deep Knowledge
    ├── marketing/
    ├── analysis/
    ├── operations/
    ├── quality/
    ├── business/
    └── corsi_sara/

/operations/                  # (NUOVO v5.0) Catalogo Flussi operativi
└── procedure/
    ├── catalogo_flussi.md    # Mappa completa dei flussi con trigger e agenti
    └── flussi_custom/        # Flussi personalizzati aggiunti nel tempo
```

### 1.2.1 FORMATO TASK LIST (`/system/task_list.md`)

```markdown
# TASK LIST — TTP Agency
## Ultimo aggiornamento: [timestamp]

### TASK ATTIVI

| ID | Task | Assegnato a | Priorita' | Stato | Dipendenze | Deadline | Note |
|----|------|------------|-----------|-------|------------|----------|------|
| T001 | Analisi competitor Settore X | Esploratore | Alta | IN_PROGRESS | - | 25/03 | Cliente: Acme |
| T002 | Draft charter Progetto Y | Architetto | Alta | WAITING | T001 | 27/03 | Aspetta ricerca |

### TASK COMPLETATI (ultimi 7 giorni)
| ID | Task | Completato da | Data | Output file |
|----|------|--------------|------|-------------|
| T000 | Setup progetto Acme | Admin | 23/03 | /clients/acme/brief.md |

### REGOLE:
- SOLO l'Orchestratore crea e aggiorna la task list
- Gli agenti scrivono i propri output in /clients/[cliente]/progetti/[progetto]/findings/ (per output di progetto) o /system/findings/ (per findings generici)
- L'Orchestratore aggiorna la task list dopo aver ricevuto gli output dai subagent
```

### 1.2.2 OUTPUT PERSISTENCE PER-PROGETTO (NUOVO v5.0)

Ogni progetto genera una cartella strutturata per tracciabilita' completa:

```
/clients/[nome_cliente]/progetti/[nome_progetto]/
├── README.md                          # Brief, agenti attivati, stato, date
├── findings/
│   ├── esploratore_competitors.md     # Output Esploratore
│   ├── stratega_positioning.md        # Output Stratega
│   ├── voce_messaging.md             # Output Voce
│   ├── calcolatore_costi.md          # Output Calcolatore
│   └── god_mode_scorecard.md         # Scorecard God Mode
└── SINTESI_FINALE.md                  # Deliverable sintetizzato
```

**Flusso output persistence:**
1. L'Orchestratore chiede a Sara il nome del progetto PRIMA di iniziare
2. Crea la cartella e il README.md con brief e piano agenti
3. Per ogni agente attivato, passa `output_path` nel Task Tool Prompt
4. Ogni agente salva il suo output completo nel path ricevuto
5. Al termine, l'Orchestratore salva la sintesi in SINTESI_FINALE.md
6. Il README.md viene aggiornato con stato finale e date

**Regola:** `/system/findings/` rimane per findings generici non legati a un progetto specifico (es: benchmark di settore, ricerche esplorative). I findings di progetto vanno SEMPRE nella cartella del progetto.

## 1.3 SISTEMA DI COMUNICAZIONE HUB-AND-SPOKE

### Come comunicano gli agenti

**Canale sincrono: Task Tool Prompt**
L'Orchestratore (o qualsiasi agente con capacita' di spawn) passa tutto il contesto necessario direttamente nel prompt del Task tool quando spawna un subagent. L'output del subagent torna come risultato del Task tool. Non servono mailbox intermedie.

**Canale asincrono: File condivisi**
Quando un agente produce output che altri dovranno usare in futuro, lo scrive su file (in `/clients/[cliente]/progetti/[progetto]/findings/` o `/system/findings/`). L'Orchestratore sa dove sono i file e passa i riferimenti nel prompt del prossimo agente.

**Coordinamento diretto tra agenti**
Quando lo Stratega ha bisogno di dati dall'Esploratore per prendere una decisione, lo Stratega ha il Task tool e puo' spawnare l'Esploratore come suo subagent. Il flusso e':
```
Orchestratore spawna Stratega
  → Stratega spawna Esploratore (per raccogliere dati specifici)
  → Esploratore restituisce output allo Stratega
  → Stratega usa i dati per la decisione strategica
  → Stratega restituisce output all'Orchestratore
```

**Regola fondamentale:** I file condivisi sono il canale di comunicazione asincrona. Il Task tool prompt e' il canale di comunicazione sincrona. Non serve altro.

### Chi puo' spawnare chi (Matrice Spawn)

| Spawner | Puo' spawnare |
|---------|--------------|
| **Orchestratore** | TUTTI i teammate |
| **Stratega** | Esploratore, Calcolatore, Voce, Sparring Partner |
| **Architetto** | Calcolatore, Legale |
| **Voce** | Esploratore, Editore |
| **Ottimizzatore** | Formatore, Tecnico Web |
| **Calcolatore** | Esploratore, Commercialista |
| **Mentore** | Calcolatore, Commercialista, Stratega |
| **Sparring Partner** | Esploratore, Calcolatore |
| **Economo** | Artigiano, Manutentore |

Tutti gli altri agenti NON hanno il Task tool e vengono spawnati dall'Orchestratore o da un team leader.

## 1.4 TASK TOOL PROMPT PROTOCOL (v5.0 — 8 SEZIONI)

**Questa e' la sezione piu' critica dell'intera architettura.** Il prompt passato al Task tool e' il SINGOLO punto dove si determina la qualita' dell'output, l'efficienza dei token, e la coerenza del sistema. Un prompt mal scritto produce output mediocre indipendentemente dal modello LLM usato.

### Template Task Tool Prompt (v5.0)

Ogni agente che spawna un subagent DEVE usare questo template:

```
## IDENTITA'
Sei [Nome Teammate], [ruolo]. [1 frase sulla tua missione].

## CONTESTO PROGETTO
- Cliente: [nome]
- Settore: [settore]
- Obiettivo del progetto: [1-2 frasi]
- Fase attuale: [dove siamo nel flusso]

## KNOWLEDGE SKILLS (NUOVO v5.0)
- Quick Reference caricate: [lista nomi quickref assegnate a questo agente]
- Path Quick Reference: /skills/knowledge/[categoria]/[nome]-quickref.md
- REGOLA: All'inizio del task, verifica che le Quick Reference esistano. Se presenti, leggile
  con Read() PRIMA di eseguire il task. Se assenti, procedi con le tue conoscenze base
  e segnala l'assenza nel report.
- Deep Knowledge disponibili: [lista nomi deep se pertinenti al task]
- Per approfondimenti: leggi /skills/knowledge/[categoria]/[nome]-deep.md SOLO se il task
  richiede un framework in modo approfondito.

## TASK SPECIFICO
[Descrizione precisa di cosa deve fare, con criteri di successo misurabili]

## INPUT DISPONIBILI
- [Elenco file da leggere con path completi]
- [Dati chiave gia' estratti e passati inline se brevi — evita di far leggere file quando il dato puo' stare in 2-3 righe]

## OUTPUT ATTESO
- Formato: [md/docx/xlsx/etc.]
- Destinazione: [path completo — usa /clients/[cliente]/progetti/[progetto]/findings/ per output di progetto]
- Struttura: [sezioni attese o template da seguire]
- Lunghezza target: [range approssimativo]

## VINCOLI
- [Limiti di tempo, budget, scope]
- [Framework da applicare obbligatoriamente]
- [Cosa NON fare]

## REGOLE ANTI-CONTEXT ROT
- Salva findings su file dopo ogni output significativo
- Se il task richiede piu' di 15 tool calls, salva un checkpoint in /system/progress/ e segnala
- Usa il file system come disco, il contesto come RAM
```

### Regole del Task Tool Prompt Protocol (v5.0)

1. **Mai passare contesto inutile.** Se l'agente non ha bisogno della storia completa del progetto, non passargliela. Passa solo cio' che serve per il task specifico.
2. **Inline i dati brevi, file i dati lunghi.** Se un dato sta in 3 righe, mettilo nel prompt. Se richiede una pagina, passa il path del file.
3. **Output atteso esplicito.** L'agente deve sapere esattamente cosa produrre, dove scriverlo, e in che formato. Nessuna ambiguita'.
4. **Vincoli come guardrail.** I vincoli prevengono il "scope creep" degli agenti (tendenza a fare piu' del richiesto, bruciando token).
5. **Le regole anti-context rot sono sempre presenti.** Sono le stesse 3 righe in ogni prompt. Non costano quasi nulla e prevengono problemi gravi.
6. **(NUOVO v5.0) La sezione KNOWLEDGE SKILLS e' SEMPRE presente.** L'Orchestratore popola la lista Quick Reference consultando il frontmatter `knowledge_quickref:` della SKILL.md dell'agente. Se l'agente non ha skill assegnate, la sezione riporta "Nessuna Quick Reference assegnata".
7. **(NUOVO v5.0) L'output_path punta alla cartella del progetto** quando il lavoro e' legato a un progetto cliente.

### ESEMPI CONCRETI COMPILATI

**Esempio 1 — Orchestratore spawna Esploratore v5.0 (con Knowledge Skills)**

```
## IDENTITA'
Sei l'Esploratore, Market Intelligence Officer. La tua missione e' raccogliere
dati di mercato accurati, strutturati, e azionabili.

## CONTESTO PROGETTO
- Cliente: Acme Srl
- Settore: Pet food premium, mercato italiano
- Obiettivo del progetto: Definire posizionamento e strategia marketing per lancio linea bio
- Fase attuale: Fase 1 — Ricerca di mercato (pre-strategia)

## KNOWLEDGE SKILLS
- Quick Reference caricate: porter-5forces, pestel, battlecard
- Path: /skills/knowledge/analysis/[nome]-quickref.md
- REGOLA: Leggi le Quick Reference con Read() PRIMA di iniziare il task.
  Se un file non esiste, procedi e segnala nel report.
- Deep Knowledge disponibili: porter-5forces, swot
- Per approfondimenti: /skills/knowledge/analysis/[nome]-deep.md

## TASK SPECIFICO
Analizza i 5 principali competitor diretti di Acme nel segmento pet food premium/bio
in Italia. Per ogni competitor produci: posizionamento, range prezzi, canali di vendita,
punti di forza, punti di debolezza, stima quota di mercato. Concludi con una Battlecard
comparativa e 3-5 insight strategici per il posizionamento di Acme.

## INPUT DISPONIBILI
- Brief cliente: /clients/acme/brief.md
- Acme vende attualmente crocchette premium (non bio) in 200 punti vendita nel Nord Italia
- Fatturato 2025: €1.2M, obiettivo 2026: €1.8M
- Budget marketing annuale: €50.000

## OUTPUT ATTESO
- Formato: Markdown
- Destinazione: /clients/acme/progetti/lancio_bio/findings/esploratore_competitors.md
- Struttura: Overview mercato (500 parole) → 5 schede competitor (Battlecard format) →
  Tabella comparativa → Insight strategici
- Lunghezza target: 8-12 pagine

## VINCOLI
- Focus solo mercato italiano (no competitor esteri senza presenza in Italia)
- Usa fonti verificabili (siti web, articoli, dati pubblici). Segnala quando un dato e' stimato
- NON produrre raccomandazioni strategiche — quelle sono compito dello Stratega
- Framework: Porter's 5 Forces per l'overview, Battlecard template per i competitor

## REGOLE ANTI-CONTEXT ROT
- Salva findings su file dopo ogni output significativo
- Se il task richiede piu' di 15 tool calls, salva un checkpoint in /system/progress/ e segnala
- Usa il file system come disco, il contesto come RAM
```

**Esempio 2 — Orchestratore spawna Stratega v5.0 (con Knowledge Skills)**

```
## IDENTITA'
Sei lo Stratega, Chief Strategy Officer. La tua missione e' definire la direzione
strategica che massimizza il vantaggio competitivo del cliente.

## CONTESTO PROGETTO
- Cliente: Acme Srl
- Settore: Pet food premium/bio, mercato italiano
- Obiettivo: Posizionamento per lancio linea bio
- Fase attuale: Fase 2 — Strategia (post-ricerca)

## KNOWLEDGE SKILLS
- Quick Reference caricate: collins-hedgehog, deveglia-positioning, christensen-jtbd, lafley-playing-to-win
- Path: /skills/knowledge/strategy/[nome]-quickref.md
- REGOLA: Leggi le Quick Reference con Read() PRIMA di iniziare il task.
- Deep Knowledge disponibili: collins-hedgehog, deveglia-positioning, christensen-jtbd
- Per approfondimenti: /skills/knowledge/strategy/[nome]-deep.md

## TASK SPECIFICO
Definisci il posizionamento strategico di Acme per il lancio della linea bio.
Applica Hedgehog Concept + De Veglia Positioning + JTBD. Produci: analisi
dell'intersezione Hedgehog, mappa posizionamento vs. competitor, brandshot
De Veglia, Job-to-be-done principale, 3-5 messaging pillar.

## INPUT DISPONIBILI
- Findings competitor: /clients/acme/progetti/lancio_bio/findings/esploratore_competitors.md
- Brief cliente: /clients/acme/brief.md
- Il CEO di Acme e' un veterinario, forte credibilita' tecnica
- Target primario: proprietari di cani/gatti, 30-50 anni, reddito medio-alto, Nord Italia
- Pain point emerso dalla discovery: "non mi fido degli ingredienti delle marche industriali"

## OUTPUT ATTESO
- Formato: Markdown
- Destinazione: /clients/acme/progetti/lancio_bio/findings/stratega_positioning.md
- Struttura: Hedgehog analysis → Mappa posizionamento → Brandshot De Veglia →
  JTBD primary job → Messaging pillar (3-5) → Raccomandazione finale
- Lunghezza target: 5-8 pagine

## VINCOLI
- Budget marketing cliente: €50.000/anno — le strategie devono essere eseguibili con questo budget
- Il posizionamento deve differenziare Acme da [competitor X e Y identificati nei findings]
- Se hai bisogno di dati aggiuntivi, spawna l'Esploratore come subagent
- Se hai dubbi sulla fattibilita' finanziaria, spawna il Calcolatore

## REGOLE ANTI-CONTEXT ROT
- Salva findings su file dopo ogni output significativo
- Se il task richiede piu' di 15 tool calls, salva un checkpoint in /system/progress/ e segnala
- Usa il file system come disco, il contesto come RAM
```

**Esempio 3 — Stratega spawna Esploratore come subagent (ricerca mirata)**

```
## IDENTITA'
Sei l'Esploratore. Missione: raccolta dati mirati.

## CONTESTO PROGETTO
- Cliente: Acme Srl, pet food bio
- Ti sta spawnando lo Stratega per una ricerca specifica

## KNOWLEDGE SKILLS
- Quick Reference caricate: nessuna (ricerca specifica, non serve framework)
- Nessuna Quick Reference assegnata per questo micro-task.

## TASK SPECIFICO
Cerca dati sul mercato pet food bio in Italia: dimensione stimata, tasso di crescita
2023-2025, trend di consumo, profilo del consumatore bio pet food. Cerca anche
se esistono certificazioni bio specifiche per il pet food in Italia/EU.

## INPUT DISPONIBILI
- Nessun file da leggere — questa e' una ricerca web ex novo

## OUTPUT ATTESO
- Formato: Markdown
- Destinazione: /clients/acme/progetti/lancio_bio/findings/esploratore_bio_market_data.md
- Struttura: Dimensione mercato → Trend → Profilo consumatore → Certificazioni → Fonti
- Lunghezza target: 2-3 pagine (quick findings)

## VINCOLI
- Max 8 ricerche web
- Segnala chiaramente quali dati sono stimati e quali verificati
- NON interpretare strategicamente i dati — restituiscili grezzi

## REGOLE ANTI-CONTEXT ROT
- Salva findings su file dopo ogni output significativo
- Se il task richiede piu' di 15 tool calls, salva un checkpoint in /system/progress/ e segnala
- Usa il file system come disco, il contesto come RAM
```

### Ottimizzazione token del Task Tool Prompt

| Pratica | Token risparmiati | Impatto qualita' |
|---------|------------------|------------------|
| Inline dati brevi vs. Read file | 200-500 per chiamata | Neutro (stesso dato) |
| Omettere contesto irrilevante | 500-2.000 per spawn | Positivo (meno rumore) |
| Output atteso con struttura | 0 (stesso costo) | Molto positivo (output piu' preciso, meno iterazioni) |
| Vincoli espliciti | 50-100 per prompt | Molto positivo (previene scope creep) |
| Knowledge Skills safety check | ~100 per prompt | Positivo (framework caricato prima del lavoro, fallback graceful) |

## 1.5 AGENT LOOP SEMPLIFICATO (4 STEP — v5.0)

Ogni agente, quando viene spawnato, segue questo ciclo:

```
AGENT LOOP:
1. READ — Leggi i file indicati nel prompt (input, findings precedenti, KB se necessario)
         + Leggi le Quick Reference indicate nella sezione KNOWLEDGE SKILLS (safety check:
           se presenti leggile, se assenti procedi e segnala)
2. EXECUTE — Esegui il lavoro usando i tuoi tool e framework
3. WRITE — Scrivi l'output nella posizione indicata nel prompt
4. REPORT — Restituisci un summary all'agente che ti ha spawnato (torna come risultato del Task tool)
```

**Regole:**
- Max 15 tool calls per sessione prima di un checkpoint (salva findings su file e segnala)
- Se bloccato per >3 tentativi su un'azione, FERMA e restituisci il problema nel report
- L'output scritto su file e' il deliverable. Il report testuale e' il summary per il coordinamento.

## 1.6 ESECUZIONE PARALLELA E SPAWNING

L'Orchestratore puo' spawnare piu' agenti in parallelo usando il Task tool di Claude Code:

```
# Esempio: L'Orchestratore spawna 3 agenti in parallelo
Task 1: Esploratore → "Analizza competitor settore X" (usa il Task Tool Prompt Protocol v5.0)
Task 2: Voce → "Definisci messaging per cliente Y" (usa il Task Tool Prompt Protocol v5.0)
Task 3: Calcolatore → "Prepara proiezioni finanziarie per Z" (usa il Task Tool Prompt Protocol v5.0)

# I 3 agenti lavorano contemporaneamente
# Ognuno scrive il proprio output in /clients/[cliente]/progetti/[progetto]/findings/
# L'Orchestratore riceve i 3 report e aggiorna la task_list
```

**Regole di spawning:**
- Solo l'Orchestratore e gli agenti nella Matrice Spawn (sezione 1.3) possono spawnare
- Max 5 agenti in parallelo (limite pratico Claude Code)
- Prima di spawnare, verificare le dipendenze nella task_list
- Agenti indipendenti → parallelo; agenti dipendenti → sequenziale
- **CRITICO:** Solo l'Orchestratore aggiorna la task_list dopo aver ricevuto gli output. Nessun altro agente scrive sulla task_list.

## 1.7 ANTI-CONTEXT ROT (3 REGOLE EMBEDDED)

Le seguenti 3 regole sono inserite nel system prompt di OGNI agente (gia' incluse nel Task Tool Prompt Protocol):

**Regola 1 — Salva su file dopo ogni output significativo.**
Non affidare informazioni importanti solo al contesto. Scrivi sempre su file.

**Regola 2 — Checkpoint a 15 tool calls.**
Se il task richiede piu' di 15 tool calls, salva un checkpoint in `/system/progress/[progetto]_progress.md` con: cosa hai fatto finora, cosa resta da fare, findings intermedi. Poi segnala nel report.

**Regola 3 — Contesto come RAM, file come disco.**
Il contesto e' volatile. Il file system e' persistente. Quando leggi dati da un file, estrai solo cio' che ti serve — non caricare interi documenti nel contesto se ti servono 3 righe.

**Nota:** L'Economo (#18) mantiene il suo ruolo di monitoraggio costi e ottimizzazione token, ma NON gestisce piu' un sistema di Context Health Score. Le sue responsabilita' anti-context rot sono limitate a: audit periodico delle SKILL.md per lunghezza e efficienza, report mensile costi token per teammate, raccomandazioni di ottimizzazione.

## 1.8 ERROR HANDLING & FALLBACK PROTOCOL (v5.0)

Quando un subagent fallisce (output vuoto, errore, risultato inadeguato), il sistema segue questo protocollo:

```
ERRORE RILEVATO (output vuoto, errore, o qualita' sotto standard)
│
├─ STEP 1: RETRY (automatico)
│  L'Orchestratore rispawna l'agente con prompt semplificato:
│  - Rimuovi contesto non essenziale
│  - Rendi il task piu' specifico
│  - Riduci lo scope se possibile
│
├─ STEP 2: Se il retry fallisce → ESCALATION A SARA
│  L'Orchestratore presenta a Sara:
│  - Cosa si stava cercando di fare
│  - Cosa e' andato storto (errore specifico)
│  - 2-3 opzioni per procedere (es: "provare con approccio diverso",
│    "saltare questo step e procedere", "Sara lo fa manualmente")
│  - Raccomandazione dell'Orchestratore su quale opzione preferire
│
│  ⚠️ L'ORCHESTRATORE NON ESEGUE MAI AUTONOMAMENTE IL TASK FALLITO.
│  Sara decide sempre come procedere.
│
└─ STEP 3: Sara sceglie → L'Orchestratore esegue la scelta
```

**Tipi di fallimento e risposta:**

| Tipo fallimento | Retry automatico | Escalation |
|----------------|-----------------|------------|
| Output vuoto (agente non ha prodotto nulla) | Si' — prompt semplificato | Se retry fallisce |
| Errore tool (WebSearch non trova, file non esiste) | Si' — approccio alternativo | Se retry fallisce |
| Output sotto standard (qualita' inadeguata) | Si' — prompt piu' specifico con esempi | Se retry fallisce |
| Timeout / token limit raggiunto | No retry | Escalation immediata con checkpoint |
| Task ambiguo (agente non sa cosa fare) | No retry | Escalation immediata — serve chiarimento |
| Quick Reference mancanti (NUOVO v5.0) | No retry (l'agente procede con conoscenze base) | Solo segnalazione nel report |
| Richiesta non mappata nel Catalogo Flussi (NUOVO v5.0) | No retry | Orchestratore propone a Sara → Sara decide |

---

# PARTE II — SCHEDE TEAMMATE COMPLETE

Per ogni teammate: LLM (con giustificazione rivista), memoria, tool, framework, output.

**ALLOCAZIONE LLM — Principio: "Opus solo dove sbagliare costa caro"**

| Categoria | Modello | Teammate | Giustificazione |
|-----------|---------|----------|-----------------|
| **Opus fisso** (4) | Opus 4 — mai degradare | Orchestratore, Stratega, God Mode, Sparring Partner | Errore di routing, errore strategico, errore di quality gate = danni a cascata |
| **Dual-mode** (4) | Opus per strategia, Sonnet per esecuzione | Voce, Architetto, Calcolatore, Mentore | Opus quando pensano, Sonnet quando compilano |
| **Sonnet fisso** (13) | Sonnet 4 | Esploratore, Narratore, Editore, Regista, Misuratore, Ottimizzatore, Formatore, Tecnico Web, Commercialista, Legale, Economo, Manutentore, Artigiano | Task strutturati o con framework robusti che compensano |
| **Haiku** (1) | Haiku 4.5 | Admin | Task semplici e ripetitivi |

---

## TEAMMATE #0 — ORCHESTRATORE
### Chief of Staff AI — Swarm Controller

### LLM

| Parametro | Valore | Giustificazione |
|-----------|--------|-----------------|
| **Modello** | Opus 4 | Ragionamento multi-step: decomporre task, valutare dipendenze, decidere routing, gestire conflitti, scrivere Task Tool Prompts ottimizzati. Un errore di routing costa piu' di qualsiasi risparmio. |
| **Degradazione** | Mai | |

### Ruolo e confini

L'Orchestratore e' un **coordinatore operativo**. Decide CHI fa cosa, QUANDO, e IN CHE ORDINE. NON decide COSA fare strategicamente — quello e' compito dello Stratega. L'Orchestratore:
- Riceve le richieste di Sara
- Decompone in task operativi (consultando lo Stratega per le decisioni strategiche)
- Spawna gli agenti giusti con Task Tool Prompt Protocol v5.0 ottimizzati (8 sezioni, inclusa KNOWLEDGE SKILLS)
- Raccoglie output e aggiorna la task_list
- Gestisce errori e escalation
- Consegna gli output finali a Sara
- **(NUOVO v5.0)** Consulta il Catalogo Flussi per determinare la procedura corretta. Se la richiesta non e' mappata, propone a Sara come intende agire.
- **(NUOVO v5.0)** Crea la cartella progetto e aggiorna sessione.md ad ogni cambio di stato.

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| L1 — System Prompt | Identita', Task Tool Prompt Protocol v5.0 (8 sezioni), matrice spawn, elenco teammate con competenze, error handling protocol, regole anti-context rot, Catalogo Flussi reference | ~2.200 token |
| L2 — Working Context | Task list attiva, progetto corrente, dipendenze, sessione.md | ~3.000 token |
| L3 — Knowledge Base (file) | Regole di ingaggio per progetto, storico decisioni, template decomposizione task, procedure in /operations/procedure/ | On-demand via Read |

### Tool

| Tool | Tipo | Uso |
|------|------|-----|
| **Task** | Nativo | Spawnare teammate come subagent (parallelo o sequenziale) |
| **Read/Write/Edit** | Nativo | Leggere/scrivere file di sistema (task list, findings, progress, sessione.md) |
| **Glob/Grep** | Nativo | Cercare file nei progetti clienti |
| **Google Drive** (MCP) | MCP | Accesso ai documenti Drive di Sara e dei clienti |
| **Google Calendar** (MCP) | MCP | Verificare disponibilita', deadline, scadenze |
| **Gmail** (MCP) | MCP | Leggere email rilevanti, bozze comunicazioni |
| **WebSearch** | Nativo | Ricerche rapide per contesto decisionale |
| **TodoWrite** | Nativo | Gestire la todo list di sessione |

### Framework operativi

| Framework | Applicazione operativa |
|-----------|----------------------|
| **GTD** | Ogni richiesta di Sara → Capture → Clarify (cosa serve?) → Organize (chi lo fa?) → Reflect (priorita'?) → Engage (spawna) |
| **Eisenhower Matrix** | Urgente+Importante = fai ora; Importante+NonUrgente = pianifica; Urgente+NonImportante = delega ad Admin; NonUrgente+NonImportante = elimina |
| **RACI** | Per ogni task: R(esponsabile), A(ccountable=Sara per il 5%), C(onsultato), I(nformato) |
| **Cynefin** | Simple → applica template; Complicated → attiva specialista; Complex → esplora con Esploratore; Chaotic → escalata a Sara |

### Output

| Tipo output | Formato | Destinazione |
|-------------|---------|-------------|
| Task decomposition | Tabella task con ID, assegnazione, dipendenze, deadline | `/system/task_list.md` |
| Status report per Sara | Markdown: task completati, in corso, bloccati, decisioni richieste | Diretto a Sara |
| Escalation request | Contesto + opzioni + raccomandazione | Diretto a Sara |
| Team spawn | Batch di Task tool calls con prompt strutturati (Task Tool Prompt Protocol v5.0) | Via Task tool |
| Sessione update | Progetto attivo, ultimo task, prossimo step, blocchi | `/system/sessione.md` |
| Cartella progetto | README.md con brief, agenti, stato, date | `/clients/[cliente]/progetti/[nome]/` |

---

## TEAMMATE #1 — STRATEGA
### Chief Strategy Officer AI

### LLM

| Parametro | Valore | Giustificazione |
|-----------|--------|-----------------|
| **Modello** | Opus 4 | Ragionamento strategico profondo: collegare dati di mercato, posizionamento, psicologia del buyer, creare strategie integrate. Un errore strategico si propaga a tutti i deliverable. |
| **Degradazione** | Mai per decisioni strategiche. Sonnet 4 accettabile SOLO per compilazione di template gia' strutturati con dati forniti. |

### Ruolo e confini

Lo Stratega e' il **cervello strategico** dell'agenzia. NON e' un esecutore — e' il decisore che guida la direzione. Lo Stratega:
- Definisce COSA fare e PERCHE' (posizionamento, target, messaging strategy, priorita' di mercato)
- Si coordina con gli operativi (Esploratore, Calcolatore, Voce) per prendere decisioni informate
- Spawna direttamente Esploratore (per dati), Calcolatore (per sostenibilita'), Voce (per test messaging), Sparring Partner (per stress-test)
- Produce raccomandazioni strategiche che l'Orchestratore traduce in task operativi
- Ha anche un ruolo chiave nel **pre-sales**: qualifica le opportunita', definisce la strategia di pricing, e guida la negoziazione commerciale

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| L1 — System Prompt | Identita', framework core (Hedgehog, De Veglia, JTBD, Playing to Win), regole PMI italiane, ruolo nel pre-sales | ~1.800 token |
| L2 — Working Context | Brief del cliente, ICP, dati competitor, posizionamento corrente | ~4.000 token |
| L3 — Knowledge Base (file) | Quick Reference strategy/ + Deep Knowledge on-demand, Piano Marketing proprietario, Metodo Snello, Brief Format, Framework Key Action, corsi Aliotta e Abate | On-demand via Read |

### Knowledge Skills (NUOVO v5.0)

| Quick Reference (sempre caricate) | Deep Knowledge (on-demand) |
|-----------------------------------|---------------------------|
| collins-hedgehog-quickref.md | collins-hedgehog-deep.md |
| deveglia-positioning-quickref.md | deveglia-positioning-deep.md |
| christensen-jtbd-quickref.md | christensen-jtbd-deep.md |
| lafley-playing-to-win-quickref.md | — |
| maurya-lean-canvas-quickref.md | — |
| rackham-spin-quickref.md | rackham-spin-deep.md |

### Tool

| Tool | Tipo | Uso |
|------|------|-----|
| **Task** | Nativo | Lanciare Esploratore (ricerche), Calcolatore (sostenibilita'), Voce (test messaging), Sparring Partner (stress-test) |
| **Read/Write/Edit** | Nativo | Accesso knowledge base, file di sistema, output |
| **WebSearch** | Nativo | Ricerche di mercato, trend, dati settoriali |
| **Google Drive** (MCP) | MCP | Documenti clienti e framework proprietari Sara |

### Skills Compendium
`pricing-strategy`, `marketing-psychology`, `marketing-ideas`, `launch-strategy`, `competitor-alternatives`, `gtm-growth-pmi`

### Output

| Tipo output | Formato | Template |
|-------------|---------|----------|
| Piano Marketing Strategico (piccole imprese) | Documento 15-25 pagine | Template proprietario Sara |
| Piano Marketing Strategico (strutturate) | Documento 30-40 pagine: 12 sessioni su 3 mesi | Template proprietario Sara |
| Brief Opportunita' | 1-2 pagine | Template Brief Format Sara |
| Analisi posizionamento | 5-8 pagine | Struttura custom |
| GTM plan | 8-12 pagine: CAPIRE → POSIZIONARE → LANCIARE → CRESCERE | Framework gtm-growth-pmi |
| Key Action plan | Tabella: Azione, Responsabile, KPI, Timeline, Rischi, Budget | Template Key Action Sara |
| Qualification scorecard (pre-sales) | 1 pagina: fit, budget, urgenza, decisore, verdict GO/NO-GO | Template custom |
| Strategia di pricing per deal | 1-2 pagine: value-based pricing, packaging, floor/target/stretch | Template custom |

---

## TEAMMATE #2 — ESPLORATORE
### Market Intelligence Officer AI

### LLM

| Parametro | Valore | Giustificazione |
|-----------|--------|-----------------|
| **Modello** | Sonnet 4 | Task prevalentemente di raccolta e strutturazione dati. Sonnet e' sufficiente e cost-effective. |
| **Upgrade** | Non automatico. Se serve interpretazione strategica, il dato torna allo Stratega che ragiona con Opus. |

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| L1 — System Prompt | Identita', fonti dati italiane, framework analisi (Porter, PESTEL, Battlecard), regole qualita' dati | ~1.200 token |
| L2 — Working Context | Brief di ricerca, dati raccolti finora, competitor identificati | ~5.000 token |
| L3 — KB (file) | Quick Reference analysis/ + Benchmark settoriali, report precedenti, template Battlecard | On-demand |

### Knowledge Skills (NUOVO v5.0)

| Quick Reference | Deep Knowledge |
|-----------------|---------------|
| porter-5forces-quickref.md | porter-5forces-deep.md |
| pestel-quickref.md | — |
| swot-quickref.md | — |
| battlecard-quickref.md | — |

### Tool

| Tool | Tipo | Uso |
|------|------|-----|
| **WebSearch** | Nativo | Ricerche di mercato, dati competitor, trend |
| **WebFetch** | Nativo | Leggere pagine web specifiche (siti competitor, report online) |
| **Read/Write/Edit** | Nativo | Salvare findings in path progetto o /system/findings/, accesso KB |
| **Google Drive** (MCP) | MCP | Accesso a report e dati esistenti nei Drive |

### Output

| Tipo output | Formato |
|-------------|---------|
| Report competitor | Markdown 5-10 pagine: overview, SWOT, Battlecard per competitor |
| Analisi di mercato | Markdown 8-15 pagine: TAM/SAM/SOM, trend, PESTEL, 5 Forze |
| Benchmark settoriale | Tabella comparativa con metriche chiave |
| Quick findings | 1-2 pagine sintesi per alimentare altri teammate |
| Dossier prospect (pre-sales) | 2-3 pagine: chi sono, fatturato, problemi, opportunita', decisori |

---

## TEAMMATE #3 — ARCHITETTO
### Proposal & Charter Builder AI

### LLM

| Parametro | Valore | Giustificazione |
|-----------|--------|-----------------|
| **Modello primario** | Opus 4 per charter e proposte complesse (devono persuadere, anticipare obiezioni, calibrare pricing) |
| **Degradazione** | Sonnet 4 per revisioni minori a charter gia' approvati, mini-proposte <€2.000, preventivi standard |

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| L1 — System Prompt | Identita', struttura Charter TTP (10 sezioni), SPIN framework, regole pricing | ~1.500 token |
| L2 — Working Context | Brief del cliente, pain point, budget indicativo, servizi richiesti, dati Esploratore, strategia pricing dello Stratega | ~4.000 token |
| L3 — KB (file) | `PROMPT_ProjectCharter_SaraQuinto.md`, template Charter v3, listino TTP, charter precedenti | On-demand |

### Tool, Output

| Tool | Tipo | Uso |
|------|------|-----|
| **Task** | Nativo | Lanciare Calcolatore (tabella costi), Legale (clausole) |
| **Read/Write/Edit** | Nativo | KB, template, output |
| **Google Drive** (MCP) | MCP | Charter precedenti come benchmark |
| **Skill `docx`** | Core | Generare charter come file .docx professionale |
| **Skill `pdf`** | Core | Versione PDF se richiesta |

| Tipo output | Formato |
|-------------|---------|
| Project Charter | .docx 8-15 pagine, 10 sezioni |
| Mini-proposta | .docx 3-5 pagine per progetti <€2.000 |
| Preventivo | .xlsx con breakdown costi per fase |
| Proposta di upsell/cross-sell | .docx 2-3 pagine per clienti esistenti |

---

## TEAMMATE #4 — NARRATORE
### Presentation & Visual Storytelling AI

### LLM: Sonnet 4 (upgrade Opus per presentazioni ad alto impatto — upgrade deciso dallo Stratega o Orchestratore)

| Aspetto | Dettaglio |
|---------|-----------|
| **L1** | Identita', principi Assertion-Evidence, Presentation Zen, regole slide design ~1.000 token |
| **L2** | Contenuti da presentare, brief presentazione, audience, obiettivo ~3.000 token |
| **L3** | Template slide, brand guidelines clienti, presentazioni precedenti. On-demand |
| **Tool** | Skill `pptx`, Read/Write/Edit, Google Drive (MCP) |
| **Output** | Presentazione strategica (.pptx 15-30 slide), Report visuale (.pptx 10-15), Pitch deck (.pptx 10-12) |

---

## TEAMMATE #5 — VOCE
### Content Director & Copywriter AI

### LLM

| Parametro | Valore | Giustificazione |
|-----------|--------|-----------------|
| **Modello primario** | Opus 4 per messaging strategy e copy di vendita (psicologia del buyer, creativita' controllata) |
| **Degradazione** | Sonnet 4 per copy operativo (post social, email routine, caption) dove il framework e' gia' definito |

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| L1 — System | Identita', framework copy (AIDA, PAS, StoryBrand, Schwartz), regole tono italiano | ~1.500 token |
| L2 — Working | Brand voice del cliente, messaging pillar, target persona, copy approvati | ~3.500 token |
| L3 — KB | Quick Reference marketing/ + brand guidelines, copy benchmark, principi copywriting | On-demand |

### Knowledge Skills (NUOVO v5.0)

| Quick Reference | Deep Knowledge |
|-----------------|---------------|
| aida-quickref.md | — |
| pas-quickref.md | — |
| miller-storybrand-quickref.md | miller-storybrand-deep.md |
| schwartz-awareness-quickref.md | schwartz-awareness-deep.md |
| content-pillars-quickref.md | — |

### Tool

| Tool | Tipo | Uso |
|------|------|-----|
| **Task** | Nativo | Lanciare Esploratore (VoC research), Editore (piano editoriale) |
| **Read/Write/Edit** | Nativo | KB, output |
| **WebSearch** | Nativo | Voice of customer (recensioni, forum, social) |
| **Google Drive** (MCP) | MCP | Brand guidelines, copy approvati |

### Skills Compendium
`copywriting`, `copy-editing`, `email-sequence`, `marketing-psychology`

### Output

| Tipo output | Formato |
|-------------|---------|
| Messaging architecture | Documento: Core message + 3-5 pillar + proof point |
| Copy landing page | HTML/Markdown: Hero → Problem → Solution → Social proof → CTA |
| Sequenza email | Markdown: 5-7 email con subject, body, CTA, timing |
| Tone of voice guide | Documento: Personalita', DO/DON'T, esempi per canale |
| Script obiezioni (pre-sales) | Markdown: obiezione → reframe → risposta → proof point |

---

## TEAMMATE #6-15 (INVARIATI — riferimenti aggiornati)

I teammate #6 (Editore), #7 (Regista), #8 (Misuratore), #9 (Calcolatore), #10 (Ottimizzatore), #11 (Formatore), #12 (Tecnico Web), #13 (Commercialista), #14 (Legale Digital), #15 (Admin) mantengono le stesse schede della v4.1 con i seguenti aggiornamenti trasversali:

**Aggiornamenti v5.0 per tutti i teammate #6-15:**
- Gli output di progetto vanno salvati in `/clients/[cliente]/progetti/[progetto]/findings/[agente]_[tipo].md` (non piu' in `/system/findings/` per i lavori legati a un progetto specifico)
- La SKILL.md segue il blueprint v5.0 a 8 sezioni (inclusi PREREQUISITI e CHECKLIST QUALITA')
- Il Task Tool Prompt ricevuto include la sezione KNOWLEDGE SKILLS con le Quick Reference pertinenti
- Il frontmatter della SKILL.md include i campi `knowledge_quickref:` e `knowledge_deep:`

Per le schede complete (LLM, Memoria, Tool, Framework, Output) di ciascun teammate #6-15, fare riferimento alla documentazione v4.1 Parte II che resta valida per tutti i dettagli non esplicitamente sovrascritti qui.

---

## TEAMMATE #16 — GOD MODE
### Final Quality Auditor AI

### LLM: Opus 4 (mai degradare — deve trovare errori che gli altri non hanno visto)

| Aspetto | Dettaglio |
|---------|-----------|
| **L1** | Identita', Checklist 7 Dimensioni, Pre-Mortem, criteri PASS/FAIL ~1.500 token |
| **L2** | Output da revisionare, brief originale, contesto progetto ~4.000 token |
| **L3** | Standard qualita' TTP, output precedenti come benchmark, **storico scorecards in /clients/[cliente]/progetti/[progetto]/findings/god_mode_scorecard.md** (NUOVO v5.0). On-demand |
| **Tool** | Read (output + brief), Write (scorecard) — il God Mode GIUDICA, non esegue |
| **Output** | Scorecard 7 Dimensioni (.md): PASS / PASS CON RISERVE / FAIL + problemi + raccomandazioni |

**Nota v5.0:** Il God Mode ora puo' consultare scorecards precedenti dello stesso progetto per verificare se i problemi segnalati sono stati risolti. I percorsi di output seguono la struttura per-progetto.

---

## TEAMMATE #17 — ARTIGIANO
### Prompt Engineer, Skill Developer & Knowledge Builder AI

### LLM: Sonnet 4

**Nota sulla scelta LLM:** Nella v4.0 era Opus ("scrivere prompt richiede meta-cognizione"). In pratica, il prompt engineering beneficia enormemente da iterazione e testing, non dal modello piu' costoso. Sonnet + eval loop (scrivi → testa → valuta → riscrivi) produce risultati equivalenti a Opus a costo molto inferiore.

### Ruolo rivisto (v5.0) — 2 MODALITA'

**Modalita' 1 — Skill Maintenance (invariata):** Costruisce e aggiorna le SKILL.md dei teammate seguendo il blueprint v5.0 a 8 sezioni. Le SKILL.md non contengono framework embedded ma referenziano le Quick Reference tramite frontmatter.

**Modalita' 2 — Knowledge Processing (NUOVO v5.0):** Processa materiali (libri, corsi, metodologie proprietarie) trasformandoli in file Knowledge Skills a 2 livelli:
1. Sara fornisce il materiale (PDF, note, trascrizione)
2. Artigiano analizza e identifica i concetti chiave
3. Artigiano propone a Sara la struttura della Quick Reference e Deep Knowledge
4. Sara approva/modifica
5. Artigiano produce i file e li salva in `/skills/knowledge/[categoria]/`

**Priorita' di processamento:**
1. Metodologie proprietarie di Sara (massima priorita')
2. Corsi seguiti (Aliotta, Abate, ecc.)
3. Libri di reference (posizionamento, copy, strategia)

### Memoria

| Livello | Contenuto | Dimensione |
|---------|-----------|------------|
| **L1** | Identita', Blueprint SKILL.md v5.0 (8 sezioni), formato Quick Reference (max 120 righe), formato Deep Knowledge (max 350 righe), Eval Loop, anti-pattern | ~1.800 token |
| **L2** | SKILL.md o Knowledge file in lavorazione, risultati test, problemi | ~3.500 token |
| **L3** | SKILL.md esistenti, Knowledge files esistenti, documentazione Claude, prompt engineering guide. On-demand |

### Tool

| Tool | Tipo | Uso |
|------|------|-----|
| Read/Write/Edit | Nativo | Creare/modificare SKILL.md e Knowledge files |
| Task | Nativo | Testare SKILL.md spawnando teammate |
| Bash | Nativo | Validazione formale (conteggio token, formato) |
| WebSearch | Nativo | Ricerca informazioni per compilare Knowledge files |

### Skills Compendium
`prompt-engineer`, `prompt-engineering`, `skill-creator`, `context-window-management`

### Output

| Tipo output | Formato | Destinazione |
|-------------|---------|-------------|
| SKILL.md teammate | Markdown (max 1.500 token) | `/skills/[teammate]/SKILL.md` |
| Quick Reference | Markdown (max 120 righe) | `/skills/knowledge/[categoria]/[nome]-quickref.md` |
| Deep Knowledge | Markdown (max 350 righe) | `/skills/knowledge/[categoria]/[nome]-deep.md` |
| Eval report | Markdown: 5 test → valutazione | allegato al SKILL.md |
| Changelog | Markdown | allegato al SKILL.md |

---

## TEAMMATE #18-21 (INVARIATI)

I teammate #18 (Economo), #19 (Manutentore), #20 (Mentore), #21 (Sparring Partner) mantengono le stesse schede della v4.1 con gli aggiornamenti trasversali v5.0 descritti per i teammate #6-15.

**Note specifiche v5.0:**
- **Economo (#18):** Aggiunge al suo audit l'analisi delle Knowledge files (Quick Reference troppo lunghe, Deep Knowledge non utilizzate). Puo' spawnare l'Artigiano per ottimizzazione.
- **Manutentore (#19):** Gestisce anche la cartella `/skills/knowledge/` e `/operations/procedure/`. Verifica che i file Knowledge siano aggiornati (header con data ultimo aggiornamento).
- **Sparring Partner (#21):** Opus 4 fisso, mai degradare. Trova falle logiche, bias nascosti, assunzioni non verificate.

---

# PARTE II-B — BLUEPRINT SKILL.md (v5.0)

Ogni teammate viene implementato come una SKILL.md in Claude Code. Questa sezione definisce la struttura obbligatoria.

## STRUTTURA OBBLIGATORIA DI UNA SKILL.md (v5.0 — 8 SEZIONI)

```markdown
---
# METADATA (usata da Claude Code per il routing)
name: [nome-teammate]
description: [1 frase — quando attivare questo agente]
model: [opus-4/sonnet-4/haiku-4.5]
tools: [lista tool consentiti]
knowledge_quickref: [lista Quick Reference assegnate — es: "porter-5forces, pestel, battlecard"]
knowledge_deep: [lista Deep Knowledge disponibili — es: "porter-5forces, swot"]
---

# [NOME TEAMMATE] — [Ruolo]

## IDENTITA' CORE
[Chi sei, cosa fai, qual e' la tua missione. MAX 3 frasi.]

## AUTONOMIA
- Puoi fare autonomamente: [lista azioni]
- Devi chiedere conferma a Sara per: [lista azioni]
- NON puoi mai: [lista divieti]

## PREREQUISITI (NUOVO v5.0)
Prima di iniziare qualsiasi task, verifica che siano presenti:
- [ ] [Input obbligatorio 1 — es: brief cliente]
- [ ] [Input obbligatorio 2 — es: dati competitor se task e' posizionamento]
- [ ] [Input obbligatorio 3]
Se un prerequisito manca, FERMA e segnala nel report. Non procedere con dati incompleti.

## FRAMEWORK OPERATIVI
[Per ogni framework: nome, quando usarlo, i passaggi chiave. NO teoria — solo operativo.
I framework dettagliati sono nelle Quick Reference — qui solo il riferimento.]

### [Nome Framework 1]
Quando: [trigger]
Quick Reference: /skills/knowledge/[categoria]/[nome]-quickref.md
Passaggi chiave:
1. [step]
2. [step]
3. [step]
Output: [cosa produce]

## OUTPUT STANDARD
[Tabella: tipo output → formato → struttura → destinazione file]

| Output | Formato | Struttura | Destinazione |
|--------|---------|-----------|-------------|
| [tipo] | [md/docx/xlsx] | [sezioni] | /clients/[cliente]/progetti/[progetto]/findings/[agente]_[tipo].md |

## CHECKLIST QUALITA' (NUOVO v5.0)
Prima di consegnare l'output, verifica:
- [ ] [Criterio 1 — es: Tutti i dati hanno una fonte citata]
- [ ] [Criterio 2 — es: L'output segue la struttura richiesta]
- [ ] [Criterio 3 — es: Non contiene raccomandazioni fuori scope]
- [ ] Output salvato nel path corretto
- [ ] Report summary pronto per chi ti ha spawnato

## REGOLE
1. Salva findings su file dopo ogni output significativo.
2. Se superi 15 tool calls, salva checkpoint in /system/progress/ e segnala.
3. Usa il file system come disco, il contesto come RAM.
4. [Regole specifiche del teammate]

## RELAZIONI
- Ricevi task da: [chi ti spawna]
- Puoi spawnare: [chi puoi lanciare via Task tool, se hai il tool]
- I tuoi output alimentano: [chi usa i tuoi deliverable]
```

## REGOLE PER LA SCRITTURA DELLE SKILL.md (v5.0)

1. **Budget token L1 (system prompt):** ogni SKILL.md deve stare sotto i 1.500 token (ridotto da 2.000). I framework dettagliati sono nelle Quick Reference esterne, non embedded.
2. **Framework come riferimenti, non come ricette embedded.** La SKILL.md dice "usa la Quick Reference X" — non copia il contenuto della Quick Reference.
3. **Output con path espliciti per-progetto.** L'agente deve sapere di salvare in `/clients/[cliente]/progetti/[progetto]/findings/`.
4. **Regole specifiche > regole generiche.** "Non inventare dati" e' meglio di "Sii accurato".
5. **Le relazioni chiudono il cerchio.** Ogni agente sa da chi riceve input e a chi passa output.
6. **(NUOVO v5.0) PREREQUISITI sono obbligatori.** Ogni SKILL.md deve elencare gli input necessari per lavorare. Se mancano, l'agente si ferma.
7. **(NUOVO v5.0) CHECKLIST QUALITA' e' obbligatoria.** Riduce il carico di review per il God Mode.
8. **(NUOVO v5.0) Il frontmatter include knowledge_quickref e knowledge_deep.** L'Orchestratore li legge per compilare la sezione KNOWLEDGE SKILLS del Task Tool Prompt.

---

# PARTE II-C — SISTEMA KNOWLEDGE A 2 LIVELLI (NUOVO v5.0)

## Architettura

Il knowledge system ha due livelli:

**Quick Reference (max 120 righe):**
- Sempre caricata in contesto dall'agente (step READ del loop)
- Contiene: YAML frontmatter + Quando usare + Template operativo + Domande guida + Output atteso
- Esempio: `schwartz-awareness-quickref.md` con i 5 livelli di consapevolezza e come usarli nel copy

**Deep Knowledge (max 350 righe):**
- Caricata on-demand solo quando il task richiede un approfondimento
- Contiene: Teoria completa + Varianti + Casi studio + Anti-pattern + Interazioni con altri framework
- Esempio: `schwartz-awareness-deep.md` con le tecniche avanzate per ogni livello

## Struttura file system

```
/skills/knowledge/
├── strategy/
│   ├── collins-hedgehog-quickref.md
│   ├── collins-hedgehog-deep.md
│   ├── deveglia-positioning-quickref.md
│   ├── deveglia-positioning-deep.md
│   ├── lafley-playing-to-win-quickref.md
│   ├── maurya-lean-canvas-quickref.md
│   ├── christensen-jtbd-quickref.md
│   ├── christensen-jtbd-deep.md
│   ├── rackham-spin-quickref.md
│   └── rackham-spin-deep.md
├── marketing/
│   ├── aida-quickref.md
│   ├── pas-quickref.md
│   ├── miller-storybrand-quickref.md
│   ├── miller-storybrand-deep.md
│   ├── schwartz-awareness-quickref.md
│   ├── schwartz-awareness-deep.md
│   └── content-pillars-quickref.md
├── analysis/
│   ├── porter-5forces-quickref.md
│   ├── porter-5forces-deep.md
│   ├── pestel-quickref.md
│   ├── swot-quickref.md
│   ├── battlecard-quickref.md
│   └── mcclure-aarrr-quickref.md
├── operations/
│   ├── allen-gtd-quickref.md
│   ├── eisenhower-quickref.md
│   ├── raci-quickref.md
│   ├── snowden-cynefin-quickref.md
│   └── deming-pdca-quickref.md
├── quality/
│   ├── klein-premortem-quickref.md
│   ├── munger-inversion-quickref.md
│   ├── steelman-quickref.md
│   └── ttp-7dimensions-quickref.md
├── business/
│   ├── michalowicz-pumpkin-quickref.md
│   ├── gerber-emyth-quickref.md
│   ├── michalowicz-profit-first-quickref.md
│   └── staircase-of-value-quickref.md
└── corsi_sara/
    ├── aliotta-positioning-quickref.md
    ├── aliotta-positioning-deep.md
    ├── abate-strategy-quickref.md
    └── abate-strategy-deep.md
```

## Regole del Knowledge System

1. **Quick Reference massimo 120 righe.** Se sfora, taglia — il dettaglio va nella Deep Knowledge.
2. **Deep Knowledge massimo 350 righe.** Se sfora, probabilmente copre troppi concetti — spezza in 2.
3. **Un framework = un file.** Mai combinare piu' framework in un file.
4. **Solo l'Artigiano (Modalita' 2) crea Knowledge files.** Gli altri agenti li usano, non li modificano.
5. **Header con data ultimo aggiornamento.** Il Manutentore controlla periodicamente.
6. **Safety check nel loop agente:** Se la Quick Reference indicata nel prompt non esiste, l'agente procede con le sue conoscenze base e segnala l'assenza nel report.

---

# PARTE III — FLUSSI OPERATIVI

## 3.1 CATALOGO FLUSSI (NUOVO v5.0)

I flussi operativi sono codificati in `/operations/procedure/catalogo_flussi.md` e nei file individuali. L'Orchestratore consulta il catalogo per determinare quale procedura seguire.

| # | Flusso | Trigger | Agenti chiave | Output principale |
|---|--------|---------|---------------|-------------------|
| F01 | Piano Marketing | "Preparami un piano marketing per [cliente]" | Esploratore → Stratega → Voce → Architetto → God Mode | Piano completo + Charter |
| F02 | Campagna Content | "Crea una campagna content per [cliente/prodotto]" | Voce → Editore → Narratore | Messaging + PED + Copy |
| F03 | Lancio Prodotto | "Devo lanciare [prodotto/servizio]" | Stratega → Esploratore → Voce → Editore → Tecnico Web | GTM plan + Content + Landing |
| F04 | Pre-Sales | "Ho un lead: [prospect]" / "Qualifica questo contatto" | Esploratore → Stratega → Voce → Architetto | Dossier → Qualification → Charter |
| F05 | Audit & Ottimizzazione | "Analizza/migliora [sito/processo/funnel]" | Misuratore → Ottimizzatore → Tecnico Web | Audit report + Action plan |
| F06 | Business Planning | "Quanto mi costa fare X?" / "E' sostenibile?" | Calcolatore → Commercialista → Stratega | BP + Proiezioni + Parere |
| F07 | Formazione | "Prepara un corso/workshop su [topic]" | Formatore → Narratore → (Voce per copy) | Programma + Slide + Materiali |
| F08 | Coaching Sara | "Ho bisogno di ragionare su..." / "Aiutami a decidere..." | Mentore e/o Sparring Partner | Session notes + Action plan |

### PROTOCOLLO RICHIESTA NON MAPPATA

Se la richiesta di Sara non rientra in nessun flusso del catalogo:
1. L'Orchestratore analizza la richiesta e propone un piano d'azione contestualizzato
2. Presenta a Sara: "Non ho un flusso standard per questa richiesta. Propongo di procedere cosi': [piano]. Va bene?"
3. Sara decide: (a) OK procedi, (b) Modifica il piano, (c) **Mettilo a sistema** — mappalo come nuovo flusso nel catalogo
4. Se opzione (c): l'Orchestratore codifica il flusso in `/operations/procedure/flussi_custom/` e aggiorna il catalogo

## 3.2 FLUSSO PROGETTO CLIENTE (RIVISTO v5.0)

```
Sara: "Preparami la strategia per il cliente Acme, settore pet food"

1. ORCHESTRATORE riceve la richiesta
   → Consulta il Catalogo Flussi → identifica F01 (Piano Marketing)
   → Chiede a Sara il nome del progetto
   → Crea /clients/acme/progetti/lancio_bio/ con README.md
   → Aggiorna sessione.md
   → Crea task_list:
     T001: Esploratore → ricerca mercato pet food
     T002: Esploratore → analisi 5 competitor
     T003: Stratega → posizionamento (dipende da T001, T002)
     T004: Voce → messaging (dipende da T003)
     T005: Architetto → charter (dipende da T003, T004)

2. ORCHESTRATORE spawna ESPLORATORE via Task tool
   Prompt: [Task Tool Prompt Protocol v5.0 con 8 sezioni, inclusa KNOWLEDGE SKILLS
            con Quick Reference: porter-5forces, pestel, battlecard
            Output in /clients/acme/progetti/lancio_bio/findings/esploratore_*.md]
   → Esploratore legge Quick Reference, lavora (4-step loop), scrive output
   → Restituisce summary all'Orchestratore via risultato Task tool

3. ORCHESTRATORE aggiorna task_list (T001=DONE, T002=DONE)
   → Spawna STRATEGA via Task tool
   Prompt: [Task Tool Prompt Protocol v5.0 con KNOWLEDGE SKILLS:
            collins-hedgehog, deveglia-positioning, christensen-jtbd
            Input: path dei findings Esploratore
            Output: /clients/acme/progetti/lancio_bio/findings/stratega_positioning.md]
   → Stratega legge Quick Reference + findings, applica framework
   → Se ha bisogno di dati aggiuntivi, spawna Esploratore come suo subagent
   → Restituisce summary all'Orchestratore

4. ORCHESTRATORE aggiorna task_list (T003=DONE)
   → Spawna in PARALLELO:
   Task tool → Voce (con KNOWLEDGE SKILLS + path positioning)
   Task tool → Calcolatore (tabella costi — indipendente dal messaging)

5. VOCE produce messaging → scrive in /clients/acme/progetti/lancio_bio/findings/voce_messaging.md
   CALCOLATORE produce costi → scrive in /clients/acme/progetti/lancio_bio/findings/calcolatore_costi.xlsx

6. ORCHESTRATORE spawna ARCHITETTO
   Prompt: [path tutti i findings + brief]
   → Architetto produce charter in /clients/acme/charter.docx

7. ORCHESTRATORE spawna GOD MODE
   Prompt: [charter + brief originale + scorecards precedenti se esistono]
   → God Mode restituisce scorecard in /clients/acme/progetti/lancio_bio/findings/god_mode_scorecard.md

8. Se PASS → ORCHESTRATORE produce SINTESI_FINALE.md e consegna a Sara
   Se FAIL → ORCHESTRATORE presenta i problemi a Sara con opzioni
   → Aggiorna README.md del progetto con stato finale
```

## 3.3 FLUSSO PRE-SALES & NEGOZIAZIONE COMMERCIALE

Questo flusso copre l'intero ciclo di vendita, dalla prima opportunita' alla firma del contratto. Invariato rispetto a v4.1 con l'aggiornamento che gli output vanno in `/clients/[prospect]/presales/` e il Task Tool Prompt usa il formato v5.0 a 8 sezioni.

### Fase 1 — QUALIFICAZIONE LEAD
### Fase 2 — PREPARAZIONE DISCOVERY CALL
### Fase 3 — POST-DISCOVERY & STRATEGIA DI PRICING
### Fase 4 — PROPOSTA & CHIUSURA
### Fase 5 — FOLLOW-UP (per deal non chiusi)

(Flussi dettagliati invariati rispetto a v4.1 — vedi sezioni 3.2 Fasi 1-5 del documento v4.1 per i diagrammi completi. L'unica modifica e' l'uso del Task Tool Prompt Protocol v5.0 a 8 sezioni.)

## 3.4 FLUSSO ANTI-CONTEXT ROT (SEMPLIFICATO)

```
REGOLA AUTOMATICA (embedded in ogni agente via Task Tool Prompt Protocol v5.0):

Ogni agente, durante il lavoro:
1. Salva findings su file dopo ogni output significativo (Regola 1)
2. Se supera 15 tool calls → checkpoint in /system/progress/ (Regola 2)
3. Legge solo i dati che servono, non interi documenti (Regola 3)

AUDIT PERIODICO (mensile, attivato da Sara o dall'Orchestratore):
→ Orchestratore spawna Economo
→ Economo analizza: costi token per teammate, SKILL.md troppo lunghe, Task Tool Prompt
  con contesto eccessivo, Knowledge files non utilizzate o troppo lunghe
→ Economo produce report con raccomandazioni
→ Se servono modifiche alle SKILL.md o Knowledge files → Economo spawna Artigiano
```

---

# PARTE IV — RIEPILOGO COMPLETO

## 4.1 ALLOCAZIONE LLM

| Categoria | Modello | Teammate | Tot. |
|-----------|---------|----------|------|
| **Opus fisso** | Opus 4 — mai degradare | Orchestratore, Stratega, God Mode, Sparring Partner | 4 |
| **Dual-mode** | Opus strategia / Sonnet esecuzione | Voce, Architetto, Calcolatore, Mentore | 4 |
| **Sonnet fisso** | Sonnet 4 | Esploratore, Narratore, Editore, Regista, Misuratore, Ottimizzatore, Formatore, Tecnico Web, Commercialista, Legale, Economo, Manutentore, Artigiano | 13 |
| **Haiku** | Haiku 4.5 | Admin | 1 |

## 4.2 ARCHITETTURA MEMORIA (v5.0)

| Livello | Contenuto | Budget token | Persistenza |
|---------|-----------|-------------|-------------|
| **L1 — System** | Identita', framework core, regole, anti-context rot | 800-1.500 (ridotto da 2.000 grazie a Knowledge esternalizzate) | Sempre in contesto |
| **L1b — Quick Reference** | Framework operativi via /skills/knowledge/ | max 120 righe per file, caricati su Read | Per sessione (caricati a step 1 del loop) |
| **L2 — Working** | Progetto attivo, task, dati correnti | 2.000-5.000 | Per sessione |
| **L3 — Knowledge Base** | Template, storico, benchmark, Deep Knowledge | Illimitato (file) | Persistente su disco |
| **Shared** | Task list, findings, progress, clients, sessione | N/A (file) | Persistente, condiviso |

## 4.3 TOOL PER TEAMMATE (invariato da v4.1)

| Tool | Tipo | Usato da |
|------|------|---------|
| **Task** (spawn subagent) | Nativo | Orchestratore, Stratega, Architetto, Voce, Ottimizzatore, Calcolatore, Mentore, SP, Economo, Artigiano |
| **Read/Write/Edit** | Nativo | TUTTI |
| **WebSearch** | Nativo | Esploratore, Stratega, Voce, Tecnico Web, Legale, SP |
| **WebFetch** | Nativo | Esploratore, Tecnico Web, Ottimizzatore |
| **Bash** | Nativo | Calcolatore, Misuratore, Tecnico Web, Commercialista, Economo, Manutentore, Artigiano |
| **Glob/Grep** | Nativo | Orchestratore, Manutentore, Artigiano |
| **Google Drive** (MCP) | MCP | Orchestratore, Stratega, Esploratore, Architetto, Narratore, Editore, Regista, Tecnico Web, Admin, Manutentore |
| **Google Calendar** (MCP) | MCP | Orchestratore, Regista, Commercialista, Admin |
| **Gmail** (MCP) | MCP | Orchestratore, Admin |
| **Skill `docx`** | Core | Architetto, Formatore, Legale |
| **Skill `pptx`** | Core | Narratore, Formatore |
| **Skill `xlsx`** | Core | Calcolatore, Misuratore, Commercialista, Editore, Regista |
| **Skill `pdf`** | Core | Architetto |
| **Skill `business-plan-excel`** | Core | Calcolatore |

## 4.4 SKILLS COMPENDIUM PER TEAMMATE (invariato da v4.1)

| # | Teammate | Skills Compendium | Tot. |
|---|----------|------------------|------|
| 0 | Orchestratore | — | 0 |
| 1 | Stratega | `pricing-strategy`, `marketing-psychology`, `marketing-ideas`, `launch-strategy`, `competitor-alternatives`, `gtm-growth-pmi` | 6 |
| 2 | Esploratore | `competitor-alternatives`, `marketing-psychology` | 2 |
| 3 | Architetto | `copywriting`, `pricing-strategy` | 2 |
| 4 | Narratore | — | 0 |
| 5 | Voce | `copywriting`, `copy-editing`, `email-sequence`, `marketing-psychology` | 4 |
| 6 | Editore | `social-content`, `content-creator`, `geo-fundamentals` | 3 |
| 7 | Regista | `product-manager-toolkit` | 1 |
| 8 | Misuratore | `analytics-tracking`, `ab-test-setup` | 2 |
| 9 | Calcolatore | `pricing-strategy` | 1 |
| 10 | Ottimizzatore | `page-cro`, `signup-flow-cro`, `form-cro`, `popup-cro`, `onboarding-cro`, `referral-program`, `kaizen` | 7 |
| 11 | Formatore | — | 0 |
| 12 | Tecnico Web | `seo-audit`, `seo-fundamentals`, `schema-markup`, `programmatic-seo`, `analytics-tracking`, `email-systems`, `geo-fundamentals`, `zapier-make-patterns` | 8 |
| 13 | Commercialista | — | 0 |
| 14 | Legale Digital | — | 0 |
| 15 | Admin | — | 0 |
| 16 | God Mode | — | 0 |
| 17 | Artigiano | `prompt-engineer`, `prompt-engineering`, `skill-creator`, `context-window-management` | 4 |
| 18 | Economo | `context-window-management`, `prompt-caching` | 2 |
| 19 | Manutentore | `file-organizer` | 1 |
| 20 | Mentore | — | 0 |
| 21 | Sparring Partner | — | 0 |

## 4.5 COSTI STIMATI

| Voce | v4.0 | v4.1 | v5.0 (stima) |
|------|------|------|-------------|
| Opus 4 (fisso) | $150-300 (11 teammate) | $100-180 (4 teammate) | $100-180 (invariato) |
| Opus 4 (dual-mode) | — | $30-80 | $30-80 (invariato) |
| Sonnet 4 | $50-100 (10 teammate) | $55-110 (13 teammate) | $50-100 (ridotto: SKILL.md piu' snelle = meno token L1) |
| Haiku 4.5 | $5-15 | $5-15 | $5-15 (invariato) |
| Overhead comunicazione | $20-40 | $0 | $0 (invariato) |
| Tool esterni | $25-50 | $25-50 | $25-50 (invariato) |
| **TOTALE** | **$230-465/mese** | **$215-435/mese** | **$210-425/mese** |

**Nota v5.0:** Il risparmio principale viene dalla riduzione del budget L1 (da max 2.000 a max 1.500 token per SKILL.md) grazie all'esternalizzazione dei framework nelle Quick Reference. Il costo delle Quick Reference caricate (step READ) e' compensato dalla riduzione del contesto iniziale.

## 4.6 ROADMAP (RIVISTA v5.0)

**Sprint 0 (Settimana 1):** Infrastruttura
- Creare `/system/` con task_list.md, sessione.md, findings/, progress/
- Creare `/clients/` con struttura tipo
- Creare `/skills/knowledge/` con sottocartelle per categoria
- Creare `/operations/procedure/` con catalogo_flussi.md e 8 file procedura
- Costruire Artigiano (primo agente — scrive le SKILL.md e i Knowledge files)
- Definire il Task Tool Prompt Protocol v5.0 come reference document
- Creare le Quick Reference prioritarie (framework usati da piu' agenti)

**Sprint 1 (Settimane 2-3):** Core strategico
- Orchestratore + Stratega + God Mode
- Testare il flusso hub-and-spoke base con Task Tool Prompt v5.0
- Testare error handling con casi di fallimento simulati
- Verificare il safety check delle Knowledge Skills

**Sprint 2 (Settimane 4-5):** Pre-sales + proposte
- Architetto + Esploratore + Calcolatore
- Implementare il flusso pre-sales completo (F04)
- Testare l'output persistence per-progetto con un prospect reale

**Sprint 3 (Settimane 6-7):** Content
- Voce + Editore + Narratore
- Testare flusso progetto cliente (F01) end-to-end
- Artigiano processa prime Knowledge files da corsi Sara (Modalita' 2)

**Sprint 4 (Settimane 8-9):** Execution
- Regista + Misuratore + Tecnico Web + Ottimizzatore
- Testare con progetto reale in corso

**Sprint 5 (Settimane 10-11):** Support
- Commercialista + Legale + Admin + Formatore
- Integrare nel flusso operativo

**Sprint 6 (Settimana 12):** Advisory & tuning
- Mentore + Sparring Partner + Economo + Manutentore
- Audit completo del sistema (incluso Knowledge System)
- Prima sessione Economo (baseline costi + audit Knowledge files)

---

# PARTE IV-B — MODELLO DI INTERAZIONE SARA ↔ SISTEMA (v5.0)

## COME SARA USA IL SISTEMA

Sara interagisce SOLO con l'Orchestratore. Non spawna mai agenti direttamente. L'Orchestratore e' il suo unico punto di accesso.

### Tipologie di richiesta e risposta del sistema

| Sara scrive... | L'Orchestratore fa... |
|----------------|----------------------|
| "Preparami la strategia per il cliente Acme, settore pet food" | Consulta Catalogo Flussi → F01 (Piano Marketing): decompone → spawna → coordina → consegna |
| "Ho un lead interessante: [nome]. Qualificalo." | Catalogo → F04 (Pre-Sales Fase 1): Esploratore + Stratega → qualification scorecard |
| "Domani ho una discovery call con [prospect]. Preparami." | Catalogo → F04 (Pre-Sales Fase 2): Stratega → discovery prep con domande SPIN |
| "Il cliente Acme vuole un piano editoriale per Q2" | Catalogo → F02 (Campagna Content): spawna Editore (con input da Voce) |
| "Quanto mi costa fare il progetto X? E quanto mi resta netto?" | Catalogo → F06 (Business Planning): Calcolatore + Commercialista in parallelo |
| "Rivedi questo charter prima che lo mandi" | Spawna God Mode → scorecard → feedback a Sara |
| "Ho bisogno di ragionare su una decisione importante" | Catalogo → F08 (Coaching): Mentore o Sparring Partner |
| "Come stanno andando i progetti?" | Legge task_list + progress files + sessione.md → produce status report |
| "Questa idea ha senso?" | Spawna Sparring Partner → stress test → scorecard |
| "Processa questo libro/corso in knowledge skills" | Spawna Artigiano (Modalita' 2) → Knowledge Processing interattivo |
| Richiesta non nel catalogo | Protocollo Richiesta Non Mappata: propone piano → Sara decide → opzionalmente si mappa |

### Regole di interazione

1. **Sara non deve conoscere i nomi degli agenti.** L'Orchestratore traduce.
2. **Sara puo' chiedere un agente specifico** se lo desidera.
3. **Ogni deliverable torna a Sara per approvazione** prima di essere usato nel flusso successivo, TRANNE quando Sara ha pre-approvato un flusso completo.
4. **L'Orchestratore non sommerge Sara di domande.** Chiede solo per: decisioni strategiche, approvazione deliverable, risoluzione errori, richieste non mappate.
5. **I deliverable vengono presentati con un summary** — mai il file raw.

### Flusso decisionale: quando l'Orchestratore chiede a Sara

```
RICHIESTA DI SARA
│
├─ E' mappata nel Catalogo Flussi?
│  → SI: segui la procedura
│  → NO: Protocollo Richiesta Non Mappata
│
├─ L'Orchestratore puo' decidere da solo?
│  (routing, sequencing, quale agente, quale flusso)
│  → SI: procede autonomamente
│  → NO: chiede a Sara
│
├─ Serve una decisione strategica?
│  → Lo Stratega produce opzioni → l'Orchestratore le presenta a Sara → Sara decide
│
├─ Un agente ha prodotto un deliverable?
│  → Se Sara ha pre-approvato il flusso: procede al passo successivo
│  → Se non pre-approvato: presenta summary a Sara, attende OK
│
├─ Un agente ha fallito?
│  → Retry automatico (1 volta)
│  → Se fallisce ancora: presenta il problema a Sara con opzioni
│
└─ La richiesta e' ambigua?
   → Chiede chiarimento PRIMA di spawnare qualsiasi agente
```

---

# PARTE IV-C — STRUTTURA KNOWLEDGE BASE (v5.0)

## ORGANIZZAZIONE FILE SYSTEM COMPLETA

```
/knowledge_base/
├── frameworks/                    # Framework proprietari di Sara
│   ├── piano_marketing_piccole_imprese.md
│   ├── piano_marketing_strutturate.md
│   ├── metodo_snello.md
│   ├── brief_format.md
│   ├── key_action_template.md
│   ├── sprint_ttp.md
│   └── project_charter_template.md
├── corsi/
│   ├── aliotta_positioning.md
│   ├── abate_strategy.md
│   └── [altri_corsi].md
├── brand_guidelines/[cliente]/
│   ├── brand_guide.md
│   ├── tone_of_voice.md
│   └── assets/
├── templates/
│   ├── battlecard_template.md
│   ├── ped_template.xlsx
│   ├── dashboard_template.xlsx
│   ├── contratto_servizio_template.docx
│   ├── privacy_policy_template.md
│   ├── nda_template.docx
│   └── fattura_template.md
├── benchmark/
│   ├── benchmark_social_italia.md
│   ├── benchmark_email.md
│   ├── benchmark_cro.md
│   └── [settore]_benchmark.md
├── storico/
│   ├── piani_marketing/
│   ├── charter/
│   ├── analisi_competitor/
│   └── coaching_sessions/
└── ttp_internal/
    ├── listino_servizi.md
    ├── processi_interni.md
    ├── parametri_fiscali_sara.md
    ├── obiettivi_annuali.md
    └── AI_Agency_TTP_v5.0_Swarm_Architecture.md

/skills/
├── [nome_teammate]/SKILL.md        # 22 SKILL.md (una per teammate)
└── knowledge/                       # (NUOVO v5.0) Sistema a 2 livelli
    ├── strategy/
    ├── marketing/
    ├── analysis/
    ├── operations/
    ├── quality/
    ├── business/
    └── corsi_sara/

/operations/                         # (NUOVO v5.0) Catalogo Flussi
└── procedure/
    ├── catalogo_flussi.md
    └── flussi_custom/

/system/
├── task_list.md
├── sessione.md                      # (NUOVO v5.0)
├── decisions_log.md
├── findings/
└── progress/

/clients/[nome_cliente]/
├── brief.md
├── positioning.md
├── messaging.md
├── charter.docx
├── presales/
├── progetti/                        # (NUOVO v5.0) Output persistence
│   └── [nome_progetto]/
│       ├── README.md
│       ├── findings/
│       └── SINTESI_FINALE.md
└── deliverables/
```

## MAPPA KB PER TEAMMATE (v5.0)

| Teammate | Path KB principale | Knowledge Skills (Quick Ref) |
|----------|--------------------|-----------------------------|
| Stratega | `/knowledge_base/frameworks/` | strategy/*.quickref.md |
| Esploratore | `/knowledge_base/benchmark/` + templates | analysis/*.quickref.md |
| Architetto | `/knowledge_base/frameworks/` + templates | — (usa KB diretta) |
| Voce | `/knowledge_base/brand_guidelines/[cliente]/` | marketing/*.quickref.md |
| Editore | `/knowledge_base/templates/` + benchmark | marketing/content-pillars |
| Calcolatore | `/knowledge_base/templates/` + ttp_internal | — |
| Commercialista | `/knowledge_base/ttp_internal/` | — |
| Legale | `/knowledge_base/templates/` | — |
| God Mode | `/knowledge_base/storico/` + progetti findings | quality/*.quickref.md |
| Mentore | `/knowledge_base/storico/coaching_sessions/` + ttp_internal | business/*.quickref.md |
| Ottimizzatore | `/knowledge_base/benchmark/` | operations/deming-pdca |

## REGOLE DI GESTIONE KB

1. **La KB e' L3 — mai caricata in contesto.** Gli agenti la leggono on-demand con Read tool.
2. **Solo Sara e il Manutentore aggiornano la KB.** Gli agenti non scrivono nella KB — scrivono in /clients/ o /system/findings/.
3. **I file KB hanno un header con data ultimo aggiornamento.** Se un file e' piu' vecchio di 6 mesi, il Manutentore lo segnala per revisione.
4. **Lo storico viene anonimizzato.** I piani e charter precedenti usati come reference NON contengono dati sensibili dei clienti.
5. **(NUOVO v5.0) Le Knowledge files in /skills/knowledge/ seguono le regole del Knowledge System** (sezione II-C): max 120 righe per Quick Reference, max 350 per Deep Knowledge.

---

# PARTE V — AVVOCATO DEL DIAVOLO (v5.0)

### Cosa e' migliorato rispetto alla v4.1

1. **Knowledge System a 2 livelli.** I framework non sono piu' duplicati nelle SKILL.md. Un aggiornamento al framework si propaga automaticamente a tutti gli agenti che lo usano. Le SKILL.md sono piu' snelle (max 1.500 token vs. 2.000).

2. **Input Validation (PREREQUISITI).** Ogni agente verifica di avere gli input necessari PRIMA di lavorare. Riduce drasticamente il lavoro sprecato su dati incompleti.

3. **Quality Checklist.** L'auto-verifica pre-consegna riduce il carico di review per il God Mode e migliora la qualita' media del primo output.

4. **Catalogo Flussi.** Le procedure operative sono codificate, non improvvisate. Il protocollo per richieste non mappate permette crescita organica del catalogo.

5. **Output persistence per-progetto.** Tracciabilita' completa: chi ha prodotto cosa, quando, per quale progetto. Il God Mode puo' fare audit longitudinali.

6. **Sessione.md.** Ripresa sessione piu' rapida — l'Orchestratore sa dove eravamo senza rileggere tutta la task_list.

7. **Artigiano Modalita' 2 (Knowledge Processing).** Pipeline scalabile per trasformare materiali proprietari in Knowledge Skills strutturate. Sara mantiene il controllo sul processo.

### Rischi residui (aggiornati)

1. **22 agenti restano un investimento significativo.** Invariato da v4.1. Mitigazione: la roadmap e' per sprint, si puo' rallentare.

2. **Complessita' del Knowledge System.** Quick Reference + Deep Knowledge + SKILL.md con frontmatter reference = 3 strati di indirezione. Se un file viene rinominato o spostato, le reference si rompono. Mitigazione: il Manutentore fa health check periodici, naming convention rigide.

3. **Sprint 0 piu' pesante.** Lo Sprint 0 ora include la creazione delle Knowledge files oltre all'infrastruttura base. Potrebbe richiedere piu' di una settimana. Mitigazione: prioritizzare i framework usati da piu' agenti e creare solo le Quick Reference inizialmente (le Deep Knowledge possono attendere).

4. **Safety check come graceful degradation.** Se le Quick Reference non esistono, l'agente procede con conoscenze base. Questo e' un fallback, non una situazione ideale — l'output sara' meno strutturato. Mitigazione: completare le Quick Reference prioritarie nello Sprint 0.

5. **Catalogo Flussi come rigidita'.** Se l'Orchestratore segue troppo alla lettera i flussi mappati, potrebbe perdere flessibilita' su richieste ibride. Mitigazione: il protocollo per richieste non mappate e la possibilita' di combinare flussi danno flessibilita'.

6. **Sara come bottleneck.** Invariato da v4.1. L'escalation include sempre contesto + opzioni + raccomandazione per decisioni rapide. In v5.0 si aggiunge la decisione sulle richieste non mappate — ma e' raro e produttivo (mappa nuovi flussi = sistema che migliora).

7. **Race condition sui file condivisi.** Invariato da v4.1. La regola "ogni agente scrive solo i propri file output" previene conflitti. L'output persistence per-progetto con naming `[agente]_[tipo].md` riduce ulteriormente il rischio.
