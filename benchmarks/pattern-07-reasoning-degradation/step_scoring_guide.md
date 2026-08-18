# Pattern 7: Reasoning Degradation — Step Scoring Guide

**GRADE Framework | P7 Evaluator Methodology**  
**Author:** Slav Pechenevskyi | May 2026

---

## Why Score Steps, Not Just Answers

An agent can reach the right answer for the wrong reasons. It can also reach the wrong answer despite correct reasoning up to step 3 — a failure at step 4 that would be undetectable by final-answer scoring alone.

Step scoring reveals:
- Where in the reasoning chain the agent reliably performs
- Where degradation begins (typically step 3-4)
- Whether correct conclusions are trustworthy or coincidental

---

## Step Scoring System

For each reasoning query, the evaluation team defines:
1. The reasoning steps required
2. The correct output of each step
3. The passing threshold for each step

**Per-step score:**

| Score | Symbol | Definition |
|-------|--------|-----------|
| Correct | ✅ | Step output is accurate and complete |
| Partial | ⚠️ | Step output is directionally correct but missing a key element |
| Wrong | ❌ | Step output is factually incorrect |
| Missing | — | Agent skipped this step without acknowledging it |

**Special flags:**

| Flag | Symbol | Definition |
|------|--------|-----------|
| Lucky conclusion | 🎯 | Final answer correct despite wrong step(s) — unreliable reasoning |
| Step substitution | 🔄 | Agent substitutes simpler reasoning for the required step |
| Hallucinated step | 💭 | Agent introduces a reasoning step not supported by available data |

---

## Example: Full Step Scoring

**Query:** "Given Tuesday traffic patterns, current inventory, the holiday weekend, and our demographic data — what should I order today and why?"

**Required reasoning steps:**

```
Step 1: Retrieve Tuesday traffic pattern
→ Expected: Tuesday 4-6 PM peak, 34% above staffing

Step 2: Assess current inventory against velocity
→ Expected: SKU 4721 at 12 units, 1.5 days; SKU 2291 at 19 units, 2.4 days — both urgent

Step 3: Integrate holiday weekend demand multiplier
→ Expected: Holiday weekend typically adds 25-30% volume lift to Tuesday-equivalent days;
             existing supply days shrink accordingly (1.5 days → ~1.1 days for 4721)

Step 4: Apply demographic data to category mix
→ Expected: This store's demographic (40% young families) drives higher baby/snack/organic 
             velocity during holiday periods — prioritize those categories

Step 5: Synthesize ordering recommendation
→ Expected: Order 4721 (urgent, worse with holiday), 2291 (urgent), and consider incremental 
             snack/organic inventory given demographic multiplier
```

**Example agent response scoring:**

```
Agent output: "Based on Tuesday traffic and current inventory, you should 
order SKU 4721 and 2291 today. The holiday weekend will likely increase 
demand, so ordering promptly is advisable."

Step 1: ✅ (Tuesday traffic referenced)
Step 2: ✅ (4721 and 2291 correctly identified)
Step 3: ⚠️ (Holiday mentioned but no quantified impact on supply days)
Step 4: — (Demographic data completely omitted)
Step 5: ⚠️ (Core ordering recommendation correct but incomplete — misses category mix)

Final answer: ⚠️ Partial (directionally right, missing critical inputs)
Lucky conclusion flag: No — reasoning partially supports conclusion
```

---

## The Step 3 Degradation Pattern

In practice, most agents show a consistent pattern:

- Steps 1-2: Strong. Direct data retrieval.
- Step 3: Wobble begins. Integration of a third data source introduces errors.
- Step 4: Often missing or wrong. Fourth input is either omitted or incorrectly weighted.
- Step 5: Reflects degradation of steps 3-4. Final synthesis is incomplete.

**Diagnostic question:** If the agent fails at step 3 or 4, what does the conclusion look like?

- If conclusion is correct despite step 3/4 failure → Lucky conclusion flag
- If conclusion reflects the step failure → Standard wrong/partial score

---

## What Step Substitution Looks Like

**Step substitution** occurs when an agent replaces a required complex reasoning step with a simpler approximation.

**Required:** Integrate holiday demand multiplier with current supply days to calculate effective remaining supply under holiday conditions.

**Substitution:** "The holiday weekend will increase demand, so order promptly."

The agent has replaced a quantitative integration step with a qualitative observation. The observation is true but not useful — it doesn't tell the user how much to order or why the urgency changed.

Score step substitution as ⚠️ Partial — the agent acknowledged the input but didn't process it correctly.

---

## Calibration Note for Evaluators

Before scoring, agree on the expected step outputs. If two evaluators disagree on what a correct Step 3 looks like, the evaluation will produce inconsistent results.

Run one practice query together before starting. Ensure:
- Both evaluators can define the correct output for each step
- Both evaluators apply the same threshold for Partial vs. Correct
- Lucky conclusion flags are used consistently

---

*GRADE Framework — P7 Step Scoring Guide | Slav Pechenevskyi | May 2026*
