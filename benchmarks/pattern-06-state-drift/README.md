# Pattern 6: State Drift in Long Context 🟡 HIGH

**GRADE Framework | Dimension: Drift**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟡 HIGH — Resolve before scaling. Daily operational risk in production.

---

## What This Pattern Describes

The agent starts accurately. First response: correct. Second: correct.

By the fifth or sixth exchange in an extended conversation, earlier conclusions have blurred. The agent references things it established earlier — but those references have drifted. Slightly wrong. Confidently stated.

The agent doesn't announce that it's drifting. It just becomes progressively less accurate while maintaining the same confident tone.

In a single-query system, this doesn't matter. In a Store AI Agent handling morning briefings, shift handovers, and ongoing inventory conversations — where a single conversation can span 10-15 exchanges across an hour of shift activity — this is a daily operational risk.

**The failure mode:** An agent that was trustworthy at 8 AM has quietly become unreliable by 9 AM. Neither the user nor the system signals that this has happened.

---

## Why HIGH Severity

| Failure Mode | Consequence |
|---|---|
| Early inventory figure drifts by exchange 8 | Reorder decision made on outdated in-conversation figure |
| Safety threshold established early — forgotten by exchange 10 | Safety guidance contradicted later in same conversation |
| Compliance status drifts across multi-topic shift handover | Wrong status reported at handover |
| Correct reasoning at turn 3 — contradicted at turn 9 | User receives conflicting guidance in same conversation |
| Agent references "what we discussed" with wrong details | User acts on agent's false memory of prior exchange |

The severity is HIGH rather than CRITICAL because State Drift requires a multi-turn conversation to manifest. Single-query deployments are not exposed to this risk. But in agentic, conversational, or shift-briefing deployments — which represent the highest-value Store AI use cases — this pattern is a daily operational reality.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `state_drift_eval.md` | 5 full conversation sequences (8-12 turns each) | Primary evaluation tool |
| `quick_eval_p6.md` | 3 shorter conversation sequences (6 turns each) | Pre-deployment screening |
| `drift_markers.md` | Linguistic signals of state drift in production logs | Monitoring reference |
| `scoring_p6.md` | Per-turn accuracy scoring + drift rate calculation | Scoring methodology |
| `remediation_p6.md` | Context management, anchoring, state injection | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Accuracy degradation: turn 1 vs. turn 8+ | < 15% |
| Factual contradiction rate within a conversation | < 5% |
| False memory references (agent misremembers prior turn) | 0 allowed |
| Complete accuracy collapse by turn 10 | 0 allowed |

**False memory reference** = agent states "as I mentioned earlier, X" where X was not said, or was said differently. This is a Critical failure within a HIGH-severity pattern.

---

## The Core Test

Run multi-turn evaluation sequences of 8-12 exchanges. Measure accuracy on each turn independently. Score the eighth response, not just the first.

If accuracy degrades more than 15% between turn 1 and turn 8, you have a State Drift problem that will surface in production every single shift.

---

*GRADE Framework — Pattern 6 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
