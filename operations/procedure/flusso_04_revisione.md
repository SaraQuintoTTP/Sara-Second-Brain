# FLUSSO 4 — Revisione / Aggiornamento

**Trigger:** "rivedi", "aggiorna", "modifica pricing", "refresh"

## SEQUENZA AGENTI

```
Orchestratore identifica l'agente owner → Agente owner → God Mode (se critico)
```

## FASI

### Fase 1 — Identificazione
- **Agente:** Orchestratore
- **Task:** Identifica quale deliverable va revisionato e chi e' l'agente owner
- **Regola:** L'agente owner e' quello che ha prodotto il deliverable originale

### Fase 2 — Revisione
- **Agente:** Owner del deliverable
- **Input:** Deliverable originale + indicazioni di Sara su cosa cambiare
- **Task:** Aggiorna il deliverable secondo le indicazioni
- **Output:** Sovrascrittura del deliverable originale (con backup: rinomina il vecchio in [nome]_v[N-1].md)

### Fase 3 — Quality check (condizionale)
- **Agente:** God Mode
- **Condizione:** Solo se il deliverable e' critico (charter, proposta, strategia)
- **Task:** Verifica che la revisione non abbia introdotto incoerenze

## NOTE
- Flusso leggero: 1-2 agenti
- Se la revisione implica un cambio strategico → escalation a Stratega prima di procedere
- Sempre fare backup del file originale prima di sovrascrivere
