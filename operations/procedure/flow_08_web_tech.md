# FLOW 8 — Web / Tech / Automations

**Triggers:** "website", "seo", "analytics", "automations", "email marketing", "funnel"

## AGENT SEQUENCE

```
Web Tech + Optimizer + Measurer (KPI) → Voice (copy if needed)
```

## PHASES

### Phase 1 — Technical Analysis
- **Agent:** Web Tech
- **Task:** Technical audit (SEO, performance, analytics setup, existing automations)
- **Output:** `/clients/[client]/projects/[name]/findings/webtech_audit.md`

### Phase 2 — Optimization
- **Agent:** Optimizer
- **Task:** CRO, funnel optimization, UX improvements, automations
- **Output:** `/clients/[client]/projects/[name]/findings/optimizer_recommendations.md`

### Phase 3 — KPI & Tracking
- **Agent:** Measurer
- **Task:** KPI setup, dashboard, tracking plan
- **Output:** `/clients/[client]/projects/[name]/findings/measurer_tracking.md`

### Phase 4 — Copy (conditional)
- **Agent:** Voice
- **Condition:** Only if copy is needed for landing pages, email sequences, or funnels
- **Task:** Conversion-optimized copy
- **Output:** `/clients/[client]/projects/[name]/findings/voice_copy.md`

## NOTES
- Strategist only if a strategic decision is required (e.g., platform change, rebranding)
- For CRO and funnels, Optimizer leads the flow
- Web Tech and Optimizer can work in parallel if tasks are independent
