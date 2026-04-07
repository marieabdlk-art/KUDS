# KUDS
### Controlled Divergence and Selection for LLM Idea Generation

[![Status: Research Prototype](https://img.shields.io/badge/status-research%20prototype-blue)](#current-status)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](./LICENSE)
[![Cite this repository](https://img.shields.io/badge/citation-CITATION.cff-orange)](./CITATION.cff)

KUDS is a research framework for generating **structurally nontrivial candidate ideas** with large language models.

Instead of asking an LLM for one “creative” answer, KUDS treats ideation as a **search problem**:

- generate baseline outputs
- push the model away from default solution paths
- build a pool of divergent candidates
- rank candidates across multiple axes
- penalize pseudo-novelty
- select or refine only the strongest ideas

> KUDS does **not** claim to prove true originality or access the model’s training data.
> It aims at a narrower and testable goal: finding candidate ideas that differ from baseline outputs while remaining coherent enough to develop further.

---

## Quick links

- [Why this exists](#why-this-exists)
- [What makes KUDS different](#what-makes-kuds-different)
- [Core pipeline](#core-pipeline)
- [Current status](#current-status)
- [Current validated takeaway](#current-validated-takeaway)
- [Baseline vs KUDS](#baseline-vs-kuds)
- [Quickstart](#quickstart)
- [Repository structure](#repository-structure)
- [Limitations](#limitations)
- [License](#license)
- [Collaboration](#collaboration)

---

## Why this exists

LLMs are often fluent but conventional.

When asked for “creative” ideas, they frequently return:

- renamed baseline solutions
- familiar abstractions
- decorative novelty without mechanism
- safe answers that look different but are structurally similar

KUDS is built to counter that.

Its main design principle is simple:

> **separate divergence from selection**

Generate broadly first.
Filter aggressively second.

---

## What makes KUDS different

KUDS is **not**:

- a prompt collection
- a wrapper around an API
- a one-shot creativity trick

KUDS **is**:

- a search-and-selection framework for novelty-oriented ideation
- a research prototype for candidate generation and ranking
- a notebook-first evaluation artifact for studying non-banal LLM outputs

---

## Core pipeline

```text
task
  -> baseline generation
  -> divergence operators
  -> candidate pool
  -> scoring
  -> pseudo-novelty filtering
  -> selection
  -> optional refinement
```

Divergence operators include:

- pattern deconstruction
- distant analogy transfer
- conceptual conflict induction
- recombination of functional fragments

Selection evaluates candidates across:

- **novelty**
- **mechanism distinctness**
- **coherence**
- **testability**
- **interestingness**
- **banality resistance**

KUDS also penalizes pseudo-novelty such as:

- decorative abstraction
- renamed baseline ideas
- hidden contradiction
- verbosity without mechanism
- banal solutions in unusual language

---

## Current status

**Status:** research prototype / architecture draft

KUDS is currently a notebook-first research artifact with real pilot signal, but it should still be read as an experimental framework rather than a finished product.

---

## Current validated takeaway

Early project notes emphasized the divergence layer as the strongest validated component. In the **current tuned 10-task pilot**, KUDS still clearly outperforms baseline prompting on judged novelty, mechanism distinctness, and banality resistance, and the tuned `full_pipeline` now slightly outperforms `divergence_only` on average by improving coherence and testability while preserving substantial structural novelty.

This suggests that:

- baseline prompting remains highly conventional
- divergence is a real source of structural novelty
- calibrated internal selection can add value without collapsing back into safe baseline-like outputs
- external selection is the next layer to test as a separate component

### Pilot summary

| Mode | Novelty | Mechanism Distinctness | Coherence | Testability | Interestingness | Banality Resistance |
|---|---:|---:|---:|---:|---:|---:|
| Baseline | 2.0 | 2.0 | 4.0 | 4.1 | 2.0 | 1.6 |
| Divergence-only | 4.0 | 4.0 | 3.0 | 3.1 | 4.0 | 4.0 |
| Full pipeline | 4.2 | 4.2 | 3.8 | 3.6 | 4.2 | 4.2 |

**Task wins:** Full pipeline **6/10**, Divergence-only **4/10**

### Interpretation

The baseline mode produced coherent but mostly conventional ideas.

The divergence-only mode produced a strong increase in novelty and mechanism distinctness, but with lower coherence and testability.

The tuned full pipeline preserved most of the novelty gains while improving idea quality along more practical dimensions. In this pilot, it achieved the best overall balance between originality and development potential.

---

## Baseline vs KUDS

**Task:** Design a new mechanism for long-context LLM memory.

### Baseline output
- retrieval improvements
- anchoring schemes
- graph-like structuring
- decay-and-reinforcement mechanisms

### KUDS-style output
- temporal resonance memory
- antibody-like memory agents
- counterfactual memory forks
- semantic pressure fields
- autocatalytic memory chains

These are not valuable merely because they sound stranger.
They are valuable when they introduce a **different mechanism** while remaining interpretable enough to evaluate or prototype.

---

## Quickstart

The easiest way to reproduce the current pilot is to run the notebook workflow in `notebooks/`.

Recommended order:

1. `notebooks/demo.ipynb` — smaller tuned run
2. `notebooks/eval.ipynb` — 10-task pilot evaluation

Typical compared modes in the current pilot:

- `baseline`
- `divergence_only`
- `full_pipeline`

The current pilot evaluates these modes along:

- novelty
- mechanism distinctness
- coherence
- testability
- interestingness
- banality resistance

The notebook uses an API-based workflow and includes a cell where you can insert your OpenRouter API key manually.

---

## Example use cases

KUDS can be used for:

- scientific hypothesis ideation
- product concept generation
- design-space exploration
- speculative engineering
- educational system concepts
- research assistance
- agent-memory design
- non-banal interface ideation

---

## Repository structure

```text
kuds/
├── notebooks/
│   ├── demo.ipynb
│   ├── eval.ipynb
│   └── archive/
├── data/
│   └── benchmark_tasks.json
├── prompts/
│   └── kuds-ideation-engine.skill
├── docs/
│   ├── method.md
│   ├── structural_compressor.md
│   ├── agent_memory_layer.md
│   └── pilot_results.md
├── results/
│   ├── pilot_10tasks_avg_scores.csv
│   ├── pilot_10tasks_winner_counts.csv
│   ├── pilot_10tasks_summary.json
│   └── README.md
├── .gitignore
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── SECURITY.md
├── README.md
├── LICENSE
├── requirements.txt
└── CITATION.cff
```

---

## Limitations

KUDS does not claim:

- proof of philosophical originality
- proof that an idea never appeared in training data
- guaranteed usefulness of unusual outputs
- a finished production-ready selector
- a validated external selection layer in the current pilot

KUDS does claim:

- a reproducible search process for novelty-oriented generation
- explicit separation of divergence and selection as a design principle
- a way to rank structurally nontrivial candidate ideas relative to baseline outputs
- early pilot evidence that tuned search-and-selection can outperform baseline prompting

---

## License

This repository is released under the **MIT License**.

This is the simplest option for broad reuse, experimentation, and remixing while preserving attribution through the repository history and citation file.

---

## Collaboration

KUDS is available for:

- novelty-oriented ideation experiments
- prompt/workflow design for R&D teams
- pseudo-novelty analysis in LLM outputs
- structured concept generation and evaluation
- experimental agent-memory design

For research or commercial collaboration, contact: `your_email@example.com`