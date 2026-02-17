# ROLE_TRIGGERS

Phase-agnostic detectors. Scan PROGRESS.md and PRD (if present) to see if a trigger role should run before or alongside the primary role.

Apply on RETURN and after any role. See LAUNCH.md Step 3.5 and RETURN.md.

## Trigger → Role mapping

| Trigger | Role | When to pick |
|---------|------|--------------|
| uncertainty | HYPOTHESIST or FORECASTER | See rules below |
| risk | THREAT_MODELER or SKEPTIC | See rules below |
| correctness | VERIFIER | See rules below |
| ship | RELEASE_ENGINEER | See rules below |
| maintain | MAINTAINER | See rules below |
| context | CONTEXT_CURATOR | See rules below |
| integration | INTEGRATOR | See rules below |

## Concrete trigger rules

### Uncertainty / direction

**HYPOTHESIST** when PROGRESS contains any of:
- "not sure", "maybe", "evaluate", "options", "direction", "what should we do"
- Multiple competing approaches listed with no decision
- A blocked task due to "unknown requirement / dependency / external constraint"

**FORECASTER** when:
- Choosing between options with time/cost/likelihood tradeoffs
- Scheduling, estimating, or sizing work
- "deadline / milestone" mentioned

### Correctness / validation

**VERIFIER** when:
- Implementation touches critical invariants (data correctness, migrations, concurrency, parsing, reproducibility)
- "tests missing", "bug", "regression", "edge cases"
- Integrating with external APIs/tools

### Adversarial review

**SKEPTIC** (or THREAT_MODELER for security/privacy) when:
- Plan is high impact / hard to reverse
- Making assumptions with weak evidence
- Security, privacy, or reliability mentioned even once

### Shipping / ops

**RELEASE_ENGINEER** when:
- "ready to merge", "prepare release", "deploy", "rollout"
- "migration", "backwards compatibility", "version bump"

**MAINTAINER** when:
- Tech debt tasks are piling up
- "refactor", "cleanup", "deprecate", "simplify" shows up

### Context hygiene / coherence

**CONTEXT_CURATOR** when:
- PRD missing/partial but work is underway
- PROGRESS is long and messy, or "we keep revisiting this"
- Multiple chats/threads causing divergence

**INTEGRATOR** when:
- Multiple components touched in one change
- Interfaces/contracts unclear
- "end-to-end" or "cross-cutting" work
