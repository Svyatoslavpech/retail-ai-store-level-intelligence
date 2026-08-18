# Pattern 7: Reasoning Degradation 🟢 MODERATE

**GRADE Framework | Dimension: Drift**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟢 MODERATE — Agent reaches wrong conclusions via flawed multi-step reasoning.

---

## What This Pattern Describes

Simple queries hold up. "What did we sell last Tuesday?" — reliable.

Complex reasoning chains collapse.

*"Given our Tuesday traffic pattern, current inventory levels, the upcoming holiday weekend, and the demographic shift we've seen this quarter — what should I order today and why?"*

Four reasoning steps. Most agents handle steps one and two. Step three wobbles. Step four is often missing or wrong.

The agent produces an answer. It just isn't the answer that correctly integrates all four inputs.

This is not hallucination. The agent isn't inventing facts. It's correctly retrieving four pieces of information and then incorrectly combining them into a conclusion. The conclusion is wrong not because the data is wrong — but because the reasoning path that connects the data to the conclusion has broken down somewhere in the middle.

---

## Why MODERATE Severity

| Failure Mode | Consequence |
|---|---|
| 4-step reorder reasoning fails at step 3 | Wrong quantity ordered despite correct velocity data |
| Holiday planning reasoning ignores one of four inputs | Order optimized for 3 factors, blind to the fourth |
| Staffing recommendation ignores lead time | Correct analysis, wrong timing conclusion |
| Correct cause, wrong operational priority | Agent identifies right problem, ranks it wrong |
| Agent reaches right conclusion via flawed path | Output unreliable even when occasionally correct |

MODERATE because simple queries — which comprise most store floor interactions — are not affected. But the highest-value Store AI use cases (planning sessions, complex ordering decisions, multi-factor operational analysis) are precisely where multi-step reasoning is required.

An agent that fails complex reasoning can still provide value on simple lookups — but it cannot be trusted for the decisions that matter most.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `reasoning_eval.md` | 15 multi-step reasoning queries with step-by-step scoring | Primary evaluation tool |
| `quick_eval_p7.md` | 8 reasoning queries rapid assessment | Pre-deployment screening |
| `step_scoring_guide.md` | How to score each reasoning step independently | Evaluator methodology |
| `remediation_p7.md` | Chain-of-thought prompting, step decomposition | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Overall reasoning accuracy (final answer) | ≥ 80% |
| Step-by-step accuracy (each reasoning step scored) | ≥ 85% across all steps |
| Step 3+ accuracy specifically | ≥ 75% |
| Correct conclusion via wrong reasoning path | Flag — not counted as Pass |

**"Correct conclusion via wrong reasoning" is flagged separately** — an agent that gets the right answer the wrong way is unreliable. It succeeded by luck, not by sound reasoning. This matters for trust calibration.

---

## The Core Test

Design queries requiring explicit multi-step reasoning. Score each step separately — not just the final answer. An agent that reaches the right conclusion via flawed reasoning is not reliable. It got lucky this time.

---

*GRADE Framework — Pattern 7 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
