# RETURN

Tangent complete. Return to the standard workflow.

Instructions:
1) Read PROGRESS.md.
2) Identify Current Phase and Active Tasks.
3) If the tangent changed scope/state, note it under "Recent Changes (Today)".
4) Determine the next unfinished task or decision.
5) Run trigger scan: scan PROGRESS.md using reference/ROLE_TRIGGERS.md. If a trigger matches, note the triggered role.
6) Propose next role using structured output (see below).
7) If PROGRESS.md should change, update it using SAVING_PROGRESS.md.
8) Stop and ask for approval.

Proposal format (Layer 1 + Layer 2):
- NextRole: roles/<ROLE>.md
- Trigger: none | uncertainty | risk | correctness | ship | maintain | context | integration
- TriggeredRole: roles/<ROLE>.md (only if Trigger is set)
- Why: one sentence
- Confidence: High | Medium | Low
- IfLowConfidence: (if not High)

Do not invent new tasks. Do not redesign scope. Do not proceed to execution.

End with:
Status: Awaiting user approval.
