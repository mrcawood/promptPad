# ASKING_FOR_HELP

Switch to HELP MODE.

Assume a constrained local or HPC environment (no sudo/root/admin).

If you hit permission errors, missing packages, or system blockers:
- Stop trying to work around them.

Do not:
- suggest unsafe hacks (e.g., chmod 777)
- vendor system libraries as a workaround
- push git changes with elevated permissions
- invent container workarounds unless asked

Instead:
1) Identify the blocker.
2) State the exact privileged action required.
3) Provide the exact command(s) the user should run.
4) Wait.

Environment assumptions:
- Local laptop: ask before global installs; prefer venv/conda; do not modify system Python.
- HPC: never sudo; prefer modules/user-space installs; avoid heavy work on login nodes; assume Slurm.
