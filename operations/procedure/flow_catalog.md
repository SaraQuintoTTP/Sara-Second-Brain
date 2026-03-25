# FLOW CATALOG — TTP Agency v5.0

> The Orchestrator consults this file to determine which procedure to activate
> based on Sara's request. If unmapped, follow the Unmapped Request Protocol below.

| # | Flow | Triggers | Procedure File |
|---|------|----------|----------------|
| 1 | Full Marketing Strategy | "strategy for", "marketing plan", "positioning", "launch" | flow_01_marketing_strategy.md |
| 2 | Pre-Sales (5 phases) | "new prospect", "qualification", "proposal for", "quote" | flow_02_presales.md |
| 3 | Content / Social Only | "editorial plan", "content for", "social for", "PED" | flow_03_content_social.md |
| 4 | Review / Update | "review", "update", "modify pricing", "refresh" | flow_04_review.md |
| 5 | Business Coaching | "coaching", "session", "goals", "personal growth", "unblock" | flow_05_coaching.md |
| 6 | Audit / Quality Review | "audit", "quality review", "check deliverable" | flow_06_audit.md |
| 7 | Training / Academy | "course", "training", "workshop", "academy", "teaching material" | flow_07_training.md |
| 8 | Web / Tech / Automations | "website", "seo", "analytics", "automations", "email marketing", "funnel" | flow_08_web_tech.md |

---

## UNMAPPED REQUEST PROTOCOL

When Sara's request does not match any flow:

1. Orchestrator **recognizes** the request has no mapped flow
2. Orchestrator **proposes** a plan to Sara:
   - Which agents to activate and in what order
   - Rationale for the sequence
   - Complexity estimate (light / medium / heavy)
3. Sara **decides**:
   - a) Approve → Orchestrator executes
   - b) Modify → Orchestrator adapts the plan
   - c) "Make it permanent" → Orchestrator executes AND creates a new flow in `/operations/procedure/flussi_custom/flow_[name].md`
4. If Sara chooses (c), the new flow becomes available for future requests
