# FLOW 6 — Audit / Quality Review

**Triggers:** "audit", "quality review", "check deliverable"

## AGENT SEQUENCE

```
God Mode (audit) + Sparring Partner (stress-test) → Explorer (if comparative data needed)
```

## PHASES

### Phase 1 — Audit
- **Agent:** God Mode
- **Task:** 7-dimension scorecard on target deliverable
- **Verdict:** PASS / PASS WITH RESERVATIONS / FAIL
- **Output:** `/clients/[client]/projects/[name]/findings/god_mode_scorecard.md`

### Phase 2 — Stress-test
- **Agent:** Sparring Partner
- **Task:** Pre-Mortem, Inversion, Steel Man on the deliverable
- **Verdict:** GO / CAUTION / STOP
- **Output:** `/clients/[client]/projects/[name]/findings/sparring_stress_test.md`

### Phase 3 — Comparative Data (conditional)
- **Agent:** Explorer
- **Condition:** Only if God Mode or Sparring Partner request external data for comparison
- **Task:** Specific benchmark as requested

## NOTES
- Also used as final step in other flows (Flow 1, Flow 2 Phase 4)
- When used standalone, Sara specifies which deliverable to audit
- If verdict is FAIL, Orchestrator presents recommendations and options to Sara
