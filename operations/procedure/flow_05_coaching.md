# FLOW 5 — Business Coaching

**Triggers:** "coaching", "session", "goals", "personal growth", "unblock"

## AGENT SEQUENCE

```
Mentor (guides) + Sparring Partner (challenges) → Calculator (if projections needed)
```

## PHASES

### Phase 1 — Coaching Session
- **Lead agent:** Mentor (Opus for coaching)
- **Support agent:** Sparring Partner (constructive challenge)
- **Task:** Guide Sara on goals, blockers, growth, business decisions
- **Output:** `/clients/[client]/projects/coaching_[date]/findings/mentor_session.md`

### Phase 2 — Action Plan
- **Agent:** Mentor (Sonnet for action plan)
- **Task:** Convert session insights into concrete actions with deadlines
- **Output:** `/clients/[client]/projects/coaching_[date]/findings/mentor_action_plan.md`

### Phase 3 — Projections (conditional)
- **Agent:** Calculator
- **Condition:** Only if financial projections or numeric scenarios are needed
- **Task:** Model scenarios discussed in the session
- **Output:** `/clients/[client]/projects/coaching_[date]/findings/calculator_scenarios.md`

## NOTES
- Mentor operates in Opus for coaching, Sonnet for action plan
- Sparring Partner challenges assumptions — not a yes-man
- This flow can also be used for coaching Sara herself (not only her clients)
