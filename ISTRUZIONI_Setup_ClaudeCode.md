# ISTRUZIONI PER SARA — Setup AI Agency TTP v5.0 in Claude Code

## I TUOI 4 FILE

Nella tua cartella di progetto trovi 4 file:

1. **`.claude/CLAUDE.md`** (~50 righe) — Il "cervello" sintetico v5.0. Claude Code lo legge automaticamente a ogni sessione.
2. **`knowledge_base/ttp_internal/TTP_Agency_Operative_v5.0.md`** (~700 righe) — Le istruzioni operative complete v5.0. Documento principale per il 95% delle operazioni.
3. **`knowledge_base/ttp_internal/AI_Agency_TTP_v5.0_Swarm_Architecture.md`** (~1550 righe) — L'architettura completa di reference v5.0. Per capire il PERCHE' delle scelte.
4. **`ISTRUZIONI_Setup_ClaudeCode.md`** (questo file) — La guida passo-passo che stai leggendo ora.

---

## STEP 1 — Crea la cartella del progetto

Sul tuo computer, crea una cartella dedicata al progetto. Esempio:
```
~/Documenti/TTP_AI_Agency/
```

## STEP 2 — Posiziona il CLAUDE.md

Copia `CLAUDE_TTP_Agency.md` nella root della cartella del progetto e rinominalo:
```
~/Documenti/TTP_AI_Agency/.claude/CLAUDE.md
```
(Crea la sottocartella `.claude` se non esiste)

Questo fa si' che Claude Code legga automaticamente queste istruzioni a ogni sessione.

## STEP 3 — Crea la struttura iniziale

Dentro la cartella del progetto, crea questa struttura:
```
~/Documenti/TTP_AI_Agency/
├── .claude/
│   └── CLAUDE.md                    ← (gia' fatto nello Step 2)
├── knowledge_base/
│   └── ttp_internal/
│       ├── TTP_Agency_Operative_v5.0.md         ← copia qui il file operativo
│       └── AI_Agency_TTP_v5.0_Swarm_Architecture.md  ← copia qui il file architetturale
├── system/                          ← vuota per ora (la popola lo Sprint 0)
├── clients/                         ← vuota per ora
├── skills/                          ← vuota per ora
│   └── knowledge/                   ← (NUOVO) per il sistema a 2 livelli
└── operations/
    └── procedure/                   ← (NUOVO) Catalogo Flussi
```

## STEP 4 — Apri Claude Code

Apri Claude Code e naviga nella cartella del progetto:
```
cd ~/Documenti/TTP_AI_Agency
claude
```

## STEP 5 — Lancia lo Sprint 0

Copia e incolla il prompt qui sotto nella nuova sessione Claude Code.

---

## PROMPT DI AVVIO — Sprint 0

```
Sei l'Orchestratore della AI Agency TTP. Prima di fare qualsiasi cosa:

1. Leggi il documento operativo completo: /knowledge_base/ttp_internal/TTP_Agency_Operative_v5.0.md
2. Dopo averlo letto, esegui lo Sprint 0 — Infrastruttura:

SPRINT 0 — CHECKLIST:

A) VERIFICA STRUTTURA FILE SYSTEM
   - Verifica che esistano le cartelle: /system/, /clients/, /skills/, /knowledge_base/, /operations/
   - Crea le sottocartelle mancanti secondo la sezione 2 del documento operativo:
     /system/findings/, /system/progress/
     /skills/knowledge/ con sottocartelle: strategy/, marketing/, analysis/, operations/, quality/, business/
     /operations/procedure/
   - Crea il file /system/task_list.md con il template dalla sezione operativa
   - Crea il file /system/decisions_log.md (vuoto con header)
   - Crea il file /system/sessione.md (vuoto con header: Progetto attivo, Ultimo task, Prossimo step, Blocchi)

B) CREA IL SISTEMA KNOWLEDGE A 2 LIVELLI
   - Nella cartella /skills/knowledge/, crea le Quick Reference (max 120 righe ciascuna)
     per i framework prioritari elencati nella sezione 11 del documento operativo
   - Formato Quick Reference: YAML frontmatter + Quando usare + Template operativo + Domande guida + Output atteso
   - Per i framework piu' complessi, crea anche le Deep Knowledge (max 350 righe)
   - Usa la tua conoscenza dei framework e WebSearch dove necessario
   - Priorita': prima i framework usati da piu' agenti (posizionamento, SWOT, AIDA, PAS, Lean Canvas)

C) POPOLA IL CATALOGO FLUSSI
   - In /operations/procedure/, crea un file per ciascuno degli 8 flussi definiti nella sezione 9
     del documento operativo (piano_marketing.md, campagna_content.md, lancio_prodotto.md, ecc.)
   - Ogni file deve contenere: trigger, fasi, agenti coinvolti, sequenza, output attesi

D) CREA LA SKILL.md DELL'ARTIGIANO
   - L'Artigiano e' il primo agente da costruire (scrive le SKILL.md degli altri)
   - Segui il blueprint SKILL.md v5.0 dalla sezione 10 del documento operativo (8 sezioni)
   - Includi le sezioni PREREQUISITI e CHECKLIST QUALITA'
   - L'Artigiano ha 2 modalita': Skill Maintenance e Knowledge Processing (sezione 15)
   - Salva in /skills/artigiano/SKILL.md

E) REPORT A SARA
   - Quando hai finito, presenta un summary di cosa hai creato
   - Segnala eventuali problemi o decisioni che richiedono il mio input
   - Proponi il prossimo step (Sprint 1: Orchestratore + Stratega + God Mode)

Procedi in ordine A → B → C → D → E. Se qualcosa non e' chiaro, chiedi prima di procedere.
```

