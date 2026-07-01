# Pattern 1: Granularity Boundary Failure 🔴 CRITICAL

**GRADE Framework | Dimension: Granularity**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🔴 CRITICAL — Do not deploy until resolved

---

## What This Pattern Describes

The agent answers at the wrong altitude.

A question that has a meaningful answer only at store level receives a response drawn from national trends, regional aggregates, or chain-wide benchmarks. The answer is technically correct — and operationally useless.

The agent doesn't fail visibly. It doesn't say "I don't know." It produces a fluent, confident, well-structured response that describes a different store, a different customer base, a different reality.

This is the most common failure in Store AI deployment — and the hardest to catch, because the answer sounds authoritative.

Foundation models default toward statistically dominant patterns in their training data. Ask about holiday snack performance and the model tells you what sells across North America. Ask what sells on aisle 7 of a specific store in a neighborhood that's 40% young families — and without proper grounding, it still tells you about North America.

---

## Why CRITICAL Severity

| Failure Mode | Consequence |
|---|---|
| National trend replaces local data on inventory query | Wrong order placed. Stockout or overstock. |
| Chain-wide promo data replaces store promo history | Markdown or reorder decision made on irrelevant baseline |
| Aggregate demographic data replaces local customer profile | Feature area decisions misaligned with actual shopper behavior |
| Regional seasonality replaces store-specific pattern | Seasonal order based on wrong market signal |
| Industry benchmark replaces store performance metric | Performance assessment against wrong standard |

IHL Group estimates inventory management errors cost global retailers $1.77 trillion annually — a significant portion driven by aggregate data substituting for local intelligence. A Store AI Agent with Granularity Boundary Failure doesn't reduce that cost. It systematizes it.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `granularity_eval.md` | 20 evaluation sequences — full format | Primary evaluation tool |
| `quick_eval_p1.md` | 10-sequence rapid assessment | Pre-deployment screening |
| `scoring_rubric_p1.md` | Scoring criteria + edge cases | Evaluator calibration |
| `altitude_markers.md` | Linguistic signals of wrong-altitude responses | Production monitoring |
| `remediation_p1.md` | Retrieval grounding + prompt interventions | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Store-level response rate (full 20-sequence) | ≥ 85% |
| Store-level response rate (rapid 10-sequence) | ≥ 80% |
| National/regional substitution on explicit local query | 0 allowed |
| Ambiguous-scope responses (neither clearly local nor aggregate) | < 10% |

**Any response substituting national or regional data for an explicitly store-level query = FAIL on that sequence.**

---

## The Core Test

> Ask the agent a question that only has a meaningful answer at store level.

*"What's our Tuesday evening traffic pattern?"*

If the response describes industry benchmarks, regional trends, or chain-wide averages — you have a Granularity Boundary Failure.

The test is not whether the agent is accurate. The test is whether the agent is answering the question that was actually asked.

---

*GRADE Framework — Pattern 1 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
