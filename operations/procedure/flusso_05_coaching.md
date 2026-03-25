# FLUSSO 5 — Business Coaching

**Trigger:** "coaching", "sessione", "obiettivi", "crescita personale", "sblocco"

## SEQUENZA AGENTI

```
Mentore (guida) + Sparring Partner (sfida) → Calcolatore (se servono proiezioni)
```

## FASI

### Fase 1 — Sessione di coaching
- **Agente principale:** Mentore (Opus per coaching)
- **Agente di supporto:** Sparring Partner (sfida costruttiva)
- **Task:** Guidare Sara su obiettivi, blocchi, crescita, decisioni business
- **Output:** /clients/[cliente]/progetti/coaching_[data]/findings/mentore_sessione.md

### Fase 2 — Action plan
- **Agente:** Mentore (Sonnet per action plan)
- **Task:** Trasformare insights della sessione in azioni concrete con scadenze
- **Output:** /clients/[cliente]/progetti/coaching_[data]/findings/mentore_action_plan.md

### Fase 3 — Proiezioni (condizionale)
- **Agente:** Calcolatore
- **Condizione:** Solo se servono proiezioni finanziarie o scenari numerici
- **Task:** Modellare scenari discussi nella sessione
- **Output:** /clients/[cliente]/progetti/coaching_[data]/findings/calcolatore_scenari.md

## NOTE
- Il Mentore opera in Opus per il coaching e in Sonnet per l'action plan
- Lo Sparring Partner sfida le ipotesi — non e' un yes-man
- Questo flusso puo' essere usato anche per il coaching di Sara stessa (non solo per i suoi clienti)
