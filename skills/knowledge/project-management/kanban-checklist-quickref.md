---
framework: Kanban Checklist (task-level execution tracking)
author: Kanban — Toyota Production System (Taiichi Ohno, anni '40-'50). Adattamento a knowledge-work/PM: David J. Anderson, "Kanban: Successful Evolutionary Change for Your Technology Business" (2010).
type: quickref
category: project-management
status: active
---
# KANBAN CHECKLIST — Quick Reference
## Source: Taiichi Ohno / Toyota Production System (concetto originale, produzione). David J. Anderson, *Kanban: Successful Evolutionary Change for Your Technology Business*, 2010 (adattamento a lavoro di conoscenza/progetti). Adattamento TTP: schema colonne derivato dalla checklist operativa reale di Sara (fasi + task + owner/operativo + stato + note).
## When to use: Per tracciare l'esecuzione quotidiana/settimanale di un progetto già scomposto in fasi (vedi `wbs-stage-gate-quickref.md`) — ogni riga è un'attività con stato sempre visibile. **Sessione tipica: 15-20 min a settimana per aggiornare lo stato, non uno strumento da "impostare una volta e dimenticare".**

## WHEN NOT TO USE
- Pianificazione iniziale del progetto (fasi, gate, charter) → prima serve `wbs-stage-gate-quickref.md`, il Kanban traccia l'esecuzione, non la disegna
- Decisioni su COSA fare o se un progetto vale la pena → framework di Strategist
- Attività singola senza dipendenze né bisogno di visibilità di team → è overhead, basta una nota

## CORE THESIS
Un Kanban non è "una lista con tre colonne" — è uno strumento che rende visibile IL FLUSSO del lavoro, non solo l'elenco. Il principio centrale (Anderson 2010) è il **limite al lavoro in corso (WIP limit)**: poche attività "In corso" per persona alla volta, altrimenti il flusso si blocca e tutto rallenta insieme. Una checklist con 15 righe "In corso" contemporaneamente per la stessa persona non è Kanban — è solo una lista disordinata con un'etichetta Kanban sopra.

**Nota di attribuzione (Criterio 7):** Anderson non prescrive un numero universale di WIP limit — il metodo dice di **fissarlo esplicitamente e calibrarlo per team/contesto**, partendo conservativo e aggiustando in base a dove si formano i colli di bottiglia. Il numero "2-3 per persona" più avanti in questo documento **è un'euristica di partenza TTP** per micro-team italiani, non una cifra tratta dalla fonte — per un libero professionista solo, va calibrato a 1-2, non 2-3.

## FIRST PRINCIPLES THINKING (adattamento PMI)
1. **Assunzioni del framework originale**: Kanban nasce per una linea di produzione fisica (Toyota) e viene adattato da Anderson a team software con più persone intercambiabili sullo stesso tipo di lavoro.
2. **Verità fondamentale**: il lavoro invisibile (che nessuno vede bloccato) è lavoro che nessuno sblocca — rendere lo stato visibile è già metà della soluzione ai ritardi.
3. **Vincoli PMI**: spesso una persona sola copre più ruoli contemporaneamente (non "intercambiabile" come in una linea di produzione), quindi il WIP limit non si applica per ruolo ma per persona reale, e va tarato più basso che in un team strutturato.
4. **Ricostruzione nativa TTP**: si mantiene il principio (stato visibile + WIP limit esplicito), si abbandona l'idea di colonne fisiche/board dedicata — per una PMI la checklist tabellare con colonna Stato assolve la stessa funzione, a costo di gestione quasi zero.

## SCHEMA COLONNE (dalla checklist operativa)

| Colonna | Cosa contiene | Nota |
|---|---|---|
| Task Principale | Il macro-task/gruppo di attività | Corrisponde a un ramo del WBS |
| Priorità | Alta / Media / Bassa | Non tutte le attività di una fase hanno lo stesso peso |
| Descrizione Attività | La singola sotto-attività eseguibile | Deve essere azionabile, non un obiettivo generico |
| Effort | Ore stimate | ±20%, si ritara a consuntivo — non è un impegno rigido |
| Owner | Chi ne risponde (Accountable) | Vedi `raci-quickref.md` — deve essere una persona sola |
| Operativo | Chi esegue materialmente (Responsible) | Può essere diverso dall'Owner, o coincidere |
| Data Inizio / Data Fine | Date pianificate | Aggiornate se slittano, non lasciate stantie |
| Stato | Da fare → In corso → Completato | 3 stati minimi, il minimo che serve per essere Kanban |
| Completamento % | Legato a criteri verificabili | Mai "a sensazione" — vedi Errori Comuni |
| Note | Blocchi, dipendenze, motivo di un ritardo | La colonna più importante e la più trascurata |

