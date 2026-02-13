# promptPad

A small, file-based control framework for running LLM agents in a predictable, human-in-the-loop workflow.

![Demo](assets/demo.gif)


Design goals:
- Deterministic startup and resume behavior
- Clear role separation (Architect vs Planner vs Debugger, etc.)
- Persistent handoff state via PROGRESS.md
- Explicit approval gates (no surprise execution)
- Low token overhead (short, focused prompts)

## Directory layout

- BOOTSTRAP.md - "bootloader" prompt: forces the agent to load LAUNCH.md first
- LAUNCH.md - dispatcher/state machine: inventory artifacts, pick next role, ask for approval
- RETURN.md - resync after tangents: re-anchor to PROGRESS.md and propose the next step
- SAVING_PROGRESS.md - schema + rules for creating/updating PROGRESS.md

- workflows/ - reusable workflow prompts
  - TDD.md - test-driven development sprint loop
  - ASKING_FOR_HELP.md - switch to guidance when blocked by privileges/environment
  - GIT_WORKFLOW.md - optional git change-management rules

- roles/ - role prompts (each ends in an approval gate)
  - ARCHITECT.md
  - PLANNER.md
  - RESEARCHER.md
  - DEBUGGER.md
  - DEVELOPER.md (writes code; others produce plans/proposals)
  - OPTIMIZER.md
  - REFACTORER.md
  - HPC_USESPACE.md
  - CHANGE_MANAGER.md (optional; git hygiene)

- reference/ - optional reference context (only include when needed)
  - DOCUMENTATION_GUIDE.md
  - LMOD_TESTING.md

## How to use

### Start a session (recommended)
Give the agent this instruction:

- "Your instructions are in BOOTSTRAP.md"

BOOTSTRAP.md forces the agent to load LAUNCH.md and begin the dispatcher flow (artifact inventory -> proposal -> approval).

### Resume work
If you are resuming a project, ensure these artifacts exist in the project root:
- PRD (e.g., prd.md)
- PROGRESS.md

Then start the agent via BOOTSTRAP.md. LAUNCH.md should classify the state as RESUME and propose the next role.

### Recover from a tangent
When a discussion drifted and you want to get back on rails:

- "Tangent complete. Run RETURN.md"

RETURN.md re-reads PROGRESS.md, proposes the next unfinished task, and asks for approval.

### Save state / handoff
When you want to checkpoint the work (end of day, context window pressure, etc.):

- "Run SAVING_PROGRESS.md"

This updates PROGRESS.md using a consistent schema so a future session can resume quickly.

## Optional: git hygiene / change-management

If the project uses git and you want a normal, traceable history (feature branches, small commits):

- Ask the agent to apply workflows/GIT_WORKFLOW.md before implementation work, or use roles/CHANGE_MANAGER.md when planning commits.

If you are not using git (or do not care about history quality), ignore these files.

## Typical cycle (human-in-the-loop)

1) BOOTSTRAP -> LAUNCH: build context + propose next role
2) Approve role (Architect/Researcher/Planner/Debugger/etc.)
3) Role does its work (no execution unless approved)
4) Update PROGRESS.md via SAVING_PROGRESS.md
5) Stop + ask for approval before the next step
