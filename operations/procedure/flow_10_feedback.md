# FLOW 10 — Post-Deliverable Feedback

**Triggers:** "client said", "feedback on", "client objections", "revision after feedback"

## AGENT SEQUENCE

```
Strategist (if strategic) → Deliverable owner agent → God Mode (if significant revision)
```

## PHASES

### Phase 1 — Triage
- **Agent:** Strategist
- **Task:** Evaluate whether the feedback requires a strategic change or is cosmetic
- **Output:** Brief triage note (inline, not a separate file, unless the change is significant)

### Phase 2 — Revision
- **Agent:** The deliverable's owner agent (whoever produced the original output)
- **Task:** Apply the revision
- **Output:** Updated deliverable, original version kept as backup

### Phase 3 — Quality Review (conditional)
- **Agent:** God Mode
- **Task:** Re-audit only if the revision is significant (not for cosmetic fixes)
- **Output:** Updated `god_mode_scorecard.md` if re-run

## NOTES
- If feedback is cosmetic: only the owner agent acts, no Strategist or God Mode involvement.
- If feedback is strategic: Strategist evaluates first, before the owner agent touches the deliverable.
- Always keep a backup of the pre-revision deliverable — never overwrite without one.
