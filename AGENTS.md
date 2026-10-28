# AGENTS.md for MLGEO2026_UWNETID

## Project
Course repository for ESS 469/569, Autumn 2026: homeworks and the final project.
Every number and figure here must be regenerated from a fresh clone using
the commands in README.md.

## Environment and compute
- Run all code through `pixi run`; add packages only with `pixi add`, and
  commit pixi.toml and pixi.lock together.
- Do not install packages with pip or conda outside pixi.

## Data and provenance
- Fetch values that a provider publishes (station coordinates, velocities,
  catalogs) and cite the URL and retrieval date; do not recompute or retype them.
- Download data with a script in this repository, not by hand, and record the
  dataset DOI or URL, version, and retrieval date in README.md.
- Never modify raw data files; write processed data to a separate folder.

## Code and workflow
- Use paths relative to the repository root; no absolute paths such as /Users/...
- Every notebook must run top to bottom after Restart Kernel and Run All Cells.
- Every reported number and figure comes from a command listed in README.md.

## Reporting and credit
- State the reference frame, units, and time window of every number.
- Mark AI-drafted commits: "AI-assisted: <tool>, <what it drafted>".

## Verification
- Run `pixi run smoke` before reporting any result, and show its last line.
- Report the exact commands you ran and the commit hash they ran on.
- If a check fails or a value cannot be fetched, say so; do not substitute an estimate.
