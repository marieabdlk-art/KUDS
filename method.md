# KUDS method

KUDS frames novelty-oriented ideation as a **search process** rather than a one-shot prompt.

## Core design principles

1. Do not trust one-shot creativity
2. Generate many candidates
3. Separate divergence from selection
4. Use multiple evaluation axes
5. Penalize fake novelty
6. Refine only strong candidates
7. Compare against baseline, not intuition

## Current executable pilot

The current notebook pilot evaluates three modes:

- `baseline`
- `divergence_only`
- `full_pipeline`

In the current codebase, `full_pipeline` refers to a tuned internal selection variant inside the notebook workflow.

## Planned next step

The next major step is to externalize candidate selection more cleanly through:

- candidate pool generation
- candidate scoring
- pseudo-novelty filtering
- optional external selector

This aligns the execution layer more closely with the intended architecture described in project notes.