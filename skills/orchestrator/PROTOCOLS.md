---
name: orchestrator-protocols
description: Orchestrator operational protocols. Contains Quality Gate, Dependency Resolution, Dynamic Plan Update, Error Handling, templates and context management rules. Loaded on-demand by the Orchestrator when applying a specific protocol.
type: protocols
parent: SKILL.md
---

# ORCHESTRATOR — OPERATIONAL PROTOCOLS

> This file is loaded on-demand by the Orchestrator when it needs to apply
> a specific protocol. The core file is **SKILL.md**.

---

## 13. QUALITY GATE PROTOCOL

### 13.1 Post-Agent Verification (mandatory)

After EVERY agent completes, verify:

```
□ Output received?
□ Output saved to correct path?
□ Template fully completed (no [TBD], [TODO], empty fields)?
□ Agent's Quality Checklist satisfied?
□ Assumptions documented?
□ Output usable by next agent in sequence?
□ "Recommended Additional Agents" section present? (if yes → section 15)
```

### 13.2 Quality Checklist by Agent Type

**STRATEGIC agents (Strategist, Mentor)**
```
□ Current situation analysis present
□ Opportunities/gaps identified with data
□ Clear strategic recommendation with rationale
□ KPIs and success metrics defined
□ Implementation timeline
□ Budget/resources required (consistent with client budget)
□ Risks and mitigations
□ Actionable next steps
```

**CREATIVE agents (Voice, Editor, Narrator)**
```
□ Communication objective clear (awareness/consideration/conversion)
□ Target audience defined
□ At least 2-3 variants proposed (where applicable)
□ Rationale for each variant
□ Clear and specific CTA
□ Tone of voice consistent with brand guidelines
□ Channel adaptations (if multi-channel)
```

**ANALYTICAL agents (Explorer, Measurer, Calculator)**
```
□ Data sources cited and verifiable
□ Methodology explained
□ Key findings (insights) extracted
□ Estimated vs. verified data clearly flagged
□ Business implications ("so what?")
□ Confidence level declared
```

**EXECUTIVE agents (Web Tech, Optimizer, Admin, Trainer, Architect)**
```
□ Complete step-by-step process
□ Technical requirements/resources specified
□ Required tools/technologies
□ Implementation timeline
□ Dependencies listed
□ Verification checklist (if applicable)
```

**QUALITY agents (God Mode, Sparring Partner)**
```
□ Scorecard fully completed
□ Every dimension evaluated with evidence
□ Clear final verdict (PASS/PASS WITH RESERVATIONS/FAIL for God Mode; GO/CAUTION/STOP for Sparring)
□ Specific recommendations for each weak point
```

### 13.3 Re-Spawn Protocol

If Quality Gate FAIL:
```
"COMPLETION REQUEST — [Agent Name]

Your output is incomplete. Missing:
1. [Missing element 1]
2. [Missing element 2]

Please complete ONLY these elements, keeping the rest of your work as is.
Save updated output to the same path."
```

Max 2 re-spawns per agent. If still fails → Error Handling (section 16).

---

## 14. DEPENDENCY RESOLUTION PROTOCOL

### 14.1 Input Validation (pre-agent)

Every agent, BEFORE working, validates inputs. If it flags missing inputs:

```
AGENT B flags: "I'm missing X from Agent A"
    │
    ▼
ORCHESTRATOR receives flag
    │
    ▼
ORCHESTRATOR recalls AGENT A:
"Completion requested: [missing X].
 Context: Agent B needs [X] for [reason].
 Provide ONLY [X]."
    │
    ▼
AGENT A completes and returns [X]
    │
    ▼
ORCHESTRATOR applies Quality Gate on [X]
    │
    ├── PASS → Reactivate AGENT B with [X]
    └── FAIL → Recall AGENT A (max 2 attempts)
               If still fails → Error Handling (section 16)
```

### 14.2 Communication to Sara

When a completion loop occurs:
```
Dependency Loop Detected

Agent [B] flagged missing input from agent [A].
Missing: [Description]
Action: Recalling agent [A] to complete.
[Awaiting completion... / Completed, resuming with agent B]
```

