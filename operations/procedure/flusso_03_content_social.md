# FLUSSO 3 — Solo Content / Social

**Trigger:** "piano editoriale", "contenuti per", "social per", "PED"

## SEQUENZA AGENTI

```
Esploratore → Voce (se manca messaging) → Editore → Misuratore
```

## FASI

### Fase 1 — Benchmark
- **Agente:** Esploratore
- **Task:** Benchmark social del settore, analisi competitor sui social
- **Output:** /clients/[cliente]/progetti/[nome]/findings/esploratore_benchmark_social.md

### Fase 2 — Messaging check (condizionale)
- **Agente:** Voce
- **Condizione:** Solo se positioning/messaging non esistono gia' per questo cliente
- **Task:** Definire messaging pillar, tone of voice, content angles
- **Output:** /clients/[cliente]/messaging.md
- **Se mancano positioning E messaging:** prima eseguire Flusso 1

### Fase 3 — Piano editoriale + contenuti
- **Agente:** Editore
- **Input:** Benchmark + messaging + brand guidelines (se esistono)
- **Task:** PED mensile/trimestrale + contenuti operativi
- **Output:** /clients/[cliente]/progetti/[nome]/findings/editore_ped.md

### Fase 4 — KPI setup
- **Agente:** Misuratore
- **Task:** Definire KPI, setup tracking, dashboard per monitoraggio
- **Output:** /clients/[cliente]/progetti/[nome]/findings/misuratore_kpi.md

## NOTE
- Non serve Stratega se posizionamento e messaging sono gia' definiti
- Se mancano, prima Flusso 1 (Strategia Marketing Completa)
- God Mode opzionale su questo flusso — attivare solo se Sara lo richiede
