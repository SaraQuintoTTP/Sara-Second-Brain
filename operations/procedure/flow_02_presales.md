# FLOW 2 — Pre-Sales (5 Phases)

**Triggers:** "new prospect", "qualification", "proposal for", "quote"

## AGENT SEQUENCE

```
Phase 1: Explorer → Strategist → Sara decides GO/NO-GO
Phase 2: Strategist → Sara (before discovery call)
Phase 3: Strategist → Voice (optional) → Sara
Phase 4: Architect → God Mode → Sara (loop until close)
Phase 5: Admin (follow-up)
```

## PHASES

### Phase 1 — Qualification
- **Explorer:** Prospect dossier (who they are, revenue, pain points, decision-makers)
- **Strategist:** GO/NO-GO scorecard
- **Sara decides:** Proceed or not
- **Output:** `/clients/[prospect]/presales/prospect_dossier.md`

### Phase 2 — Discovery Call Prep
- **Agent:** Strategist
- **Task:** Produce `discovery_prep.md` with SPIN questions, pain hypotheses, packaging, pricing range
- **Output:** `/clients/[prospect]/presales/discovery_prep.md`
- Sara receives this before the call

### Phase 3 — Post-Discovery & Pricing
- **Orchestrator:** Updates brief with Sara's discovery call notes
- **Strategist:** Produces `negotiation_strategy.md` (packaging, anchor/target/floor pricing, concessions, objections)
- **Voice (if needed):** Produces `objection_map.md`
- **Output:** `/clients/[prospect]/presales/negotiation_strategy.md` + `objection_map.md`

### Phase 4 — Proposal & Close
- **Architect:** Generates charter / proposal
- **God Mode:** Reviews
- Sara receives and sends to prospect
- If prospect negotiates: Strategist → Architect loop until close or NO-GO

### Phase 5 — Follow-up
- **Admin:** Creates `followup_tracker.md`
- Each follow-up: Orchestrator asks Sara → Voice drafts → Sara sends
- After 3 unanswered follow-ups: escalation with 3 options

## NOTES
- Phase 1 is fast (1-2 hours). If Sara already has prospect info, Explorer supplements
- Phases 2-3 depend on Sara's discovery call — system pauses and waits for her input
- Phase 4 can iterate multiple times during negotiation