---

## DOPO LO SPRINT 0

Una volta completato lo Sprint 0, il sistema e' pronto per costruire gli agenti in ordine di priorita':

| Sprint | Settimane | Agenti | Perche' prima |
|--------|-----------|--------|---------------|
| Sprint 0 | 1 | Infrastruttura + Artigiano | L'Artigiano scrive le SKILL.md degli altri |
| Sprint 1 | 2-3 | Orchestratore + Stratega + God Mode | Il nucleo decisionale |
| Sprint 2 | 4-5 | Architetto + Esploratore + Calcolatore | Pre-sales + proposte (generazione revenue) |
| Sprint 3 | 6-7 | Voce + Editore + Regista | Content + flusso progetto e2e |
| Sprint 4 | 8-9 | Misuratore + Tecnico Web + Ottimizzatore | Esecuzione |
| Sprint 5 | 10-11 | Commercialista + Legale + Admin + Formatore | Supporto |
| Sprint 6 | 12 | Mentore + SP + Economo + Manutentore | Advisory + audit + Knowledge Processing fonti Sara |

**Stato attuale:** Sprint 0 completato. Sprint 1 parzialmente avviato (Orchestratore, Stratega, God Mode, Sparring Partner hanno gia' le SKILL.md).

---

## NOTA IMPORTANTE

I tuoi materiali proprietari (template Project Charter, Brief Format, corsi Aliotta e Abate, listino servizi, parametri fiscali) li caricherai in `/knowledge_base/` man mano che li prepari. Il sistema funziona anche senza — parte con i framework pubblici e si arricchisce nel tempo.

Per caricare materiali proprietari che diventano Knowledge Skills (Quick Reference + Deep Knowledge), usa l'Artigiano in Modalita' 2 (Knowledge Processing):
"Artigiano, processa questo materiale in knowledge skills: [allega file]"

Per materiali grezzi non ancora processati:
"Carica questo file in /knowledge_base/frameworks/[nome].md" oppure
"Carica questo in /knowledge_base/corsi/[nome].md"

---

## TROUBLESHOOTING

**Claude Code non legge il CLAUDE.md?**
Verifica che il file sia in `.claude/CLAUDE.md` nella root del progetto e che tu abbia aperto Claude Code dalla cartella giusta.

**Lo Sprint 0 si interrompe a meta'?**
Rilancia il prompt di Sprint 0. Claude Code riprendera' da dove si e' fermato verificando cosa esiste gia'.

**Devo aggiornare i documenti?**
Il documento operativo (`TTP_Agency_Operative_v5.0.md`) e' l'unico che va aggiornato regolarmente. L'architetturale (`AI_Agency_TTP_v5.0_Swarm_Architecture.md`) cambia solo per revisioni architetturali maggiori. Il CLAUDE.md cambia solo se cambia il protocollo core.

**Convenzione linguistica**
I file di infrastruttura (SKILL.md, prompts, system/, operations/, knowledge skills) sono in inglese — gli LLM performano meglio con istruzioni in inglese e il testo e' ~25% piu' conciso. I deliverable cliente e le comunicazioni con Sara restano in italiano.
