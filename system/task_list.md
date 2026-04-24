# TASK LIST — TTP Agency
## Last updated: 2026-04-24

### ACTIVE TASKS

| ID | Task | Assigned to | Priority | Status | Dependencies | Deadline | Notes |
|----|------|-------------|----------|--------|--------------|----------|-------|
| T014 | Test hub-and-spoke flow | Orchestrator | HIGH | PENDING | T011-T013 | — | Sprint 1 completion |
| T015 | Populate all 48 Knowledge Skills | Artisan | MEDIUM | SUPERSEDED_BY_T016 | — | — | Replaced by T016 (priority subset) |
| T016 | Populate priority Knowledge Skills (10 quickref + 4 deep + moderni) | Artisan | HIGH | IN_PROGRESS | — | — | Sessione dedicata 2026-04-24. Include anche messy-middle-b2c + b2b-buying-journey (nuovi, non in lista originale — sostituiscono AIDA) |
| T017 | Knowledge Processing — libreria epub su Drive (Opzione C: triage + deep processing) | Artisan (Mode 2) | MEDIUM | PLANNED | T016 | — | 98+ epub in "epub Business e Marketing"; piano a 5 step documentato |
| T018 | Decisione su SKILL.md Orchestrator (snellimento vs eccezione) | Orchestrator + Sara | LOW | PENDING | T016 | — | Priorità 3 briefing 2026-04-24, non ancora affrontata |

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
| T011 | SKILL.md Strategist | Artisan | 2026-04-23 | /skills/strategist/SKILL.md (v5.1) |
| T012 | SKILL.md God Mode | Artisan | 2026-04-23 | /skills/god_mode/SKILL.md |
| T013 | SKILL.md Sparring Partner | Artisan | 2026-04-23 | /skills/sparring_partner/SKILL.md |

### T016 — PROGRESS LOG (Knowledge Skills — priority subset)

**Started**: 2026-04-24
**Status**: IN_PROGRESS (5/~15 files completed)

| Sub-task | Status | Date | File(s) |
|----------|--------|------|---------|
| swot-quickref.md | ✅ COMPLETED (v2) | 2026-04-24 | /skills/knowledge/analysis/swot-quickref.md (96 lines) |
| porter-5forces-quickref.md | ✅ COMPLETED (v3) | 2026-04-24 | /skills/knowledge/analysis/porter-5forces-quickref.md (120 lines) |
| aida-quickref.md | ✅ COMPLETED (deprecated as historical reference) | 2026-04-24 | /skills/knowledge/marketing/aida-quickref.md (31 lines — A2 solution) |
| messy-middle-b2c-quickref.md | ✅ COMPLETED (new, replaces AIDA operationally) | 2026-04-24 | /skills/knowledge/marketing/messy-middle-b2c-quickref.md (94 lines) |
| messy-middle-b2c-deep.md | ✅ COMPLETED (new) | 2026-04-24 | /skills/knowledge/marketing/messy-middle-b2c-deep.md (284 lines) |
| b2b-buying-journey-quickref.md | ✅ COMPLETED (new) | 2026-04-24 | /skills/knowledge/marketing/b2b-buying-journey-quickref.md (120 lines) |
| b2b-buying-journey-deep.md | ✅ COMPLETED (new, with Italian context + SMB variant) | 2026-04-24 | /skills/knowledge/marketing/b2b-buying-journey-deep.md (345 lines) |
| pas-quickref.md | PENDING | — | — |
| maurya-lean-canvas-quickref.md | PENDING | — | — |
| deveglia-positioning-quickref.md | PENDING | — | — |
| christensen-jtbd-quickref.md | PENDING | — | — |
| christensen-jtbd-deep.md | PENDING | — | — |
| miller-storybrand-quickref.md | PENDING | — | — |
| miller-storybrand-deep.md | PENDING | — | — |
| collins-hedgehog-quickref.md | PENDING | — | — |
| collins-hedgehog-deep.md | PENDING | — | — |
| pestel-quickref.md | PENDING | — | — |
| porter-5forces-deep.md | PENDING | — | — |

### META-DELIVERABLES COMPLETED IN THIS SESSION
- Quickref Protocol v1.1 in `/operations/procedure/quickref_protocol.md` (new file — checklist 7 criteri + First Principles Thinking)

### RULES
- ONLY the Orchestrator creates and updates the task list
- Agents write outputs to /clients/[client]/projects/[project]/findings/ (project output) or /system/findings/ (generic findings)
- Orchestrator updates task list after receiving subagent outputs