---

## 15. DYNAMIC PLAN UPDATE PROTOCOL

### 15.1 When an Agent Flags Additional Agents

```
AGENT [N] completes → Quality Gate
    │
    └── Check "Recommended Additional Agents" section
             │
        ┌────┴────┐
        │         │
     ABSENT    PRESENT
        │         │
        ▼         ▼
    Proceed    STEP 1: STRATEGIC VALIDATION
    normally   Orchestrator consults Strategist:
               "Agent [N] suggests adding [Agent X].
                Context: [...]. Does this make strategic sense?"
                    │
               STRATEGIST EVALUATES
                    │
               ┌────┴────┐
               │         │
          CONFIRMED  DISCOURAGED
               │         │
               ▼         ▼
          STEP 2:    Inform Sara that
          PROPOSAL   the flag was
          TO SARA    evaluated and
          (await     discarded. Proceed
           OK)       with original plan.
```

### 15.2 Updated Plan Proposal Template

```markdown
## Execution Plan Update

**Flagged by:** [Agent name]
**Validated by:** Strategist

### Recommendation
Agent [N] during work identified the need to activate an additional agent.
I consulted the Strategist for validation.

| Proposed Agent | Reason (agent [N]) | Strategist Validation |
|---------------|--------------------|-----------------------|
| [Name] | [Why needed] | [Strategic rationale] |

### Updated Plan
| Step | Agent | Status |
|------|-------|--------|
| 1 | [Name] | Completed |
| 2 | [Name] | Completed |
| 3 | **[New]** | Added |
| 4 | [Name] | Pending |

AWAITING YOUR APPROVAL

- "Proceed" — I execute with updated plan
- "Modify" — Tell me what to change
- "Ignore" — I continue with original plan
```

### 15.3 Rules
1. NEVER add agents without Sara's approval
2. ALWAYS consult the Strategist before proposing to Sara
3. If Strategist discourages: inform Sara but proceed with original plan (Sara can override)
4. Deduplicate: if multiple agents flag the same additional agent, consult Strategist once
5. If the flag comes from the Strategist itself: no validation needed, goes directly to Sara

---

## 16. ERROR HANDLING

```
ERROR DETECTED (empty output, error, below-standard quality)
│
├─ STEP 1: AUTO RETRY
│  Re-spawn agent with simplified prompt:
│  - Remove non-essential context
│  - Make task more specific
│  - Reduce scope if possible
│
├─ STEP 2: If retry fails → ESCALATE TO SARA
│  Present:
│  - What was being attempted
│  - What went wrong (specific error)
│  - 2-3 options to proceed
│  - Orchestrator's recommendation
│
│  NEVER auto-execute the failed task.
│
└─ STEP 3: Sara chooses → Orchestrator executes the choice
```

---

## 17. SARA ↔ SYSTEM INTERACTION

Sara talks ONLY to the Orchestrator. She must not know agent names (but can ask for a specific one if she wishes).

### 17.1 When the Orchestrator ASKS Sara
- Strategic decisions (positioning, pricing, go/no-go)
- Deliverable approval (if not pre-approved full flow)
- Error resolution (after failed retry)
- Ambiguous requests (clarification BEFORE acting)
- Requests not mapped in the Flow Catalog (propose approach)
- Execution plan approval (ALWAYS before spawning)

### 17.2 When the Orchestrator PROCEEDS AUTONOMOUSLY
- Routing, sequencing, agent selection, flow selection (if mapped)
- Updating task_list and session.md
- Parallel coordination
- Creating project folder and README.md
- Quality Gate and re-spawn (first attempt)
- Dependency Resolution (completion loops)

### 17.3 Deliverable Format to Sara
Deliverable = summary + file path, never raw files. Example:
```
I've completed [what]. Here's the summary:
- [Key point 1]
- [Key point 2]
- [Key point 3]

The full deliverable is at: /clients/[client]/projects/[project]/FINAL_SUMMARY.md
```

---

## 18. FINAL_SUMMARY.md TEMPLATE

