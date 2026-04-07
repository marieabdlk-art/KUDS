# Pilot results

## Current tuned 10-task pilot

Evaluated modes:
- baseline
- divergence_only
- full_pipeline

Judged dimensions:
- novelty
- mechanism distinctness
- coherence
- testability
- interestingness
- banality resistance

## Aggregate summary

| Mode | Novelty | Mechanism Distinctness | Coherence | Testability | Interestingness | Banality Resistance |
|---|---:|---:|---:|---:|---:|---:|
| Baseline | 2.0 | 2.0 | 4.0 | 4.1 | 2.0 | 1.6 |
| Divergence-only | 4.0 | 4.0 | 3.0 | 3.1 | 4.0 | 4.0 |
| Full pipeline | 4.2 | 4.2 | 3.8 | 3.6 | 4.2 | 4.2 |

Task wins:
- Full pipeline: 6/10
- Divergence-only: 4/10

## Interpretation

The current pilot supports a narrower but stronger claim than "creative prompting works":

- baseline prompting is coherent but highly conventional
- divergence creates real structural novelty
- tuned internal selection can improve practical quality without fully collapsing novelty
- the next major research question is whether an external selector improves further or starts smoothing too aggressively