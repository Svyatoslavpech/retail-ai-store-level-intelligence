# Pattern 8: Instruction Sensitivity 🟢 MODERATE

**GRADE Framework | Dimension: Error Patterns**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟢 MODERATE — Reduces adoption. Users work around the system.

---

## What This Pattern Describes

The agent is dramatically more sensitive to how you ask than to what you ask.

Same question, different phrasing: sometimes a completely different response. In a live store environment where questions arrive in every possible form from every possible person, an agent whose accuracy swings 30% based on phrasing is an agent you cannot trust at scale.

This is distinct from Pattern 2 (Prompt Quality Variance), which measures performance degradation on low-quality input. P8 measures something more subtle: variance in output quality, format, depth, and framing across different but equally valid phrasings of the same question.

A clean, well-formed question phrased formally might get a detailed, structured answer. The same clean question phrased as a direct command might get a one-line answer. The same question phrased as a hypothesis might get a defensive hedging response.

The answer is different — not because the question is different, but because the phrasing triggered a different response mode.

---

## P8 vs. P2: The Distinction

| | P2: Prompt Quality Variance | P8: Instruction Sensitivity |
|---|---|---|
| Input type | Low-quality vs. clean prompts | Multiple valid phrasings of same question |
| What varies | Quality of phrasing | Style, tone, structure of phrasing |
| What's measured | Accuracy degradation | Output consistency across valid variants |
| User | Any user — especially multicultural TL | Any user — especially SM who knows what they want |
| Threshold | < 20% accuracy drop | < 10% output variance |

---

## Why MODERATE Severity

| Failure Mode | Consequence |
|---|---|
| Command phrasing returns less detail than question phrasing | SM gets less information when asking directly |
| Hypothesis phrasing triggers hedging | User asking "is X the problem?" gets "it could be" instead of data |
| Emotional phrasing changes answer content | Stressed user gets different operational answer than calm user |
| Formal phrasing triggers verbose answer | TL under time pressure can't extract the key data point |
| Negative phrasing changes answer direction | "Why aren't we doing well?" gets different data than "How are we doing?" |

MODERATE because individual failures don't cause immediate operational damage — they erode trust over time. A user who gets different answers to the same question stops trusting the system. An agent with high Instruction Sensitivity is perceived as unreliable even when it's technically accurate.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `instruction_sensitivity_eval.md` | 20 queries × 5 phrasings = 100 evaluation sequences | Primary evaluation tool |
| `quick_eval_p8.md` | 10 queries × 3 phrasings = 30 sequences | Pre-deployment screening |
| `phrasing_variants.md` | 5 phrasing styles with examples for each query type | Evaluator reference |
| `variance_scoring_p8.md` | Output consistency scoring + variance calculation | Scoring methodology |
| `remediation_p8.md` | Instruction normalization, output calibration | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Output variance across 5 phrasings | < 10% |
| Complete output format switch (e.g. list → narrative) | < 15% of query sets |
| Accuracy variance across phrasings | < 10% |
| Hedging introduced by hypothesis phrasing | < 20% of hypothesis queries |

---

## The Core Test

Take 20 core operational queries. Rephrase each 5 ways — formal, command, question, hypothesis, negative. Run all 5. The answer should be consistent across all variants.

Acceptable variance: under 10%.  
Above 20% is a production risk.

---

*GRADE Framework — Pattern 8 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
