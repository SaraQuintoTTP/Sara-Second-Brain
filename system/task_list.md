# TASK LIST — TTP Agency
## Last updated: 2026-06-04 (T021 COMPLETED)

### ACTIVE TASKS

| T030 | EVA analisi_mercato_2026: Strategist — positioning + GTM | Strategist | HIGH | COMPLETED | — | 2026-06-06 | 474 lines — clients/EVA/projects/analisi_mercato_2026/findings/strategist_positioning.md |
| T031 | EVA analisi_mercato_2026: Calculator — financial model Year 1-2 | Calculator | HIGH | COMPLETED | T030 | 2026-06-06 | 385 lines — calculator_financials.md (3 issues fixed post God Mode) |
| T032 | EVA analisi_mercato_2026: Voice — messaging framework + copy pillars | Voice | HIGH | COMPLETED | T030 | 2026-06-06 | 416 lines — voice_messaging.md (1 issue fixed post God Mode) |
| T033 | EVA analisi_mercato_2026: God Mode quality audit | God Mode | HIGH | COMPLETED | T030-T032 | 2026-06-06 | PASS WITH RESERVATIONS → corrections applied → effective PASS |
| T034 | EVA analisi_mercato_2026: HTML deliverable | Orchestrator | HIGH | COMPLETED | T033 | 2026-06-06 | EVA_Market_Analysis_2026.html — ~150KB |
| T035 | EVA analisi_mercato_2026: PDF deliverable | Orchestrator | HIGH | COMPLETED | T034 | 2026-06-06 | EVA_Market_Analysis_2026.pdf — 1.6MB (Playwright Chromium) |
| T036 | EVA analisi_mercato_2026: Il Conclave — critical points + opportunities | Sparring Partner / Il Conclave | HIGH | IN PROGRESS | T033 | 2026-06-06 | Convocato da Sara — findings da integrare nel progetto |
|----|----|----|----|----|----|----|----|

