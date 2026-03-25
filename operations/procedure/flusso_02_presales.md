# FLUSSO 2 — Pre-Sales (5 fasi)

**Trigger:** "nuovo prospect", "qualificazione", "proposta per", "preventivo"

## SEQUENZA AGENTI

```
Fase 1: Esploratore → Stratega → Sara decide GO/NO-GO
Fase 2: Stratega → Sara (prima della discovery call)
Fase 3: Stratega → Voce (opzionale) → Sara
Fase 4: Architetto → God Mode → Sara (ciclo fino a chiusura)
Fase 5: Admin (follow-up)
```

## FASI

### Fase 1 — Qualificazione
- **Esploratore:** Dossier prospect (chi sono, fatturato, problemi, decisori)
- **Stratega:** Scorecard GO/NO-GO
- **Sara decide:** Procedere o no
- **Output:** /clients/[prospect]/presales/dossier_prospect.md

### Fase 2 — Prep Discovery Call
- **Agente:** Stratega
- **Task:** Produce discovery_prep.md con domande SPIN, ipotesi pain, packaging, range pricing
- **Output:** /clients/[prospect]/presales/discovery_prep.md
- **Sara riceve** prima della call

### Fase 3 — Post-Discovery & Pricing
- **Orchestratore:** Aggiorna brief con note dalla discovery call di Sara
- **Stratega:** Definisce negotiation_strategy.md (packaging, pricing ancora/target/floor, concessioni, obiezioni)
- **Voce (se necessario):** Produce objection_map.md
- **Output:** /clients/[prospect]/presales/negotiation_strategy.md + objection_map.md

### Fase 4 — Proposta & Chiusura
- **Architetto:** Genera charter / proposta
- **God Mode:** Revisiona
- **Sara riceve** e invia al prospect
- Se il prospect negozia: ciclo Stratega → Architetto finche' si chiude o NO-GO

### Fase 5 — Follow-up
- **Admin:** Crea followup_tracker.md
- Ogni follow-up: Orchestratore chiede a Sara → Voce draft → Sara invia
- Dopo 3 follow-up senza risposta: escalation con 3 opzioni

## NOTE
- La Fase 1 e' veloce (1-2 ore). Se Sara ha gia' info sul prospect, l'Esploratore integra
- Le fasi 2-3 dipendono dalla discovery call di Sara — il sistema si ferma e aspetta il suo input
- La Fase 4 puo' iterare piu' volte in caso di negoziazione