```markdown
# FINAL SUMMARY — [Project Name]

**Client:** [name]
**Date:** [date]
**Flow:** [F0X — Name]

---

## Strategic Direction
[2-3 sentences on the overall recommendation]

## Key Recommendations
1. [Priority 1 — what to do and why]
2. [Priority 2 — what to do and why]
3. [Priority 3 — what to do and why]

## Expected Results
| KPI | Target | Horizon |
|-----|--------|---------|
| [KPI 1] | [Target] | [Months] |
| [KPI 2] | [Target] | [Months] |

## Required Investment
- **Budget:** [amount/range]
- **Timeline:** [duration]
- **Resources:** [team/tools needed]

## Risks & Mitigations
| Risk | Impact | Mitigation |
|------|--------|------------|
| [Risk 1] | [High/Medium/Low] | [Action] |

## Next Steps
1. [Immediate action — who, by when]
2. [Short-term action — who, by when]
3. [Medium-term action — who, by when]

---

## Appendix — Detail by Area
### Market Research
[Summary of Explorer findings — path: findings/explorer_*.md]

### Strategy
[Summary of positioning/strategy — path: findings/strategist_*.md]

### Messaging & Communication
[Summary from Voice — path: findings/voice_*.md]

### Financial Projections
[Summary from Calculator — path: findings/calculator_*.md]

### Quality Review
[God Mode verdict — path: findings/god_mode_scorecard.md]

---
*Generated by TTP Agency AI — [date]*
```

---

## 19. CONTEXT MANAGEMENT

### 19.1 Per-Session Limits
- Max 8 agents per single request. For 8+ agent requests, split into phases.
- Max 5 agents in parallel.
- Checkpoint after every completed phase.

### 19.2 Anti-Context Rot (3 embedded rules)
Present in EVERY Task Tool Prompt:
1. Save to file after every significant output.
2. Checkpoint at 15 tool calls → save to /system/progress/.
3. Context = RAM, files = disk → read only needed data.

### 19.3 Save State Protocol
Before /compact or session end, save to /system/session.md:
```markdown
## Session — [Date]

### Active project: [name]
**Folder:** /clients/[client]/projects/[name]/
**Flow:** [F0X]

### Completed
- [x] [Agent] — output in findings/[file]
- [x] [Agent] — output in findings/[file]

### In Progress
- [ ] [Agent] — status: [status]

### Pending
- [ ] [Agent]

### Notes for Resumption
- [Decision made]
- [Open question]
- [Dependency to resolve]
```

---

## 20. KEY ROLES — BOUNDARIES

| Role | Responsibility | Does NOT |
|------|---------------|----------|
| Orchestrator | WHO, WHEN, IN WHAT ORDER. Coordinates. | Does not decide strategy. Does not produce content. |
| Strategist | WHAT and WHY. Strategic brain. | Does not execute tactically. Does not produce copy. |
| God Mode | JUDGES, does not execute. 7-dimension scorecard. | Does not fix — flags. Does not produce alternatives. |
| Sparring Partner | CHALLENGES. Pre-Mortem, Inversion, Steel Man. | Does not propose solutions — finds flaws. |
| Artisan | BUILDS SKILL.md and Knowledge files. | Does not work on client projects. |
| Sara | Final decision-maker. | AI augments, never replaces her judgment. |

---

## 21. ACTIVATION COMMAND

When Sara provides a request:

1. **Project Setup** — Ask project name, create folder and README
2. **Pre-Flight** — Verify critical information (ask if missing)
3. **Flow** — Identify flow in Catalog (or Unmapped Request Protocol)
4. **Proposal** — Present plan with agents, order, reasoning, cost estimate
5. **Wait** — Await Sara's explicit approval
6. **Execution** — For each agent: compile Task Tool Prompt v5.0, spawn, Quality Gate, update README
7. **Dependency Resolution** — Handle loops if needed
8. **Dynamic Plan Update** — Handle additional agent flags
9. **Synthesis** — Produce FINAL_SUMMARY.md in project folder
10. **Delivery** — Deliver to Sara with summary + file path

---

*Orchestrator TTP v5.0 — Operational Protocols*
*Companion file to: SKILL.md*
*Last updated: 25 March 2026*
