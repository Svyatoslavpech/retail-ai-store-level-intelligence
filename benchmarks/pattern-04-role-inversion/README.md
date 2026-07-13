# Pattern 4: Information Role Inversion 🟢 MODERATE

**GRADE Framework | Dimension: Role**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟢 MODERATE — Reduces adoption. One user group consistently over-trusts or under-uses the agent.

---

## What This Pattern Describes

The Store Manager comes to the agent holding an answer. They want speed, confirmation, data access. The agent is a fast encyclopedia — they use it to validate and accelerate.

The Team Lead comes holding a question. They want logic, reasoning, a path to a decision. The agent is a thinking partner — they use it to discover.

One agent. Two completely inverted operational modes.

An agent optimized for the Store Manager will overwhelm the Team Lead. An agent optimized for the Team Lead will frustrate the Store Manager. An agent calibrated for neither will fail both — but differently, and invisibly.

**The inversion:** Each role uses the agent as if it's something different. The agent that doesn't adapt to these inverted modes produces outputs that are technically accurate but operationally misaligned for at least one user at all times.

---

## P4 vs. P3: The Distinction

| | P3: Asymmetric Error Tolerance | P4: Information Role Inversion |
|---|---|---|
| Core question | Who is at risk when the AI is wrong? | Who is being served by how the AI is right? |
| Failure mode | Wrong answer + TL trust = operational damage | Right answer + wrong mode = adoption failure |
| Test type | Inject wrong answers, measure who catches them | Measure whether output mode matches user's operational need |
| Consequence | Financial, compliance, safety risk | Frustration, workarounds, distrust of system |

P3 and P4 address opposite sides of the same role problem. P3: error risk. P4: usability fit.

---

## Why MODERATE Severity

| Failure Mode | Consequence |
|---|---|
| SM receives TL-style explanations | SM is frustrated by over-explained answers. Stops using agent for quick lookups. |
| TL receives SM-style analysis | TL is overwhelmed by data-heavy responses. Can't extract what to do. Stops trusting. |
| Agent doesn't adapt to role at all | Both groups develop workarounds. Adoption plateaus. |
| Agent over-optimizes for one role | The other role's productivity gain from AI is lost entirely. |

MODERATE because the failure doesn't damage operations directly — it damages adoption. But adoption failure in Store AI means the investment in the system produces no operational return. In the long run, adoption failure is as damaging as operational failure.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `role_inversion_eval.md` | 20 query sets — same query evaluated for SM and TL usability | Primary evaluation tool |
| `quick_eval_p4.md` | 10 query sets rapid assessment | Pre-deployment screening |
| `role_mode_matrix.md` | SM encyclopedia mode vs. TL discovery mode — characteristics and signals | Evaluator reference |
| `scoring_p4.md` | Dual-role usability scoring | Scoring methodology |
| `remediation_p4.md` | Role detection, mode adaptation, output calibration | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| SM usability score | ≥ 85% — output serves encyclopedia/validation mode |
| TL usability score | ≥ 85% — output serves discovery/reasoning mode |
| Cross-mode failure (output clearly wrong mode for one role) | < 15% of queries |
| Adaptation when role is signaled | ≥ 80% — agent adjusts when role context is provided |

---

## The Two Operational Modes

**Encyclopedia Mode (Store Manager):**
- User knows roughly what the answer should be
- Agent provides fast confirmation + specific data
- Speed and precision matter more than explanation
- Trust is built through accuracy, not through reasoning shown

**Discovery Mode (Team Lead):**
- User doesn't know the answer
- Agent provides reasoning path + conclusion
- Understanding matters as much as the answer
- Trust is built through the agent showing its work

---

*GRADE Framework — Pattern 4 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
