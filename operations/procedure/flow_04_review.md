# FLOW 4 — Review / Update

**Triggers:** "review", "update", "modify pricing", "refresh"

## AGENT SEQUENCE

```
Orchestrator identifies owner agent → Owner agent → God Mode (if critical)
```

## PHASES

### Phase 1 — Identification
- **Agent:** Orchestrator
- **Task:** Identify which deliverable needs revision and who is the owner agent
- **Rule:** The owner agent is the one who produced the original deliverable

### Phase 2 — Revision
- **Agent:** Deliverable owner
- **Input:** Original deliverable + Sara's change instructions
- **Task:** Update the deliverable per instructions
- **Output:** Overwrite original (backup first: rename old file to `[name]_v[N-1].md`)

### Phase 3 — Quality Check (conditional)
- **Agent:** God Mode
- **Condition:** Only if the deliverable is critical (charter, proposal, strategy)
- **Task:** Verify the revision introduced no inconsistencies

## NOTES
- Lightweight flow: 1-2 agents
- If revision implies a strategic change → escalate to Strategist before proceeding
- Always back up the original file before overwriting
