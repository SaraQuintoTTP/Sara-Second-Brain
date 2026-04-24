# QUICK REFERENCE PROTOCOL — TTP Agency
## v1.1 — updated 2026-04-24

## PURPOSE
Defines the mandatory quality standard for writing Quick References (Tier A, 2-tier Knowledge System — see Operative v5.0, §11).
Applies to: Artisan (primary author), Orchestrator (when spawning Artisan for Knowledge Processing), God Mode (when auditing Quick References).

---

## PART 1 — MANDATORY CHECKLIST (v1.1 — 7 criteria)

Every Quick Reference must satisfy ALL 7 criteria before being marked `status: active`.

### Criterion 1 — Explicit scope boundaries
- `When to use`: single sentence identifying the activation trigger.
- `When NOT to use`: 3-5 bullets redirecting to other frameworks when this one is wrong.

### Criterion 2 — Operational core with PMI-typed examples
The framework's central component (matrix, funnel, scorecard, etc.) must be accompanied by **example-types per cell / per step** adapted to the Italian PMI / micro-enterprise context — not abstract descriptions only.

### Criterion 3 — Declared effort-time for a PMI session
State how many hours / days the framework takes to apply properly in a typical Italian micro-PMI (sole practitioner → ~15-20 team members, fatturato fino a ~10-12M€).

### Criterion 4 — Cross-references by real relevance
At least 4 links to related frameworks, selected ONLY for pragmatic relevance. Do NOT force citations to local frameworks (e.g., Sportelli) unless the domain genuinely overlaps.

### Criterion 5 — Common mistakes anchored to observable PMI patterns
Bullets must reflect real mistakes Sara has seen or would plausibly see in Italian PMI consulting — not generic textbook errors.

### Criterion 6 — Concrete PMI Quick Example
One example case with: a specific decision to make, plausible numbers, framework applied, GO/NO-GO criterion. Vary the sectors across the knowledge base (avoid food/horeca saturation). Cover both liberi professionisti AND production/service PMI up to ~15-20 people, ~10-12M€ fatturato.

### Criterion 7 — Verifiability of strong claims (NEW in v1.1)
**Every strong claim in the Quick Reference must be one of:**
- **Cited** — with original source (author, work, year), even inline in the body.
- **Declared explicitly as TTP extrapolation / operational corollary**, naming the supporting secondary sources.
- **NEVER presented as the author's principle if it is not.**

**Rationale**: prevents hallucinated attribution (e.g., attributing to Porter a prescription Porter never wrote) from propagating into agent outputs and client deliverables.

**Self-check question before marking `status: active`**:
> For every strong statement in this file — can I point to a published source, or have I declared it as my own extrapolation?

---

## PART 2 — FIRST PRINCIPLES THINKING (mandatory method)

When adapting a framework designed for large enterprises to Italian PMI / micro-enterprises, DO NOT reason by analogy ("big companies do X, let's do a smaller X"). Apply First Principles Thinking.

### Sources (verified)
- Aristotele, *Metafisica*, I.3 — prōtai archai (primi principi)
- Richard Feynman — *"The first principle is that you must not fool yourself, and you are the easiest person to fool."*
- Farnam Street (fs.blog), "First Principles: The Building Blocks of True Knowledge"
- Stanford Graduate School of Business / eCorner — materials on first-principles reasoning
- Elon Musk (popularizer): *"Boil things down to their fundamental truths and reason up from there — not by analogy."*

### Operational process (4 steps)

```
1. IDENTIFY ASSUMPTIONS
   → What does the framework assume about its user?
     (available resources, data, time, team size, decision velocity)

2. DECOMPOSE TO FUNDAMENTALS
   → What is the underlying problem the framework solves?
   → What fundamental truths make the framework work?
     (economic laws, human behavior patterns, competitive dynamics)

3. MAP PMI CONSTRAINTS
   → What is different in an Italian PMI context?
     (limited budget, solo/small team, speed over thoroughness,
     the owner is the decision-maker and operator at the same time)

4. RECONSTRUCT NATIVELY
   → Rebuild the framework starting from the fundamental truths PLUS the PMI constraints.
   → Do NOT shrink the original — redesign it for the context.
   → Document what was kept, what was cut, what was added, and WHY.
```

### Worked example — Porter 5 Forces adapted to PMI

- **Assumption in original framework**: user has resources to conduct 360° analysis on all 5 forces (analytical staff, time, industry data).
- **Fundamental truths**:
  (a) Profit is shaped by industry structure, not just firm ability (Porter 1980 — documented).
  (b) Competitive forces have unequal weights on margin (Porter HBR 2008 — documented).
  (c) Strategic resources are finite and must be allocated where they produce most return (Resource-Based View, Barney 1991 — documented).
- **PMI constraints**: titolare is CEO + analyst + operator; no analytical staff; industry data hard/expensive to obtain; decision needed in days, not months.
- **Reconstruction**: identify the dominant force first, concentrate strategy there; extend analysis to the other 4 only if resources allow. Declare this explicitly as TTP corollary, supported by Pareto (Koch 1997) and Theory of Constraints (Goldratt 1984) applied to positioning.

**Key point**: the reconstruction is NOT a miniaturized Porter. It is a **native TTP/PMI version** built from first principles, with transparent attribution.

---

## PART 3 — VERIFICATION (before marking `status: active`)

1. Checklist 7/7 ✓
2. FPT applied where adaptation was needed ✓
3. Strong claims either cited or declared as extrapolation ✓
4. Italian PMI example present, numbered, with GO/NO-GO ✓
5. Length within budget (Quick Reference ≤ 120 lines; Deep ≤ 350) ✓

---

## CHANGELOG
- **v1.0 (2026-04-24)** — first 6-criteria checklist, derived during SWOT quickref review.
- **v1.1 (2026-04-24)** — added Criterion 7 (verifiability) and Part 2 (First Principles Thinking) after Sara's challenge on Porter Core Thesis hallucination risk. Retroactively applied to SWOT (added Weihrich 1982 citation) and Porter (Core Thesis reformulated with explicit source attribution).
