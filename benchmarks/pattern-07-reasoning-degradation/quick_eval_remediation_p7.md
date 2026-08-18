# Pattern 7: Reasoning Degradation — Rapid Assessment + Remediation

**GRADE Framework | P7 Quick Eval + Fix**  
**Author:** Slav Pechenevskyi | May 2026

---

## Rapid Assessment (8 Queries)

**Time estimate:** 45-60 minutes

---

### Scoring Sheet

| Query | Steps | S1 | S2 | S3 | S4 | Final | Lucky? |
|-------|-------|----|----|----|----|-------|--------|
| Q1 | 3 | | | | — | | |
| Q2 | 3 | | | | — | | |
| Q3 | 4 | | | | | | |
| Q4 | 4 | | | | | | |
| Q5 | 4 | | | | | | |
| Q6 | 5 | | | | | | |
| Q7 | 3 | | | | — | | |
| Q8 | 4 | | | | | | |

**Final accuracy: __ / 8**  
**Step 3+ accuracy: __ / [total]**  
**Lucky conclusions: __**  
**Result: PASS / CONDITIONAL / FAIL**

**Pass criteria (rapid):** Final accuracy ≥ 75%, Step 3+ ≥ 70%, zero lucky conclusions on 4+ step queries.

---

### Q1 — 3-Step: Reorder Decision

**Query:** "Based on stock and velocity, should I order SKU 4721 today?"

```
Step 1: 12 units, 8/day = 1.5 days supply
Step 2: Lead time = 2 days
Step 3: 1.5 < 2 → order today (critical)
```

**Watch:** Does agent do the math (Step 1) or just say "low stock"?

---

### Q2 — 3-Step: Shrinkage Explanation

**Query:** "Shrinkage is at 8.3% this week and we reset the endcaps Monday. Is the reset causing it?"

```
Step 1: Reset disruption window = 24-48 hours
Step 2: 8.3% is a full-week figure, not a daily spike
Step 3: Week-long rate exceeds reset window → reset insufficient explanation
```

**Watch:** Does Step 2 correctly apply the timeline logic?

---

### Q3 — 4-Step: Multi-SKU Priority

**Query:** "Which of these SKUs need ordering today: 4721, 2291, 7701?"

```
Step 1: Supply days: 4721=1.5, 2291=2.4, 7701=4.0
Step 2: Lead times: 4721=2d, 2291=2d, 7701=3d
Step 3: Decision rule: 4721 critical, 2291 urgent, 7701 not today
Step 4: Priority order: 4721 → 2291 → monitor 7701
```

---

### Q4 — 4-Step: Revenue Analysis

**Query:** "Revenue is up 4.2% but traffic is flat. What's driving the improvement?"

```
Step 1: Flat traffic + revenue up → basket value or mix shift
Step 2: Basket value up $1.42, health/wellness mix improved
Step 3: Assess sustainability (mix shift vs. one-time promo)
Step 4: Offset: shrinkage up 0.3% moderates the net gain
```

**Watch:** Does Step 4 include the shrinkage offset?

---

### Q5 — 4-Step: Contradictory Data

**Query:** "System shows 34 units of 4721 but I counted 12. What do I do?"

```
Step 1: Identify discrepancy: 22-unit gap
Step 2: Identify possible causes (shrinkage, scan error, unrecorded delivery)
Step 3: Resolve for ordering: use physical count (12) — more conservative, more reliable
Step 4: Recommend: order based on 12, flag for audit
```

**Watch:** Step 3 — does agent resolve correctly (use physical count)?

---

### Q6 — 5-Step: Holiday Planning

**Query:** "Given traffic patterns, inventory, holiday weekend, and demographics — what to order today?"

```
Step 1: Tuesday 4-6 PM peak, 34% gap
Step 2: 4721 = 1.5 days, 2291 = 2.4 days
Step 3: Holiday adds ~25-30% demand → supply days shrink further
Step 4: Demographic (40% young family) → incremental snacks/organic
Step 5: Order 4721 + 2291 urgently, increment snack/organic buffer
```

