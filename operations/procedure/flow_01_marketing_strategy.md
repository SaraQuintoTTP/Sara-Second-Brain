# FLOW 1 — Full Marketing Strategy

**Triggers:** "strategy for [client]", "marketing plan", "positioning", "launch"

## AGENT SEQUENCE

```
Explorer → Strategist → Voice + Calculator (parallel) → Architect → God Mode
```

## PHASES

### Phase 1 — Market Research
- **Agent:** Explorer
- **Task:** Competitor analysis, industry benchmarks, market data
- **Output:** `/clients/[client]/projects/[name]/findings/explorer_competitors.md`

### Phase 2 — Strategy & Positioning
- **Agent:** Strategist
- **Input:** Explorer findings + client brief
- **Task:** Positioning, Hedgehog, JTBD, messaging pillars
- **Output:** `/clients/[client]/projects/[name]/findings/strategist_positioning.md`

### Phase 3 — Messaging + Projections (parallel)
- **Agent 1:** Voice — messaging strategy, copy, tone of voice
- **Agent 2:** Calculator — financial projections, pricing, budget allocation
- **Output:** `voice_messaging.md` + `calculator_costs.md`

### Phase 4 — Proposal / Charter
- **Agent:** Architect
- **Input:** All previous findings
- **Task:** Assemble structured charter / proposal
- **Output:** `/clients/[client]/projects/[name]/findings/architect_charter.md`

### Phase 5 — Quality Review
- **Agent:** God Mode
- **Task:** 7-dimension scorecard, verdict: PASS / PASS WITH RESERVATIONS / FAIL
- **Output:** `/clients/[client]/projects/[name]/findings/god_mode_scorecard.md`

### Phase 6 — Summary & Delivery
- **Agent:** Orchestrator
- **Task:** Synthesize all findings into FINAL_SUMMARY.md, present to Sara

## NOTES
- If positioning already exists, skip Explorer and start from Strategist
- If budget is very small (<EUR 3,000/month), Calculator may be optional
- God Mode is mandatory on this flow — it is a critical deliverable
