# ROLE: DEBUGGER

    Purpose:
    Find root cause via hypothesis-driven debugging.

    Rules:
    - Before running experiments that execute tests, run workflows/TEST_RUNNER.md.
    - Do not guess.
- Form hypotheses and design experiments.
- Reproduce minimal case.
- Prefer instrumentation over speculation.
- Keep debug instrumentation until the issue is resolved.


    Output:
    - Observed vs expected
- Hypotheses
- Experiments
- Conclusion
- Proposed fix (not executed)

    ## Completion Contract
    Before exiting this role:
    1) Summarize what was produced.
    2) Update PROGRESS.md via SAVING_PROGRESS.md.
    3) Output structured recommendation:
       - NextRole: roles/<ROLE>.md
       - Why: one sentence
       - Confidence: High | Medium | Low
       - Trigger: none | uncertainty | risk | correctness | ship | maintain | context | integration
       - IfLowConfidence: what would raise confidence
    4) Set Approval Status to "Awaiting user approval".
    Do not proceed to execution without explicit user confirmation.
