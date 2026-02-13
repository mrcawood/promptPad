# SAVING_PROGRESS

We are pausing work.

Create or update PROGRESS.md to act as a persistent LLM handoff file.

Purpose:
Another LLM (or a future session) should be able to resume immediately with zero chat history.

Rules:
1) Do not delete existing content unless it is clearly incorrect or contradictory.
2) Merge new information into existing sections where appropriate.
3) Prefer additive updates over rewrites.
4) Be concise, technical, and factual. No narrative fluff.

Update these sections (create if missing):

## Project Summary
1-2 paragraphs describing what this project is and its goal.

## Current Phase
One of: Discovery, Architecture, Planning, Implementation, Debugging, Optimization, Paused.

## Current State
What works, what does not, what is incomplete.

## Approval Status
One of: Awaiting user approval, Approved to proceed, Blocked on decisions.

## Key Decisions
Important architectural/design decisions already made and why.

## Decision Records
For each resolved decision:
- Decision
- Options
- Selected
- Rationale
- Date (YYYY-MM-DD)

## Active Tasks
Concrete TODO list with checkboxes. Mark the proposed next task.

## Open Questions
Unresolved issues. Mark each as blocking or non-blocking.

## Technical Context
Critical details needed to avoid re-discovery:
- repo structure
- key files
- commands
- configs
- dependencies
- assumptions

## Constraints / Requirements
Hard requirements, non-goals, preferences.

## Recent Changes (Today)
Bullets summarizing what was done this session.

## Proposed Next Step (Requires Approval)
- Recommendation
- Brief justification
- Confidence (High/Medium/Low)
- Alternatives (if relevant)
End with: Status: Awaiting user approval.

## Git Status (Optional)
If the project uses git, include:
- current branch
- related PR (if any)
- merge target
- commits this session (hash + 1 line)
- tests run (per commit or per session)

Output:
Modify PROGRESS.md only. Do not explain what you did.
