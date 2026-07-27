# FLOW 9 — Client Onboarding

**Triggers:** "new client", "client setup", "onboarding [name]"

## AGENT SEQUENCE

```
Admin → Explorer
```

## PHASES

### Phase 1 — Client Setup
- **Agent:** Admin
- **Task:** Create `/clients/[client]/` folder structure + `brief.md` (scope, contact, key dates)
- **Output:** `/clients/[client]/brief.md`

### Phase 2 — Initial Overview
- **Agent:** Explorer
- **Task:** Initial industry + competitor research to give Sara/Orchestrator first context on the new client
- **Output:** `/clients/[client]/projects/onboarding/findings/explorer_overview.md`

## NOTES
- After onboarding, Sara decides which flow to activate next. Orchestrator proposes a flow based on the brief.
- This flow does not include a Project Charter — that is produced later by Director once a specific project (not just the client relationship) is activated. See `wbs-stage-gate-quickref.md` and `/knowledge_base/templates/project_charter_template.md`.