## LA REGOLA DEL WIP LIMIT (perché conta davvero)
Se una persona ha più attività "In corso" del proprio limite calibrato — euristica di partenza TTP: 2-3 per un piccolo team, 1-2 per un libero professionista solo — il problema non è che lavora poco, è che sta facendo context-switching continuo, e ogni attività rallenta tutte le altre. La disciplina pratica: prima di mettere una nuova attività "In corso", chiedersi se le attuali "In corso" della stessa persona sono davvero bloccate/in pausa o semplicemente non finite.

## STRUMENTO: MARKDOWN VS FOGLIO DI CALCOLO/BOARD
Questa checklist in .md è il riferimento operativo che l'agente TTP (Director) mantiene e da cui ragiona in autonomia (leggibile/scrivibile via Read/Write, versionabile). Per l'uso quotidiano diretto di Sara esiste anche una versione con formule live e semafori colorati: `/knowledge_base/templates/project_wbs_kanban_template.xlsx` (3 fogli: Project Charter, WBS Checklist, Check Effort — somma ore automatica per fase e totale, calcolo costo automatico, menu a tendina per Stato/Priorità, colore automatico per riga in base allo Stato). Le due versioni non sono sincronizzate automaticamente: l'agente mantiene il .md, Sara può lavorare sul .xlsx per l'uso diretto — a fine progetto o a ogni revisione importante, allineare manualmente.

## GUIDING QUESTIONS (da fare in revisione settimanale)
- "Quali attività sono 'In corso' da più di 2 settimane senza cambiamento di stato?" → probabilmente bloccate senza che nessuno l'abbia scritto in Note
- "Il completamento % è legato a qualcosa di verificabile, o è una stima a occhio?" → se non sai rispondere, è a occhio
- "Chi supera il proprio WIP limit calibrato (righe 'In corso' contemporanee)?" → rischio di rallentamento generale, non solo suo

## EXPECTED OUTPUT
1. Checklist compilata per fase — vedi `/knowledge_base/templates/wbs_checklist_template.md`
2. Per ogni attività bloccata: nota esplicita del motivo e della condizione di sblocco (non solo "In corso" senza spiegazione)
3. Revisione periodica: quante righe sono ferme da più di 2 settimane, e perché

## ERRORI COMUNI NELLE PMI
- Completamento % stimato a sensazione ("boh, diciamo 75%") invece che legato a sotto-attività concluse verificabili
- Attività "In corso" per settimane senza una nota che spieghi il blocco — il Kanban diventa un elenco statico, non uno strumento di flusso
- Owner e Operativo sempre identici per abitudine, anche quando in realtà chi risponde del risultato non è chi lo produce materialmente
- Troppe attività "In corso" per la stessa persona — il Kanban senza WIP limit è solo una to-do list travestita

## QUICK EXAMPLE (PMI italiana — studio di consulenza fiscale, 5 persone, progetto di digitalizzazione processo fatturazione)
**Situazione**: 12 attività nel progetto, di cui 6 assegnate alla stessa persona (il titolare), tutte segnate "In corso" da 3 settimane.

**Applicazione**: si scopre che 4 delle 6 sono in realtà ferme in attesa di una decisione del fornitore software (nessuna Nota lo diceva). Si aggiorna: 2 restano "In corso" (WIP limit rispettato), 4 passano a una nuova convenzione "In attesa — bloccata da [motivo]" con data di verifica fissata, e la Nota registra il blocco.

**GO/NO-GO**: se dopo la data di verifica il blocco persiste, si escalation al fornitore con un ultimatum di 5 giorni lavorativi, non si lascia "In corso" a tempo indeterminato.

## QUICK EXAMPLE 2 (libero professionista — grafico freelance, 1 persona, 4 progetti clienti in parallelo)
**Situazione**: il freelance segna "In corso" tutti e 4 i progetti attivi contemporaneamente, perché "ci lavora un po' ogni giorno".

**Applicazione**: con WIP limit 1-2 (calibrato per una sola persona, non 2-3 da team), si scopre che in realtà avanza seriamente solo su 1-2 alla volta — gli altri 2-3 sono fermi in attesa di feedback cliente o materiali, semplicemente non segnati come tali. Si riclassificano: max 2 "In corso" reali, gli altri "In attesa — [motivo]".

**GO/NO-GO**: se un progetto resta "In attesa" per più di 10 giorni lavorativi senza risposta cliente, si invia un sollecito con deadline esplicita, non si lascia scorrere.

## CROSS-REFERENCE
- `wbs-stage-gate-quickref.md` — la pianificazione a monte di cui questo Kanban traccia l'esecuzione
- `raci-quickref.md` — per la distinzione Owner (Accountable) vs Operativo (Responsible)
- `/knowledge_base/templates/wbs_checklist_template.md` — template .md compilabile (agente)
- `/knowledge_base/templates/project_wbs_kanban_template.xlsx` — template .xlsx con formule live (uso diretto di Sara)
- `director/SKILL.md` — agente TTP che mantiene questo tracciamento per ogni progetto attivo
