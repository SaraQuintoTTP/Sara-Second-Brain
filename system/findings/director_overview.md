# MULTI-PROJECT OVERVIEW
## Director — TTP Agency
**Generated:** 2026-07-27
**Sources:** /system/task_list.md, /system/session.md (only). Client directory listing used only to confirm which project folders exist — deliverables inside them were not opened (out of scope).

**% complete methodology note:** computed as (tasks marked COMPLETED / total tracked tasks logged for that project in task_list.md). This is a count derived directly from the source file, not an estimate of effort or business progress — flagged here so it isn't mistaken for a qualitative judgment.

---

## STATUS TABLE

| Client | Project | Phase | % Complete | Next Deadline |
|---|---|---|---|---|
| EVA (Studio Legale Boschetti) | analisi_mercato_2026 | Deliverables (T030–T035) complete; T036 "Il Conclave — critical points + opportunities" IN PROGRESS | 6/7 tasks completed (~86%) | **Unverified.** T036's Deadline column reads "2026-06-06" — identical to the task's own open date, not distinguishable from a placeholder. No confirmed real due date found in either source file. |
| test_dog_food | brand_strategy | COMPLETED (T001–T010, FINAL_SUMMARY.md delivered) | 10/10 tasks completed (100%) | None — project closed 2026-03-26 |
| test_dog_food | bruto_analysis | COMPLETED (T023–T027, God Mode scorecard delivered) | 5/5 tasks completed (100%) | None — project closed 2026-05-20 |
| test_dog_food | customer_discovery | **Unverified.** Folder exists on disk (confirmed via directory listing) but has zero entries in task_list.md or session.md — no task ID, owner, status, or deadline of any kind. | Unverified — no data | Unverified — no data |
| TTP (internal) | Agency system build (roster + knowledge base) | Sprint 0–2 complete per session.md ("Sprint 0 ✓ — Infrastructure, Sprint 1 ✓ — Core strategico, Sprint 2 ✓ — 9 SKILL.md creati"); Sprint 3–6 marked "✗ — In sospeso" with no scope defined in either source | Roster: 22/22 agent SKILL.md files complete (T037). Knowledge Skills subset (T016): 13/~15 items done, 6 sub-items still PENDING (miller-storybrand quickref+deep, collins-hedgehog quickref+deep, pestel-quickref, porter-5forces-deep) | None listed. Session.md names three unstarted candidates with no dates: full 22-agent hub-and-spoke test, closing the 4 remaining Knowledge Skills gaps, and unblocking T028/T022 (both waiting on Sara). |

---

## RACI FLAGS

Per `/skills/knowledge/operations/raci-quickref.md`: every deliverable must have exactly one Accountable, never zero, never more than one. The following entries in task_list.md do not satisfy that.

1. **T036 — EVA "Il Conclave — critical points + opportunities"** (Sparring Partner / Il Conclave). Assignee field lists two names joined by "/". If this means "Sparring Partner using the Il Conclave skill," ownership is fine and this is just a notation issue. If it means joint ownership between two distinct accountable parties, it violates the single-Accountable rule. **Also flagged as stale-in-progress:** opened and still IN PROGRESS since 2026-06-06 (7+ weeks as of today, 2026-07-27), with no updated status, no logged next owner, and no completion note in either source file. Recommend Orchestrator confirm current status and, if genuinely still open, assign one unambiguous Accountable and a real deadline.

2. **T018 — "Decisione su SKILL.md Orchestrator (snellimento vs eccezione)"**. Assigned to "Orchestrator + Sara" jointly. No single Accountable named. Status PENDING since dependency T016 completed (2026-06-04); no owner has since claimed the decision.

3. **T020 — "Decidere global_skills per God Mode e Sparring Partner"**. Assigned to "Orchestrator + Sara" jointly. Status DEFERRED. Same dual-assignee pattern as T018 — no single Accountable, and "DEFERRED" has no next-review trigger recorded, so it is effectively stalled with nobody currently responsible for re-raising it.

4. **T022 — "Installare wonda-cli tool + auth"**. Assigned to "Orchestrator + Sara" jointly in task_list.md. session.md's blocker note ("T022: Sara deve avere account Wondercat con crediti") suggests the real accountable party is Sara alone, but the task_list.md assignment itself still reads as joint. Recommend correcting the task_list.md assignee field to a single name to remove the ambiguity — flagging rather than editing, since Director does not own that file.

5. **T028 — "REMINDER: completare autenticazione Google Ads MCP"**. Accountable (Sara) is unambiguous — no RACI issue here. Flagged only for a secondary, non-ownership reason: the deadline field reads "Prossima sessione" ("next session"), which is not a verifiable calendar date and cannot be tracked as a real deadline.

No other IN PROGRESS or PENDING tasks in the current active set showed dual or missing Accountable assignment at the time of this review.

---

## OPEN GAPS / FLAGGED FOR ORCHESTRATOR
- `clients/test_dog_food/projects/customer_discovery/` exists on disk with no corresponding record in task_list.md — recommend Orchestrator confirm whether this project should be logged retroactively.
- T036 status/ownership per RACI flag #1 above — recommend confirming before it is treated as a live blocker for the EVA project's completion.
