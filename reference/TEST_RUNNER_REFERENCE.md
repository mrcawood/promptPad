# TEST_RUNNER_REFERENCE

Reference for workflows/TEST_RUNNER.md. Use when interpreting scheduler and system state.

## jinfo output format

`jinfo` (no arguments) shows the user's current job allocation. Example:

```
             JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
            580276          gh idv11059  mcawood  R       0:14      2 c621-[021-022]
```

| Column | Meaning | Example |
|--------|---------|---------|
| JOBID | Job identifier | 580276 |
| PARTITION | Slurm partition | gh |
| NAME | Job name | idv11059 |
| USER | Owner | mcawood |
| ST | Status (R=Running, PD=Pending, etc.) | R |
| TIME | Wall time used | 0:14 |
| NODES | Number of nodes allocated | 2 |
| NODELIST(REASON) | Node names or allocation reason | c621-[021-022] |

**Interpretation:**
- Rows with ST=R → user has an active allocation.
- Empty output or no rows → no allocation; user must request nodes.
- NODES indicates count; NODELIST shows node names (e.g., c621-021, c621-022).
- Node prefixes (e.g., c621) may indicate machine family; partition names may hint at GPU vs CPU.

## System detection

| Check | HPC login | HPC compute | Local |
|-------|-----------|-------------|-------|
| `$SLURM_JOB_ID` | unset | set | unset |
| `hostname` | Often "login" or "frontend" | Compute node name (e.g., c621-021) | Laptop hostname |
| `sinfo` / `squeue` | Usually available | Available | Not present |

## User handoff (no allocation)

When jinfo is empty or allocation is insufficient:

1. Describe required resources (nodes, GPUs, partition, wall time).
2. Provide example command for user to run, e.g.:
   - `salloc -N 2 -p gh -t 01:00:00` (interactive)
   - Or an sbatch script with appropriate `#SBATCH` lines
3. Do not execute salloc/sbatch; stop and wait for user.
