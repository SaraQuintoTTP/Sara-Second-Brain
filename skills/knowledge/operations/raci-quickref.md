---
framework: RACI Matrix
author: Origine contesa — radici nella "responsibility charting" della letteratura di organizzazione aziendale anni '50-60; formalizzazione e diffusione moderna tramite PMBOK Guide (Project Management Institute) e letteratura di project management anni '80-90. Nessun singolo autore verificabile.
type: quickref
category: operations
status: active
---
# RACI MATRIX — Quick Reference
## Source: Project Management Institute, *PMBOK Guide* (responsibility assignment matrix). Origine esatta contesa — non attribuire a un singolo autore/anno specifico.
## When to use: Quando più persone/ruoli toccano lo stesso deliverable e non è chiaro chi decide, chi esegue, chi va sentito prima. **Sessione tipica PMI: 30-45 min per mappare un processo ricorrente (non uno a uno per ogni task).**

## WHEN NOT TO USE
- Task con un solo owner evidente → la matrice è overhead inutile
- Urgenza immediata che richiede decisione in minuti → usa `eisenhower-quickref.md`
- Il problema reale è la priorità, non la responsabilità → usa `eisenhower-quickref.md`
- Metodo di lavoro personale/solo del titolare → non si applica (RACI serve dove c'è più di una persona)

## CORE THESIS
La causa più comune di ritardi/errori in una PMI non è la mancanza di competenza, è l'ambiguità su chi decide. RACI costringe a rispondere a 4 domande per ogni deliverable, non di più:
- **R — Responsible**: chi esegue materialmente il lavoro (può essere più di uno)
- **A — Accountable**: chi risponde del risultato finale — **deve essere esattamente UNA persona**, mai zero, mai più di una
- **C — Consulted**: chi va sentito PRIMA (dialogo a due vie) — tenerlo corto, ogni C aggiunto rallenta
- **I — Informed**: chi va aggiornato DOPO (comunicazione a una via) — non serve il suo consenso

## L'ERRORE PIÙ COMUNE (in assoluto)
Zero o più di un Accountable per lo stesso deliverable. Zero Accountable = nessuno risponde se qualcosa va storto. Due Accountable = ognuno pensa che decida l'altro. La disciplina di RACI in una PMI si riduce per il 90% a questa singola regola.

## APPLICAZIONE PMI — 4 PASSI
1. **Elencare i deliverable ricorrenti** del processo (non le singole micro-attività — troppo granulare è inutile)
2. **Per ciascuno, assegnare A per primo** — se non emerge un nome chiaro, il processo stesso è mal disegnato prima ancora di essere mal eseguito
3. **Assegnare R** — chi esegue; se R e A coincidono nella stessa persona è normale in una PMI piccola, non è un errore
4. **Limitare C e I** — regola pratica: se una riga ha più di 2-3 C, il processo è probabilmente troppo centralizzato o la decisione è stata scomposta male

## MATRICE — ESEMPIO-TIPO (agenzia di comunicazione, 8 persone)

| Deliverable | R | A | C | I |
|---|---|---|---|---|
| Piano editoriale mensile | Social media manager | Account manager | Titolare (su budget) | Cliente |
| Fattura cliente | Amministrazione | Titolare | — | Account manager |
| Consegna sito web | Sviluppatore | Project manager | Grafico, SEO | Cliente, titolare |

## GUIDING QUESTIONS (da fare al titolare della PMI)
- "Per [deliverable X], se qualcosa va storto, chi risponde di persona?" → quella è l'Accountable, non chi lo fa materialmente
- "Chi state consultando per ogni decisione che in realtà non ha voce in capitolo?" → candidato a diventare I invece di C
- "C'è un deliverable dove più di una persona pensa di essere responsabile?" → sintomo di A duplicato

## EXPECTED OUTPUT
1. Tabella RACI per i deliverable ricorrenti del processo analizzato (non oltre 8-10 righe — oltre è segno che il processo va scomposto)
2. Un Accountable esplicito per ogni riga, mai vuoto
3. Lista dei C da declassare a I (quick win immediato quasi sempre presente)

## ERRORI COMUNI NELLE PMI
- Accountable non assegnato ("decidiamo insieme") → in pratica nessuno decide, il deliverable si blocca
- Troppi Consulted per abitudine gerarchica, non per necessità reale della decisione
- Confondere R con A quando il titolare fa tutto: va bene che coincidano, ma vanno comunque distinti sulla carta
- Usare RACI per micro-task quotidiani invece che per processi ricorrenti — costo di manutenzione superiore al beneficio

## QUICK EXAMPLE (PMI italiana — officina meccanica conto terzi, 14 dipendenti, Brescia)
**Decisione**: chi approva una modifica al preventivo dopo che il cliente chiede una variante in corso d'opera?

Prima di RACI: la variante passava tra 4 persone (responsabile commerciale, capo officina, titolare, amministrazione) senza che nessuno sapesse chi doveva dire l'ultima parola — media 6 giorni di ritardo per variante.

RACI applicato: **R** = responsabile commerciale (ricalcola preventivo) — **A** = titolare (unico che approva, sopra soglia €500) — **C** = capo officina (fattibilità tecnica, prima dell'approvazione) — **I** = amministrazione (dopo, per fatturazione).

**GO/NO-GO**: tempo medio di approvazione variante sceso sotto 2 giorni entro 30 giorni dall'adozione → GO su estensione ad altri processi; se resta sopra 4 giorni → il collo di bottiglia non era l'ambiguità di ruolo, cercare altrove (es. disponibilità del titolare).

## CROSS-REFERENCE
- `eisenhower-quickref.md` — quando il problema è la priorità, non la responsabilità
- `snowden-cynefin-quickref.md` — per capire se il processo è abbastanza stabile da meritare una RACI fissa o è troppo complesso/mutevole
- `deming-pdca-quickref.md` — RACI definisce i ruoli, PDCA il ciclo di miglioramento del processo stesso
- `director/SKILL.md` — agente TTP che applica RACI per mappare dipendenze tra task multi-agente
