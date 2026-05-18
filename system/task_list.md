# TASK LIST — TTP Agency
## Last updated: 2026-05-19

### ACTIVE TASKS

| ID | Task | Assigned to | Priority | Status | Dependencies | Deadline | Notes |
|----|------|-------------|----------|--------|--------------|----------|-------|
| T014 | Test hub-and-spoke flow | Orchestrator | HIGH | PENDING | T011-T013 | — | Sprint 1 completion |
| T015 | Populate all 48 Knowledge Skills | Artisan | MEDIUM | SUPERSEDED_BY_T016 | — | — | Replaced by T016 (priority subset) |
| T016 | Populate priority Knowledge Skills (10 quickref + 4 deep + moderni) | Artisan | HIGH | IN_PROGRESS | — | — | Sessione dedicata 2026-04-24. Include anche messy-middle-b2c + b2b-buying-journey (nuovi, non in lista originale — sostituiscono AIDA). Global Skills Arsenal: 17 nuove marketing skills installate 2026-05-09 da coreyhaines31/marketingskills (vedi T019) |
| T017 | Knowledge Processing — libreria epub su Drive (Opzione C: triage + deep processing) | Artisan (Mode 2) | MEDIUM | PLANNED | T016 | — | 98+ epub in "epub Business e Marketing"; piano a 5 step documentato |
| T018 | Decisione su SKILL.md Orchestrator (snellimento vs eccezione) | Orchestrator + Sara | LOW | PENDING | T016 | — | Priorità 3 briefing 2026-04-24, non ancora affrontata |
| T020 | Decidere global_skills per God Mode e Sparring Partner | Orchestrator + Sara | MEDIUM | DEFERRED | T021 | Sprint 2 | Da sollevare PRIMA di creare i SKILL.md di God Mode e Sparring Partner. Opzioni: (a) skills di valutazione/sfida contestuale, (b) restano vuoti. Vedi memory project_ttp_system_evolution_deferred.md |
| T021 | Creare SKILL.md per i 9 agenti mancanti (Sprint 2) | Artigiano | HIGH | PLANNED | — | Sprint 2 | Explorer, Voice, Editor, Optimizer, Measurer, Web Tech, Narrator, Architect, Calculator. global_skills per agent definiti in Section 18.3 Operative Doc (aggiornata 2026-05-10). Editor include wonda-cli. Ricordare T020 (God Mode + Sparring Partner) prima di procedere |
| T022 | Installare wonda-cli tool + auth per produzione contenuti | Orchestrator + Sara | MEDIUM | PENDING | — | Sprint 2 | Prerequisito per usare wonda-cli in produzione: `npm i -g @degausai/wonda` + `wonda auth login` su macchina Sara. Richiede account Wondercat con crediti |
| T019 | Installazione 17 marketing skills da coreyhaines31/marketingskills | Orchestrator | HIGH | COMPLETED | — | 2026-05-09 | Skills: ab-test-setup, ai-seo, aso-audit, brainstorming, competitor-alternatives, content-creator, copy-editing, directory-submissions, email-systems, form-cro, free-tool-strategy, geo-fundamentals, launch-strategy, marketing-ideas, marketing-psychology, referral-program, viral-generator-builder |

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
| pas-quickref.md | ✅ COMPLETED | 2026-05-18 | /skills/knowledge/marketing/pas-quickref.md (~80 lines) |
| maurya-lean-canvas-quickref.md | ✅ COMPLETED (v2 — scope ristretto new initiatives) | 2026-05-18 | /skills/knowledge/strategy/maurya-lean-canvas-quickref.md |
| osterwalder-vpc-quickref.md | ✅ COMPLETED v2 (nuovo — diagnostica PMI, triage 4 scenari) | 2026-05-18 | /skills/knowledge/strategy/osterwalder-vpc-quickref.md |
| System coherence audit + 6 gap fix | ✅ COMPLETED | 2026-05-18 | Strategist SKILL.md (VPC+LeanCanvas), pas-quickref.md (VPC xref), Operative Doc Section 11.2 (→ quickref_protocol v1.1) + 11.4 (matrix allineata) |
| deveglia-positioning-quickref.md | ✅ COMPLETED | 2026-05-19 | /skills/knowledge/strategy/deveglia-positioning-quickref.md (Brand Positioning Formula, 4 step, BPS formula, 3 idee differenzianti, 2 test validità, TTP sequenza obbligatoria VPC→JTBD→De Veglia) |
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