| ID | Task | Assigned to | Priority | Status | Dependencies | Deadline | Notes |
| T023 | BRUTO business analysis: mercato, VPC, JTBD, rischi, consumer testing methodology | Strategist | HIGH | COMPLETED | — | 2026-05-20 | 746 righe — clients/test_dog_food/projects/bruto_analysis/findings/strategist_business_analysis.md |
| T024 | Benchmarking internazionale: competitor "punk/raw/istinto" pet food in EU/US | Explorer | HIGH | COMPLETED | — | 2026-05-20 | 378 righe — explorer_competitor_benchmark.md |
| T025 | Unit economics DTC petfood italiano: COGS, pricing, LTV/CAC, break-even | Calculator | HIGH | COMPLETED | — | 2026-05-20 | 442 righe — calculator_unit_economics.md |
| T026 | Devil's advocate: challenge analisi strategica BRUTO | Sparring Partner | HIGH | COMPLETED | T023 | 2026-05-20 | sparring_challenge.md |
| T027 | God Mode scorecard: review finale analisi BRUTO | God Mode | HIGH | COMPLETED | T023-T026 | 2026-05-20 | god_mode_scorecard.md — Confidenza 45-55%, The One Thing: consumer test nome+tagline €500-650 |
|----|------|-------------|----------|--------|--------------|----------|-------|
| T014 | Test hub-and-spoke flow | Orchestrator | HIGH | PENDING | T011-T013 | — | Sprint 1 completion |
| T015 | Populate all 48 Knowledge Skills | Artisan | MEDIUM | SUPERSEDED_BY_T016 | — | — | Replaced by T016 (priority subset) |
| T016 | Populate priority Knowledge Skills (10 quickref + 4 deep + moderni) | Artisan | HIGH | COMPLETED | — | 2026-06-04 | Tutti i file pending ora esistono nel file system (audit 2026-06-04). miller-storybrand quickref+deep ✓, collins-hedgehog quickref+deep ✓, pestel-quickref ✓, porter-5forces-deep ✓ + molti altri creati in sessioni precedenti non tracciati. T016 chiuso. |
| T017 | Knowledge Processing — libreria epub su Drive (Opzione C: triage + deep processing) | Artisan (Mode 2) | MEDIUM | PLANNED | T016 | — | 98+ epub in "epub Business e Marketing"; piano a 5 step documentato |
| T018 | Decisione su SKILL.md Orchestrator (snellimento vs eccezione) | Orchestrator + Sara | LOW | PENDING | T016 | — | Priorità 3 briefing 2026-04-24, non ancora affrontata |
| T020 | Decidere global_skills per God Mode e Sparring Partner | Orchestrator + Sara | MEDIUM | DEFERRED | T021 | Sprint 2 | Da sollevare PRIMA di creare i SKILL.md di God Mode e Sparring Partner. Opzioni: (a) skills di valutazione/sfida contestuale, (b) restano vuoti. Vedi memory project_ttp_system_evolution_deferred.md |
| T021 | Creare SKILL.md per i 9 agenti mancanti (Sprint 2) | Artigiano | HIGH | COMPLETED | — | 2026-06-04 | Explorer, Voice, Editor, Optimizer, Measurer, Web Tech, Narrator, Architect, Calculator. Tutti creati in /skills/[agent]/SKILL.md. Measurer include 6 deep paid-media + MCP google-ads note. Architect include win-themes + shipley-proposal. Web Tech include aeo-citation-workflow. |
| T022 | Installare wonda-cli tool + auth per produzione contenuti | Orchestrator + Sara | MEDIUM | PENDING | — | Sprint 2 | Prerequisito per usare wonda-cli in produzione: `npm i -g @degausai/wonda` + `wonda auth login` su macchina Sara. Richiede account Wondercat con crediti |
| T028 | ⚠️ REMINDER: completare autenticazione Google Ads MCP | Sara | HIGH | PENDING | — | Prossima sessione | MCP mcp-google-ads v1.6.0 installato in ~/.claude.json. Mancano le credenziali: GOOGLE_ADS_DEVELOPER_TOKEN + GOOGLE_ADS_CLIENT_ID + GOOGLE_ADS_CLIENT_SECRET + GOOGLE_ADS_REFRESH_TOKEN. Esegui: (1) Google Cloud Console → abilita Google Ads API → crea OAuth credentials Desktop app; (2) richiedi Developer Token su ads.google.com → Tools → API Center; (3) esegui `mcp-google-ads-auth` in terminale. Poi dimmi le credenziali per aggiungerle alla config. |
| T029 | Creare 6 Deep Knowledge paid-media (Phase 3) + aggiornare Operative Matrix | Artisan | HIGH | COMPLETED | — | 2026-06-04 | 6 file in /skills/knowledge/paid-media/: ppc-strategy-deep, tracking-server-side-deep, paid-social-strategy-deep, paid-creative-strategy-deep, paid-media-audit-deep, search-query-analysis-deep. Matrice aggiornata. |
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
**Status**: IN_PROGRESS (13/~15 files completed)

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
| christensen-jtbd-quickref.md | ✅ COMPLETED v3 | 2026-05-19 | /skills/knowledge/strategy/christensen-jtbd-quickref.md (123 lines — 3 tipi job + gerarchia messaggio, Big Hire/Little Hire + Firing (4ª domanda FPT), Job Statement + test anti-circolare, 4 Forze diagramma, ponte VPC→JTBD, sessione con diagnosi Big/Little Hire, example studio legale completo) |
| christensen-jtbd-deep.md | ✅ COMPLETED | 2026-05-19 | /skills/knowledge/strategy/christensen-jtbd-deep.md (272 lines — Switch Interview Bob Moesta 5 momenti, Christensen vs Ulwick comparison, Job Map Ulwick 8 fasi, 4 Forze phrase recognition, Big/Little Hire design separato, firing prevention + switch interview invertita, ODI semplificato PMI, 3 pattern italiani, 5 errori sistemici) |
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
