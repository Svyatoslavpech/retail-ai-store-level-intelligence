# Pattern 3: Asymmetric Error Tolerance 🔴 CRITICAL

**GRADE Framework | Dimension: Role**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🔴 CRITICAL — Do not deploy until resolved

---

## What This Pattern Describes

The same AI answer carries different risk depending on who receives it.

A Store Manager and a Team Lead can ask identical questions and require a completely different standard of accuracy — not because of preference, but because of how each processes and acts on the output.

**The Store Manager** has fifteen years of this store in their head. When the agent answers, they run it through an internal filter built from thousands of shifts, hundreds of seasonal cycles, deep local pattern recognition. A wrong answer costs thirty seconds — they catch it, they correct it, they move on.

**The Team Lead** came to the agent precisely because they don't have the answer. They trust the output. They act on it directly. A wrong answer doesn't cost thirty seconds — it costs a real ordering decision, a real staffing call, a real compliance action. And if the agent is wrong often enough, it costs the Team Lead's confidence in the entire system.

**85% accuracy is an acceptable operational risk for one user and a potential catastrophe for another.**

This is the core insight that separates GRADE from generic LLM evaluation: identical accuracy scores mean nothing without role-weighted context.

---

## Why CRITICAL Severity

| Failure Mode | Who it hurts | Consequence |
|---|---|---|
| Wrong inventory recommendation | Team Lead (trusts output directly) | Stockout or overstock. Financial loss. |
| Wrong safety threshold call | Team Lead | Compliance incident. |
| Wrong reorder timing | Team Lead | Supply chain disruption. |
| Wrong staffing call | Team Lead | Under-coverage. Customer impact. |
| Same output, different comprehension | Both | SM gets it. TL doesn't. Neither knows. |

The asymmetry is invisible. The agent produces one output. It lands differently for two users. Standard accuracy metrics don't capture this — because they measure whether the answer is correct, not whether it is usable by the person who received it.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `asymmetric_eval.md` | 20 evaluation sequences — full format | Primary evaluation tool |
| `quick_eval_p3.md` | 10-sequence rapid assessment | Pre-deployment screening |
| `scoring_rubric_p3.md` | Role-weighted scoring + edge cases | Evaluator calibration |
| `role_risk_matrix.md` | Risk by role x domain | Pre-evaluation planning |
| `remediation_p3.md` | Role-adaptive output design | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Team Lead usability score | >= 85% |
| Store Manager usability score | >= 90% |
| Cross-role divergence rate | <= 15% |
| Critical Role Error (TL acts on wrong answer) | 0 allowed |

---

## The Central Question

For every agent response, ask:

> If this answer is 85% accurate and 15% is wrong — which user catches it?

If the answer is "the Store Manager catches it, the Team Lead acts on it" — the agent is not ready for deployment.

---

*GRADE Framework — Pattern 3 Benchmark Suite | Slav Pechenevskyi | May 2026*
