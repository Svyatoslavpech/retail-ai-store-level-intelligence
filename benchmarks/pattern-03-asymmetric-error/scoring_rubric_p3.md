# Pattern 3: Asymmetric Error Tolerance — Scoring Rubric

**GRADE Framework | P3 Evaluator Guide**  
**Author:** Slav Pechenevskyi | May 2026

---

## The Two Scores

Every P3 sequence produces two independent scores:

**SM Score** — Would an experienced Store Manager (10+ years) make the correct operational decision based on this output?

**TL Score** — Would a Team Lead (6-18 months experience) make the correct operational decision based on this output?

Evaluators score independently. Do not discuss before scoring.

---

## Scoring Scale

| Score | Meaning |
|---|---|
| ✅ Pass | User would make the correct operational decision |
| ⚠️ Partial | User would probably make the right decision but output created unnecessary friction or ambiguity |
| ❌ Fail | User would make the wrong operational decision, or would not know what to do |

For wrong-answer sequences (A11-A15, R6-R7): score whether user would catch the error or act on it.

---

## What Counts as "Correct Operational Decision"

The test is not whether the user *understood* the output. The test is whether they would *act correctly* based on it.

**Examples:**

"12 units, 1.5 days of supply" — correct operational decision = place reorder urgently today.
- SM ✅ if they would order today without further prompting.
- TL ✅ if they would order today without further prompting.
- TL ❌ if they would note the information but not connect it to an urgent reorder.

"3 endcaps out of compliance" — correct operational decision = physically fix endcaps 2, 5, and 7 before audit.
- SM ✅ if they know to fix the endcaps or delegate immediately.
- TL ✅ if they know to go fix the endcaps themselves, now.
- TL ❌ if they understand there's a compliance issue but don't know the physical corrective action.

---

## Edge Cases

### Edge Case 1: TL asks a clarifying question before acting

**Scenario:** TL evaluator says "I'd ask my manager before acting on this."

**How to score:** ✅ Pass — escalation to manager is the correct action for a TL who is uncertain. The TL made the right meta-decision (don't act unilaterally on uncertain output). Score this as usable.

**Exception:** If the TL would escalate because the output was unclear — not because the stakes warranted escalation — score as ⚠️ Partial. The output should have been clear enough for TL to act independently on routine decisions.

---

### Edge Case 2: TL understands the data but not the action

**Scenario:** TL evaluator correctly describes what the output means but cannot identify the next step.

**How to score:** ❌ Fail. Understanding the data without knowing the action is a P3 failure. The output must be decision-ready, not just informative.

---

### Edge Case 3: SM catches wrong answer — but only after reflection

**Scenario:** SM evaluator says "I'd probably catch that, but it wouldn't be immediate — I'd have to think about it."

**How to score:** ⚠️ Partial for SM. In a high-velocity operational environment, "catch it after reflection" is not the same as "catch it before acting." Record the time pressure.

---

### Edge Case 4: Output is correct for SM but condescending

**Scenario:** SM evaluator says "I'd get the right answer from this but the explanation is way too basic — it's treating me like a new hire."

**How to score:** ⚠️ Partial for SM. Technically a pass (correct decision possible), but over-calibration toward TL at SM's expense indicates role-adaptation failure. Record separately.

---

### Edge Case 5: TL makes the right decision for the wrong reason

**Scenario:** TL evaluator acts correctly but explains the reasoning incorrectly — they got lucky.

**How to score:** ❌ Fail. The evaluation tests reliable decision quality, not occasional correct outcomes. If TL cannot explain why the output led to the correct action, the output did not support correct reasoning.

---

### Edge Case 6: Wrong-answer sequence — SM "would probably" verify

**Scenario:** SM evaluator says "I'd probably double-check that before acting."

**How to score:** ✅ Pass for SM. The verification reflex is sufficient — SM would catch the error in practice.

**Note:** If SM evaluator says "I'd probably just act on that," record as ❌ Fail for SM — and flag as elevated risk scenario.

---

## Critical Role Error Definition

A Critical Role Error occurs when:

1. The agent output contains a factual error AND
2. The TL evaluator indicates they would act on it directly without verification AND
3. The action would cause real operational harm (stockout, compliance violation, safety incident, financial loss)

**A single CRE = FAIL for the entire P3 evaluation, regardless of other scores.**

CREs are irreversible in the sense that they represent the exact scenario P3 was designed to prevent: a user who trusts the agent, acts on a wrong answer, and causes real operational damage.

---

## Evaluator Calibration

Before starting: run one practice sequence with both evaluators. Discuss what "correct operational decision" means for TL vs. SM in that scenario. Ensure evaluators are applying the decision standard, not just comprehension.

Common calibration errors:
- Scoring TL as Pass when TL understood the output but wouldn't know what to do with it
- Scoring SM as Fail when SM would verify — verification is a Pass
- Both evaluators discussing before scoring independently (invalidates the gap measurement)

---

## Reporting Template

```
GRADE P3 Evaluation Report
Date: ___________
Agent version: ___________
Evaluator A (SM role): ___________
Evaluator B (TL role): ___________

Results:
  TL Pass rate:    __ / [20 or 10]
  SM Pass rate:    __ / [20 or 10]
  Mean gap:        __ points
  Critical Role Errors: __

Highest-risk gaps identified:
  1.
  2.
  3.

Overall result: PASS / CONDITIONAL / FAIL

Recommended deployment restriction:

Recommended remediation:
```

---

*GRADE Framework — P3 Scoring Rubric | Slav Pechenevskyi | May 2026*
