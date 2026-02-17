# TEST_RUNNER

Pre-flight workflow before executing tests. Ensures correct system and allocation.
Do not proceed to run tests until this workflow completes successfully.

## Steps

1) **Detect system**
   - Run: `hostname`, `uname -n`, check for `$SLURM_JOB_ID` or similar.
   - Classify: HPC login node, HPC compute node, local laptop/desktop.

2) **Determine test type**
   - Ask user or infer from context: CPU-only, GPU, multi-node, memory size.
   - If unclear, ask before proceeding.

3) **Check allocation (HPC only)**
   - Run `jinfo` (see reference/TEST_RUNNER_REFERENCE.md).
   - Parse output: rows with ST=R mean active allocation; NODES and NODELIST show resources.
   - Empty output or no rows = no allocation.

4) **Decide**
   - **Allocation OK**: Output the exact test command(s). Await user approval before executing.
   - **No allocation or wrong hardware**: Do NOT run sbatch. Provide:
     - Clear description of what resources are needed.
     - Example `salloc` or `sbatch` command(s) for the user to run.
     - Stop. Wait for user to allocate and re-run this workflow.

## Rules

- Never run sbatch, salloc, or submit jobs on the user's behalf.
- On local/laptop: skip allocation check; proceed to run tests if appropriate.
- On HPC login node without allocation: do not run heavy tests; instruct user to allocate.
- Include reference/TEST_RUNNER_REFERENCE.md when interpreting jinfo output.
