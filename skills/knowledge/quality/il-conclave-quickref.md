---
framework: Il Conclave — Single-Model LLM Council
author: SOsintOps (github.com/SOsintOps/il-conclave)
type: quickref
category: quality
status: active
version: 1.0
installed: ~/.claude/skills/il-conclave/SKILL.md
---
# IL CONCLAVE — Quick Reference

## Overview
Single-model decision council that forces analytical divergence through 6 structured procedures.
**Core principle:** divergence from procedures (structurally incompatible frameworks), not personas.
**Use when:** the cost of being wrong is high. Not for operative tasks or simple yes/no questions.

## When to Use
- Strategic pivots, product/pricing direction, irreversible resource allocation
- Proposals >€20k or decisions that damage a client relationship if wrong
- Sara's internal TTP decisions (architecture choices, agent assignments, system evolution)

## When NOT to Use
- Factual lookups, summaries, content creation, task execution
- Simple questions without a real tradeoff (no stakes → no council)
- God Mode already covers quality audit of deliverables — use Il Conclave for strategic decisions

## The 6 Archetypes

| Archetype | Framework | Mission |
|-----------|-----------|---------|
| **Savonarola** | Pre-Mortem (Gary Klein) | Assumes failure, reconstructs why — surfaces hidden risks |
| **Galileo** | 5 Whys + Constraint Map | Drills to root cause, separates real vs assumed constraints |
| **Marco Polo** | Opportunity Cost Matrix | Finds the upside everyone ignores, compares alternatives |
| **Falcone** | ACH — Competing Hypotheses (CIA) | Generates rival hypotheses, tests each against evidence |
| **Machiavelli** | Steelman-then-Attack | Strengthens the recommendation first, then demolishes it |
| **Salomone** | Confidence-Weighted Synthesis | Weighs all advisors by confidence (1-10), can override majority |

## Operative Sequence (6 phases)

1. **Framing** — Scan workspace (CLAUDE.md, memory/), reframe question neutrally
2. **4 Advisors (parallel)** — Savonarola, Galileo, Marco Polo, Falcone analyze independently
3. **Anonymous Peer Review** — Responses anonymized A-D, ordering randomized
4. **Debate Round** — Each advisor sees critiques, responds: CONCEDE / DEFEND / UPDATE confidence
5. **Machiavelli** — Steelman (strongest version of recommendation) → then demolition
6. **Salomone** — Confidence-weighted synthesis → verdict + first concrete action + timeline

## Confidence Scoring
Each of the 4 advisors rates confidence 1-10 + key uncertainty + data that would change their mind.
Salomone weights the final verdict by post-debate confidence. Can override majority if divergence is justified.

## Output Files
- `council-transcript-[topic].md` — Full text: all advisors, peer reviews, debate, synthesis
- `council-report-[topic].html` — Visual: hero verdict, confidence dashboard, collapsible sections

## Activation Triggers
"council this:", "conclave:", "pressure-test this:", "stress-test this:", "debate questo:", "council this:"

## In TTP Context
- Activated via flag `conclave_protocol: true` in Sparring Partner Task prompt
- Replaces the standard 4-tool sequence (First Principles + Pre-Mortem + Inversion + Steel Man)
- Client output: `/clients/[c]/projects/[p]/findings/conclave_[topic].md + .html`
- Sara/TTP output: `/system/findings/conclave_[topic]_[data].md + .html`
- Full procedure: `~/.claude/skills/il-conclave/SKILL.md`
