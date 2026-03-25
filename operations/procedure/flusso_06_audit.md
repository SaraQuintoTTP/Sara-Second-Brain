# FLUSSO 6 — Audit / Quality Review

**Trigger:** "audit", "revisione qualita'", "check deliverable"

## SEQUENZA AGENTI

```
God Mode (audit) + Sparring Partner (stress-test) → Esploratore (se servono dati comparativi)
```

## FASI

### Fase 1 — Audit
- **Agente:** God Mode
- **Task:** Scorecard 7 dimensioni sul deliverable target
- **Verdetto:** PASS / PASS CON RISERVE / FAIL
- **Output:** /clients/[cliente]/progetti/[nome]/findings/god_mode_scorecard.md

### Fase 2 — Stress-test
- **Agente:** Sparring Partner
- **Task:** Pre-Mortem, Inversion, Steel Man sul deliverable
- **Verdetto:** GO / CAUTION / STOP
- **Output:** /clients/[cliente]/progetti/[nome]/findings/sparring_stress_test.md

### Fase 3 — Dati comparativi (condizionale)
- **Agente:** Esploratore
- **Condizione:** Solo se God Mode o Sparring Partner richiedono dati esterni per il confronto
- **Task:** Benchmark specifico richiesto

## NOTE
- Usato anche come step finale di altri flussi (Flusso 1, Flusso 2 Fase 4)
- Quando usato standalone, Sara indica quale deliverable auditare
- Se il verdetto e' FAIL, l'Orchestratore presenta a Sara le raccomandazioni e le opzioni
