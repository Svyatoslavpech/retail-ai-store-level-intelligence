# Pattern 2: Prompt Quality Variance 🟡 HIGH

**GRADE Framework | Dimension: Granularity**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟡 HIGH — Resolve before scaling to full store deployment

---

## What This Pattern Describes

The agent works when the question is well-formed. The store floor doesn't produce well-formed questions.

A Team Lead at 5:45 AM, three minutes before the shift starts, is not thinking about query optimization. They type what they think. They write the way they talk. In the multicultural reality of American retail operations — where associates and Team Leads frequently think in one language and communicate in another — the prompt that reaches the AI already carries translation losses before the model processes a single token.

Real queries from real store floors:

> *"whats going on with the dairy section lately"*  
> *"why are we always running out of the organic stuff"*  
> *"what should i do about the tuesday problem"*

Each is a genuine operational question. Each will trigger multiple downstream failures if the agent isn't built for low-quality input.

Prompt Quality Variance is not a user problem. It is a system design problem. If your agent only works when the question is well-formed, it doesn't work.

---

## Connection to Pattern 11: Intent-to-Prompt Gap

P2 and Pattern 11 (Intent-to-Prompt Gap) address adjacent failure modes:

- **P2** measures performance degradation under low-quality prompt input
- **Pattern 11** describes why that input is low-quality in the first place — the gap between what the user means and what they can articulate, amplified by cognitive load and linguistic translation

The benchmarks in this directory test P2 directly. For the root cause — why prompts are low-quality in multicultural, cognitively loaded environments — see the GRADE Pattern 11 documentation and companion article.

---

## Why HIGH Severity

| Failure Mode | Consequence |
|---|---|
| Agent fails on informal queries | Users with lowest experience get worst results — the people who most need help |
| Accuracy drops under cognitive load phrasing | Morning shift decision quality degraded precisely when stakes are highest |
| Non-native English queries return poor results | Multicultural workforce systematically underserved |
| Incomplete queries misinterpreted | Wrong answer delivered confidently to a question that wasn't asked |
| Colloquial queries trigger hallucination | Agent fills gaps in low-quality input with plausible-sounding fabrication |

The users most likely to submit low-quality prompts are the users with the least experience — exactly the users who most need the agent to work reliably. P2 failure creates an inverse quality curve: best results for users who need them least.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `prompt_variance_eval.md` | 20 query sets × 5 phrasings = 100 evaluation sequences | Primary evaluation tool |
| `quick_eval_p2.md` | 10 query sets × 3 phrasings = 30 sequences | Pre-deployment screening |
| `prompt_taxonomy.md` | Classification of real store-floor prompt types | Evaluator reference + query design guide |
| `variance_scoring.md` | Variance calculation method + thresholds | Scoring methodology |
| `remediation_p2.md` | Query normalization, intent inference, prompt hardening | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Accuracy variance: clean vs. messy prompts | < 20% degradation |
| Accuracy variance: clean vs. non-native phrasing | < 20% degradation |
| Accuracy variance: clean vs. incomplete queries | < 25% degradation |
| Complete failure rate on any prompt variant | < 5% |

**Complete failure** = agent returns an answer that is factually wrong, completely off-topic, or clearly misinterpreted the query.

---

## The Core Test

Take a set of core operational queries. Rephrase each one five ways:
1. Clean / formal
2. Casual / colloquial
3. Incomplete / fragmented
4. Non-native English phrasing
5. Emotionally loaded / stressed

Run all five variants. The correct answer is the same for all five. Measure how often the agent gets it right across all variants — and how much accuracy drops from clean to messy.

---

*GRADE Framework — Pattern 2 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
