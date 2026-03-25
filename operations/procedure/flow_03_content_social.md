# FLOW 3 — Content / Social Only

**Triggers:** "editorial plan", "content for", "social for", "PED"

## AGENT SEQUENCE

```
Explorer → Voice (if messaging missing) → Editor → Measurer
```

## PHASES

### Phase 1 — Benchmark
- **Agent:** Explorer
- **Task:** Social industry benchmark, competitor social analysis
- **Output:** `/clients/[client]/projects/[name]/findings/explorer_social_benchmark.md`

### Phase 2 — Messaging Check (conditional)
- **Agent:** Voice
- **Condition:** Only if positioning/messaging do not already exist for this client
- **Task:** Define messaging pillars, tone of voice, content angles
- **Output:** `/clients/[client]/messaging.md`
- If both positioning AND messaging are missing: run Flow 1 first

### Phase 3 — Editorial Plan + Content
- **Agent:** Editor
- **Input:** Benchmark + messaging + brand guidelines (if available)
- **Task:** Monthly/quarterly editorial plan + operational content
- **Output:** `/clients/[client]/projects/[name]/findings/editor_editorial_plan.md`

### Phase 4 — KPI Setup
- **Agent:** Measurer
- **Task:** Define KPIs, set up tracking, monitoring dashboard
- **Output:** `/clients/[client]/projects/[name]/findings/measurer_kpi.md`

## NOTES
- Strategist not needed if positioning and messaging are already defined
- If missing, run Flow 1 (Full Marketing Strategy) first
- God Mode optional on this flow — activate only if Sara requests it
