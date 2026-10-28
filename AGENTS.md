# AGENTS.md for ForestLUC

## Project
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

## AI-ready data
- Before applying the machine learning commands, data must be verified using the AI-ready rubric below.

# AI-readiness rubric: instructions for an assistant

ESS 469/569, Session 10 (Fri Oct 23) and notebook 2.13. Give this file to your assistant together with the
dataset's documentation (paper, README, metadata files) or a clone of the repository. Copy it into your
project's AGENTS.md if you want every session to use it.

## How to score

- Score each of the 11 criteria 0, 1 or 2:
  0 = missing; 1 = present but incomplete; 2 = another team could verify it from the evidence you quote.
- For every score, quote the evidence: a file path and line, a page and section, a URL, or a count you computed.
- If you cannot find evidence, write "not found" and score 0. Do not infer a score from the dataset's
  reputation or from what similar datasets usually provide.
- Count independent units (stations, events, regions, years, instruments), not rows.
- Report your answer as a table with columns: criterion, score, evidence, what is missing.

## Analysis readiness

- A1 Provenance. Name the source, version or retrieval date, license, and citation. State whether any part is
  synthetic or augmented.
- A2 Homogenization. Check that units, reference frame, coordinates, time base and sampling are consistent
  across the record. List instrument or processing changes and whether they are corrected or flagged.
- A3 Quality and gaps. Find quality flags, missing values, sentinel values (e.g. -999, 0) and values below a
  detection limit. Say what caused each kind of gap if the documentation says.
- A4 Structure and metadata. Name the file format, the shape of one sample, and whether variables and units are
  described in a file a script can read.

## AI readiness

- B1 Diversity. Count the independent units the data cover and the range of conditions (regions, seasons,
  event types, magnitudes, instruments).
- B2 Distribution. Report the distribution of targets or classes and of key inputs; give the share of the rarest
  class or the tail of the target; say how it compares with the population the model will face.
- B3 Noise. Report what is known about instrumental noise (sensor, processing) separately from natural
  variability; give a noise level or signal-to-noise ratio if documented.
- B4 Augmentation. List transformations that keep the physics (e.g. time shifts, adding noise at the measured
  level, synthetic events with known truth) and ones that would break it.
- B5 Labels. Name who or what produced the labels, how, and any measure of their consistency or uncertainty.
  If there are few labels, say whether abundant unlabeled data could support self-supervised learning.
- B6 Dimensionality. Give the number of samples N, the dimension D of one sample (values per sample), N/D, and
  any estimate of the intrinsic dimension (e.g. variance captured by a few principal components).
- B7 Partitioning. Say whether train, validation and test sets are shipped. For the test set, name the axis on
  which it lies outside the training domain: statistical (distance in feature space), spatiotemporal (held-out
  period or region), or physical (different process, event size, or physics). Check that preprocessing
  statistics are computed on the training set only and that splits are made by independent unit.

## Before you report

- Re-read each score of 2 and confirm the quoted evidence would let another team check it.
- List the three criteria with the lowest scores and what the dataset's authors would need to add.