**Watch:** Most complex rapid query. Steps 3 and 4 are the degradation test.

---

### Q7 — 3-Step: Competitor Response

**Query:** "Beverage sales are down 31% since the Fifth Street competitor opened. What's the priority response?"

```
Step 1: 31% decline is significant — likely competitive impact confirmed
Step 2: Tactical options: price, promo, in-stock, assortment
Step 3: Prioritize in-stock reliability (within control) before margin actions
```

**Watch:** Does Step 3 prioritize correctly (in-stock before price)?

---

### Q8 — 4-Step: Customer Complaint Root Cause

**Query:** "Customer complaints about availability are up 40%. What might be causing it and what do I check first?"

```
Step 1: Availability complaint → inventory gap → (stockout/shrinkage/receiving/demand)
Step 2: Check inventory levels, shrinkage data, delivery log, traffic
Step 3: Evidence-based prioritization of most likely cause
Step 4: Specific investigation action tied to most likely cause
```

**Watch:** Step 3 — does agent prioritize based on data or based on habit?

---

## After Rapid Eval

**Final ≥ 75%, Step 3+ ≥ 70%:**  
→ Conditional pass. Full 15-query evaluation recommended.

**Final ≥ 75% but Step 3+ < 70%:**  
→ Lucky conclusions present. Reasoning is unreliable despite correct outputs. See remediation.

**Final < 75%:**  
→ FAIL. Remediation required before full evaluation.

---

## Remediation

### Level 1: Chain-of-Thought Prompting

**Use when:** Step 3+ accuracy < 70%, or multiple lucky conclusions

```
For complex operational questions that require multiple steps of reasoning:
Think through the problem step by step before giving your answer.

Structure your reasoning as:
Step 1: [What data do I need for the first piece of this?]
Step 2: [What does that data tell me?]
Step 3: [How does this interact with the second piece of data?]
...
Conclusion: [What does this all mean for the operational decision?]

Show your work. A correct conclusion arrived at by wrong reasoning 
is not reliable — and the user's next question will depend on 
trusting your reasoning, not just your answer.
```

### Level 2: Step Decomposition for Complex Queries

**Use when:** Agent collapses multi-step queries into single-step answers

```
When a query involves multiple variables or inputs:
1. Identify each input explicitly before combining them
2. Process each input against the question before integrating
3. Do not skip to the conclusion — the intermediate steps are the answer

Example of correct behavior:
Query: "Given stock levels, velocity, and lead time — should I order today?"
Wrong approach: "Yes, you should order today." (skipped steps)
Correct approach: "Current stock: 12 units. Velocity: 8/day → 1.5 days supply.
Lead time: 2 days. 1.5 days < 2 days → order today or face stockout."
```

### Level 3: Multi-Input Integration Protocol

**Use when:** Agent correctly handles 2-input reasoning but fails at 3+ inputs

```
When integrating 3 or more data inputs:
After processing inputs 1 and 2, explicitly state the intermediate conclusion 
before adding input 3. This prevents the third input from getting lost.

Example:
"Traffic data + inventory data = reorder is urgent. [intermediate conclusion]
Now applying the holiday demand multiplier: urgency increases further 
because holiday demand will reduce effective supply days from 1.5 to ~1.1. 
[updated conclusion after input 3]
Applying demographic weighting: young family demographic further supports 
prioritizing organic SKUs. [final integrated conclusion]"
```

### Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (chain-of-thought) | Full 15-query evaluation |
| Level 2 (step decomposition) | Rapid 8-query — focus on Q6 (5-step) |
| Level 3 (multi-input) | Full evaluation — M4, M5, M9, M10, M13 specifically |

---

*GRADE Framework — P7 Rapid Assessment + Remediation | Slav Pechenevskyi | May 2026*
