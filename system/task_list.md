# TASK LIST — TTP Agency
## Last updated: 2026-04-23

### ACTIVE TASKS

| ID | Task | Assigned to | Priority | Status | Dependencies | Deadline | Notes |
|----|------|-------------|----------|--------|--------------|----------|-------|
| T011 | SKILL.md Strategist | Artisan | HIGH | PENDING | — | — | Sprint 1 |
| T012 | SKILL.md God Mode | Artisan | HIGH | PENDING | — | — | Sprint 1 |
| T013 | SKILL.md Sparring Partner | Artisan | HIGH | PENDING | — | — | Sprint 1 |
| T014 | Test hub-and-spoke flow | Orchestrator | HIGH | PENDING | T011-T013 | — | Sprint 1 |
| T015 | Populate Knowledge Skills (48 files) | Artisan | MEDIUM | PENDING | — | — | Dedicated session |

### COMPLETED TASKS

| ID | Task | Completed by | Date | Output file |
|----|------|-------------|------|-------------|
| T001 | Market research: pet food Italia | Explorer | 2026-03-26 | clients/test_dog_food/projects/brand_strategy/findings/explorer_competitors.md |
| T002 | Positioning, JTBD, messaging pillars | Strategist | 2026-03-26 | findings/strategist_positioning.md |
| T003 | Messaging strategy, ToV, copy examples | Voice | 2026-03-26 | findings/voice_messaging.md |
| T004 | Budget allocation €10k/12m | Calculator | 2026-03-26 | findings/calculator_costs.md |
| T005 | CRO strategy, paid ads plan | Optimizer | 2026-03-26 | findings/optimizer_cro.md |
| T006 | Funnel & automation plan | Web Tech | 2026-03-26 | findings/webtech_funnel.md |
| T007 | GDPR & cookie compliance check | Legal | 2026-03-26 | findings/legal_compliance.md |
| T008 | Assemble charter | Architect | 2026-03-26 | findings/architect_charter.md |
| T009 | Quality scorecard 7 dimensions | God Mode | 2026-03-26 | findings/god_mode_scorecard.md |
| T010 | FINAL_SUMMARY.md | Orchestrator | 2026-03-26 | clients/test_dog_food/projects/brand_strategy/FINAL_SUMMARY.md |

### RULES
- ONLY the Orchestrator creates and updates the task list
- Agents write outputs to /clients/[client]/projects/[project]/findings/ (project output) or /system/findings/ (generic findings)
- Orchestrator updates task list after receiving subagent outputs
