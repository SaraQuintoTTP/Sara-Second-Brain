# FLUSSO 1 — Strategia Marketing Completa

**Trigger:** "strategia per [cliente]", "piano marketing", "posizionamento", "lancio"

## SEQUENZA AGENTI

```
Esploratore → Stratega → Voce + Calcolatore (parallelo) → Architetto → God Mode
```

## FASI

### Fase 1 — Ricerca di mercato
- **Agente:** Esploratore
- **Task:** Analisi competitor, benchmark settore, dati di mercato
- **Output:** /clients/[cliente]/progetti/[nome]/findings/esploratore_competitors.md

### Fase 2 — Strategia e posizionamento
- **Agente:** Stratega
- **Input:** Findings Esploratore + brief cliente
- **Task:** Posizionamento, Hedgehog, JTBD, messaging pillar
- **Output:** /clients/[cliente]/progetti/[nome]/findings/stratega_positioning.md

### Fase 3 — Messaging + Proiezioni (parallelo)
- **Agente 1:** Voce — messaging strategy, copy, tone of voice
- **Agente 2:** Calcolatore — proiezioni finanziarie, pricing, budget allocation
- **Output:** voce_messaging.md + calcolatore_costi.md

### Fase 4 — Proposta / Charter
- **Agente:** Architetto
- **Input:** Tutti i findings precedenti
- **Task:** Assemblare charter / proposta strutturata
- **Output:** /clients/[cliente]/progetti/[nome]/findings/architetto_charter.md

### Fase 5 — Quality Review
- **Agente:** God Mode
- **Task:** Scorecard 7 dimensioni, PASS / PASS CON RISERVE / FAIL
- **Output:** /clients/[cliente]/progetti/[nome]/findings/god_mode_scorecard.md

### Fase 6 — Sintesi e consegna
- **Agente:** Orchestratore
- **Task:** Sintetizza tutti i findings in SINTESI_FINALE.md, presenta a Sara

## NOTE
- Se il posizionamento esiste gia', skip Esploratore e parti dallo Stratega
- Se il budget e' molto piccolo (<€3.000/mese), il Calcolatore puo' essere opzionale
- God Mode e' obbligatorio su questo flusso — e' un deliverable critico
