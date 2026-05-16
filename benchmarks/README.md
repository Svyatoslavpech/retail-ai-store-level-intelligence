# GRADE Benchmarks

**Author:** Slav Pechenevskyi  
**Version:** 1.0 | 16 May, 2026  
**Status:** In development

---

## Overview

This directory contains evaluation benchmark materials for the GRADE Framework — structured test cases, example outputs, and scoring examples for each of the 10 failure patterns.

Benchmarks serve two purposes:

1. **Empirical grounding** — providing the evidence base for the operational thresholds defined in the GRADE Severity Matrix
2. **Practical templates** — enabling teams to run GRADE evaluations against their own Store AI deployments

---

## Structure

```
benchmarks/
├── README.md                          ← this file
├── pattern-01-granularity/
│   ├── test_queries.md                ← 10 store-level vs aggregate queries
│   └── results_example.md            ← example agent responses + scoring
├── pattern-02-prompt-variance/
│   ├── test_queries.md                ← clean vs floor prompt pairs
│   └── results_example.md
├── pattern-03-asymmetric-error/
│   ├── test_queries.md                ← role-differentiated error scenarios
│   └── results_example.md
├── pattern-06-state-drift/
│   ├── conversation_sequences.md      ← 8-12 turn evaluation sequences
│   └── results_example.md
└── pattern-10-sycophancy/
    ├── pushback_prompts.md            ← 20 pushback sequences
    └── results_example.md
```

*Additional pattern benchmarks added as development continues.*

---

## Benchmark Development Approach

### Phase A — Synthetic Benchmarks (Current)
Test queries and example outputs constructed from practitioner experience across retail operations (Walmart) and LLM evaluation work (Outlier, IBM Watsonx). Synthetic benchmarks establish the evaluation methodology and provide usable templates.

### Phase B — Real Evaluation Runs (In Progress)
Actual evaluation sessions running GRADE test queries through current LLM systems (GPT-4o, Claude, Gemini). Results documented with model, date, prompt, response, and GRADE score. This phase converts heuristic thresholds into empirically grounded baselines.

---

## How to Use These Benchmarks

### Running your own GRADE evaluation

1. Choose a pattern to evaluate (recommend starting with Core GRADE: P1, P3, P6, P10)
2. Open the corresponding `test_queries.md.`
3. Run each query through your Store AI Agent
4. Score responses using the criteria in `GRADE_framework.md.`
5. Compare against the example scoring in `results_example.md.`
6. Calculate your dimension score using the GRADE Radar template

### Contributing evaluation results

If you run GRADE evaluations and want to contribute results to the benchmark dataset, open a pull request or contact the author directly. Contributions that expand the empirical base of the framework are welcome.

---

## Priority Patterns for Benchmark Development

Based on severity classification:

| Priority |       Pattern       |                      Reason                     |
|----------|---------------------|-------------------------------------------------|
| 1        | P10 Sycophancy      | Most dangerous, most undertested                |
| 2        | P1 Granularity      | Most common, highest financial impact           |
| 3        | P3 Asymmetric Error | Most context-specific to retail operations      |
| 4        | P6 State Drift      | Hardest to detect without structured evaluation |

---

## Coming Soon

- `pattern-01-granularity/` — complete benchmark with 20 query pairs
- `pattern-10-sycophancy/` — 20 pushback sequences with scoring examples
- `scoring_rubric.md` — standardized scoring guide for all patterns
- `red_team_prompts.md` — adversarial prompt library for stress-testing

---

*GRADE Benchmarks v1.0 | Slav Pechenevskyi | 16 May, 2026*
