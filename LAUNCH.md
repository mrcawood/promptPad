# LAUNCH - Workflow Dispatcher

Always follow this cycle:
1) Build context from artifacts.
2) Identify the next task (phase or decision).
3) Architect and/or plan.
4) Update PROGRESS.md when it changes.
5) Stop and present a proposal.
6) Ask for user approval before any execution.

## Step 1 - Artifact Inventory
Look for:
- PRD (e.g., prd.md, PRD.md, requirements.md)
- PROGRESS.md
- Repo clues (README, src/, tests/, pyproject.toml, package.json, etc.)
List what you found.

**Run outcome:** When the next task depends on whether a run/test succeeded or failed, read the most recent log in the documented logs path (e.g. PROGRESS.md §Logs) yourself. Do not ask the user for results you can ascertain from artifacts.

## Step 2 - Classify Project State
- RESUME: PRD + PROGRESS exist
- PARTIAL_START: PRD exists, PROGRESS missing
- PARTIAL_CONTEXT: PROGRESS exists, PRD missing (normal when Current Phase is Debugging)
- NEW: no artifacts

## Step 3 - Decision Gates
PARTIAL_START:
1) Create PROGRESS.md from the PRD using SAVING_PROGRESS.md.
2) Identify the next milestone from the PRD.
3) List any open decisions that block planning.
4) If blockers exist, recommend roles/RESEARCHER.md to evaluate and propose defaults.

RESUME:
1) Read PROGRESS.md.
2) Identify the next phase/task from PROGRESS.md.
3) Recommend roles/DEVELOPER.md when the next task is implementation (code to write, fix to apply, refactor, or optimization to implement).
4) Recommend roles/PLANNER.md if the path is concrete but not yet planned; otherwise roles/ARCHITECT.md.

PARTIAL_CONTEXT:
1) Read PROGRESS.md.
2) If Current Phase is Debugging: treat as for RESUME. Do not expect or warn about missing - PRD often runs ad-hoc.
3) Otherwise: recommend mode as for RESUME, but warn that PRD is missing.

NEW:
1) Recommend roles/ARCHITECT.md first.

## Step 3.5 - Trigger Scan (Layer 2)
Before proposing, scan PROGRESS.md (and PRD if present) using reference/ROLE_TRIGGERS.md.
If a trigger matches, the triggered role may preempt or run before the primary role.
Output: Primary role + Trigger (if any) + Triggered role (if any).

## Step 4 - Proposal Format
Include:
- Project state
- Artifacts found
- Blocking decisions (if any)

Then (structured output):
- NextRole: roles/<ROLE>.md (primary; Layer 1)
- Trigger: none | uncertainty | risk | correctness | ship | maintain | context | integration (Layer 2; if set, triggered role may run first)
- TriggeredRole: roles/<ROLE>.md (only if Trigger is set)
- Why: one sentence
- Confidence: High | Medium | Low
- IfLowConfidence: what would raise confidence
- Alternatives (if relevant)

PROGRESS.md acknowledgment:
- Say whether PROGRESS.md was updated this turn. If not, say why.

Change-management gate (optional):
- If doing git-based dev, propose: branch name, commit plan, tests to run.
- Never push/merge or rewrite history without explicit user approval.

Approval gate:
- End with: "Status: Awaiting user approval."
- Ask: "Do you approve proceeding with the recommended role, or should we adjust the plan?"
