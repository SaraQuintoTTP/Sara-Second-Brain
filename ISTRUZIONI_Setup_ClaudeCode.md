# ISTRUZIONI PER SARA — Setup AI Agency TTP v5.0 in Claude Code

## I TUOI 3 FILE

Nella tua cartella Downloads trovi 3 file:

1. **`CLAUDE_TTP_Agency.md`** (~50 righe) — Il "cervello" sintetico v5.0. Va caricato come CLAUDE.md del progetto.
2. **`TTP_Agency_Operative_v5.0.md`** (~530 righe) — Le istruzioni operative complete v5.0. Va nella Knowledge Base.
3. **`AI_Agency_TTP_v5.0_Swarm_Architecture.md`** (~1800 righe) — L'architettura completa di reference v5.0. Va nella Knowledge Base.

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

## NOTA IMPORTANTE

I tuoi materiali proprietari (template Project Charter, Brief Format, corsi Aliotta e Abate, listino servizi, parametri fiscali) li caricherai in `/knowledge_base/` man mano che li prepari. Il sistema funziona anche senza — parte con i framework pubblici e si arricchisce nel tempo.

Per caricare materiali proprietari che diventano Knowledge Skills (Quick Reference + Deep Knowledge), usa l'Artigiano in Modalita' 2 (Knowledge Processing):
"Artigiano, processa questo materiale in knowledge skills: [allega file]"

Per materiali grezzi non ancora processati:
"Carica questo file in /knowledge_base/frameworks/[nome].md" oppure
"Carica questo in /knowledge_base/corsi/[nome].md"
