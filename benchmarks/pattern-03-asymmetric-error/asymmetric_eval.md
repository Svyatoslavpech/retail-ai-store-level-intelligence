# Pattern 3: Asymmetric Error Tolerance — Full Evaluation (20 Sequences)

**GRADE Framework | P3 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 120-150 minutes (requires two evaluators)  
**Use:** Full pre-deployment certification

---

## Evaluation Setup

### Required: Two Evaluators

**Evaluator A — Store Manager role**
- Plays an experienced Store Manager: 10+ years at this location
- Deep operational knowledge, strong mental model of store patterns
- Reviews agent output as someone who already knows a lot — they're checking, not learning
- Decision standard: "Would I catch an error in this response?"

**Evaluator B — Team Lead role**
- Plays a Team Lead with 6-18 months of experience
- Limited deep pattern knowledge; comes to the agent for answers they don't have
- Reviews agent output as someone who will act on it directly
- Decision standard: "Would I make the right operational decision based on this output?"

### The Core Test

Both evaluators receive the same agent response to the same query. They score independently:

- **SM Catch Rate:** How often would the Store Manager catch an error if the response were wrong?
- **TL Decision Quality:** How often would the Team Lead make the correct operational decision based on the output?

The gap between these two rates is the Asymmetric Error Tolerance score.

---

## Scoring Sheet

| Seq | Domain | SM Score | TL Score | Gap | Notes |
|-----|--------|----------|----------|-----|-------|
| A1 | Inventory | | | | |
| A2 | Reorder | | | | |
| A3 | Staffing | | | | |
| A4 | Shrinkage | | | | |
| A5 | Compliance | | | | |
| A6 | Promotion | | | | |
| A7 | Safety | | | | |
| A8 | Category | | | | |
| A9 | Seasonal | | | | |
| A10 | Performance | | | | |
| A11 | Inventory (wrong answer) | | | | |
| A12 | Reorder (wrong answer) | | | | |
| A13 | Staffing (wrong answer) | | | | |
| A14 | Compliance (wrong answer) | | | | |
| A15 | Safety (wrong answer) | | | | |
| A16 | Complex reasoning | | | | |
| A17 | Complex reasoning | | | | |
| A18 | Ambiguous output | | | | |
| A19 | Ambiguous output | | | | |
| A20 | Role-calibrated response | | | | |

**SM average score: __ / 20**  
**TL average score: __ / 20**  
**Mean gap: __ points**  
**Critical Role Errors (TL acts on wrong answer): __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Part 1: Correct Answer Sequences — Role Usability Test (A1–A10)

These sequences use correct agent responses. The test: is the output usable by both roles?

A correct answer that the Store Manager understands clearly but the Team Lead misinterprets or cannot act on is still a P3 failure.

---

### A1 — Inventory Count

**Agent response to "How many units of SKU 4721 do we have?":**
> "12 units as of the 5:43 AM scan. At current velocity of 8 units per day, that's approximately 1.5 days of supply."

**SM evaluation:** Does the Store Manager immediately understand the operational implication and what action is required?

**TL evaluation:** Does the Team Lead understand what to do with this information — specifically that a reorder is urgent?

**TL risk signal:** TL hears "12 units" and "1.5 days" but doesn't connect it to an action. Agent provided data but not decision support.

**Pass:** Both roles can extract correct action from the output.
**Fail:** TL receives correct data but cannot determine the correct next step.

---

### A2 — Reorder Recommendation

**Agent response to "Should I reorder SKU 2291 today?":**
> "Based on current stock (19 units) and sales velocity (8 units/day), you have approximately 2.4 days of supply. Given the 2-day lead time on this SKU, ordering today keeps you at or just above zero at delivery. I'd recommend placing the order before noon."

**SM evaluation:** Does the SM recognize this as a clear, actionable recommendation with solid math behind it?

**TL evaluation:** Does the TL understand: (a) what the recommendation is, (b) why, (c) what to do, and (d) by when?

**TL risk signal:** Response contains all the right data but is organized around math, not action. TL may focus on "2.4 days" without registering "before noon today."

**Pass:** TL can identify the action and timing clearly.
**Fail:** Action or timing is ambiguous for a TL-level user.

---

### A3 — Staffing Gap

**Agent response to "Is our Tuesday 4-6 PM staffing adequate?":**
> "Tuesday 4-6 PM shows a consistent 34% traffic increase over your current staffing allocation, based on the past 12 Tuesdays. You're typically short 1.5 FTE equivalents during that window. Historically, this correlates with extended queue times at checkout and reduced floor coverage in the back half of the store."

**SM evaluation:** Does the SM immediately know what this means operationally and what options exist to address it?

**TL evaluation:** Does the TL know: (a) there's a problem, (b) how significant it is, (c) what the practical impact is, and (d) what they can do about it?

**TL risk signal:** "1.5 FTE equivalents" may not be immediately translatable for a TL. Do they know what to actually do with this information on a Tuesday afternoon?

**Pass:** TL can identify the gap and take a concrete action (request coverage, adjust floor assignment, flag to manager).
**Fail:** TL understands there's a problem but cannot determine what to do.

---

### A4 — Shrinkage Alert

**Agent response to "What's our snack aisle shrinkage this week?":**
> "Snack aisle shrinkage is running at 8.3% this week, compared to the store average of 2.1% and the category benchmark of 3.4%. This is the third consecutive week above 5%. The variance is concentrated in the chips and candy subcategories on the end sections of the aisle."

**SM evaluation:** Does the SM immediately recognize this as significant, know the likely causes, and know what investigation steps to take?

**TL evaluation:** Does the TL understand: (a) 8.3% is a problem, (b) how serious it is, (c) where specifically to look, and (d) what their role is in addressing it?

**TL risk signal:** TL may not have context for what 8.3% means relative to normal. The comparison benchmarks are there — but does the TL interpret them correctly under time pressure?

**Pass:** TL knows this requires action and has a starting point for investigation.
**Fail:** TL sees the number but doesn't understand its severity or what to do.

---

### A5 — Compliance Check

**Agent response to "Are our promotional endcaps in compliance?":**
> "3 of 8 endcaps are showing configuration variance against the current planogram. Endcaps 2, 5, and 7 have items that don't match the approved promotional layout. This creates a compliance risk for the weekly audit."

**SM evaluation:** Does the SM know immediately what needs to happen and who owns it?

**TL evaluation:** Does the TL know: (a) there's a problem, (b) which endcaps to fix, (c) what "compliance risk" means in practice, and (d) what to do before the audit?

**TL risk signal:** "Configuration variance" and "compliance risk" may be abstract for a newer TL. Do they know to physically go fix endcaps 2, 5, and 7 right now?

**Pass:** TL takes the right physical action from this output.
**Fail:** TL understands something is wrong but is unclear on the specific corrective action.

---

### A6 — Promotion Performance

**Agent response to "How did last week's bottled water endcap do?":**
> "The promotion generated a 28% sales lift over the prior week baseline — 94 units vs. 73 units. Margin held steady. Sell-through was 89% by Sunday, which is above the 80% target. This performed in the top third of comparable promotions in the past 12 months."

**SM evaluation:** Does the SM read this as a successful promotion and know whether to repeat or modify the approach?

**TL evaluation:** Does the TL understand: (a) it worked, (b) by how much, (c) relative to what standard?

**TL risk signal:** TL may focus on "28% lift" without understanding the reference point. "Top third of comparable promotions" — does TL know what that means?

**Pass:** Both roles understand the promotion was successful and can explain why.
**Fail:** TL cannot determine whether this was a good result.

---

### A7 — Temperature Safety

**Agent response to "The cooler spiked to 48°F this morning — is that okay?":**
> "48°F exceeds the FDA refrigeration safety threshold of 40°F. The spike duration matters for compliance — if the temperature was above 40°F for more than 2 hours continuously, documentation and a product assessment are required. Do you have a log of when the temperature returned to normal?"

**SM evaluation:** Does the SM immediately know the compliance obligation and what steps to take?

**TL evaluation:** Does the TL know: (a) this is not okay, (b) what the specific risk is, (c) what they need to find out, and (d) what action may be required?

**TL risk signal:** TL may not know what "documentation and product assessment" means in practice. Do they know to call the manager and check the temperature log?

**Pass:** TL takes the right escalation action.
**Fail:** TL is uncertain whether this is serious or knows it's serious but not what to do.

---

### A8 — Category Velocity

**Agent response to "What are our top snack SKUs this month?":**
> "Top 5 by units sold this month: SKU 4401 (chips, family size) — 312 units; SKU 3892 (trail mix, 10oz) — 287 units; SKU 5103 (granola bar multipack) — 241 units; SKU 2874 (cheese crackers, 6pk) — 198 units; SKU 6612 (popcorn, 3-pack) — 177 units."

**SM evaluation:** Does the SM recognize these patterns and know how to use this for ordering or placement decisions?

**TL evaluation:** Does the TL know what to do with this list — specifically for a reorder or display priority decision?

**TL risk signal:** Raw velocity list is useful for a SM who knows context. Does TL know whether these are adequately stocked, whether they need reorder priority, or just that they sell well?

**Pass:** TL can use this list to make a specific operational decision (identify what to prioritize for reorder or placement).
**Fail:** TL has the data but no clear action path.

---

### A9 — Seasonal Planning

**Agent response to "What should I think about for the upcoming holiday ordering?":**
> "Based on last year's holiday season at this store: snacks drove the highest volume lift (+31%), followed by beverages (+24%) and seasonal décor (+18%). Your stockout incidents were concentrated in weeks 2 and 3 — primarily in the nuts and dried fruit subcategory. Lead time on your seasonal suppliers runs 10-14 days this time of year. First holiday order window closes in 12 days."

**SM evaluation:** Does the SM know exactly how to use this to build an order — including what to order more of, when, and where to focus?

**TL evaluation:** Does the TL know: (a) which categories to prioritize, (b) what the time pressure is, (c) what went wrong last year and how to avoid it?

**TL risk signal:** TL may not know how to translate "12 days" and "10-14 day lead time" into a concrete order-by date. Does TL know the order needs to go in within 2 days to ensure delivery before the window?

**Pass:** TL can identify the key actions and timing.
**Fail:** TL has context but cannot determine the specific action and deadline.

---

### A10 — Store Performance

**Agent response to "How are we doing vs. last month?":**
> "Revenue is up 4.2% month-over-month. Traffic is flat (+0.3%). Average transaction value increased from $34.10 to $35.52 — the improvement is driven by a category mix shift toward higher-margin items in the health and wellness section. Shrinkage is 0.3% above last month's rate, which offsets some of the revenue gain."

**SM evaluation:** Does the SM understand the performance picture and know which levers drove it?

**TL evaluation:** Does the TL understand: (a) the store is doing better, (b) why, and (c) what the one area of concern is?

**TL risk signal:** "Category mix shift toward higher-margin items" — does TL understand this at a practical level, or does it sound like a metric without an operational meaning?

**Pass:** Both roles can describe the performance picture accurately.
**Fail:** TL cannot explain why performance improved or what the shrinkage concern means operationally.

---

## Part 2: Intentionally Wrong Answer Sequences — Critical Role Error Test (A11–A15)

These sequences inject a factually incorrect agent response. The test: does the Store Manager catch it? Does the Team Lead act on it?

**Ground truth is provided to the scoring team only — not to evaluators.**

---

### A11 — Inventory Count (Wrong Answer) 🔴

**Ground truth:** 12 units in stock.

**Agent response (wrong):**
> "You have 34 units of SKU 4721 in stock as of this morning's scan."

**SM evaluation:** Does the SM recognize this is implausible? Would they verify before acting?

**TL evaluation:** Would the TL accept this and deprioritize reorder based on it?

**Critical Role Error:** TL accepts wrong count → no reorder placed → stockout in 1.5 days.

**Pass:** SM catches the error OR agent output contains sufficient context for TL to verify before acting.
**Fail (Critical):** TL would act on wrong inventory count without verification.

---

### A12 — Reorder Timing (Wrong Answer) 🔴

**Ground truth:** Reorder needed today. Lead time is 2 days. Stock runs out in 2.4 days.

**Agent response (wrong):**
> "You have comfortable stock levels — the next reorder window is next Tuesday."

**SM evaluation:** Does the SM check this against their mental model of inventory velocity?

**TL evaluation:** Would the TL delay ordering until Tuesday?

**Critical Role Error:** TL waits → stockout Thursday morning → full day of lost sales.

---

### A13 — Staffing Call (Wrong Answer) 🔴

**Ground truth:** Tuesday 4-6 PM is understaffed by 34%.

**Agent response (wrong):**
> "Tuesday afternoon staffing looks well-matched to expected traffic. No adjustments needed this week."

**SM evaluation:** Does the SM flag this as inconsistent with their experience of Tuesday afternoons?

**TL evaluation:** Does the TL plan the shift without adjustments?

**Critical Role Error:** TL schedules normally → Tuesday 4-6 PM is understaffed → service disruption.

---

### A14 — Compliance Status (Wrong Answer) 🔴

**Ground truth:** 3 endcaps out of compliance.

**Agent response (wrong):**
> "All promotional endcaps are configured correctly and in compliance with this week's planogram."

**SM evaluation:** Does the SM verify before the audit?

**TL evaluation:** Does the TL proceed without checking endcaps?

**Critical Role Error:** TL doesn't check endcaps → audit finds violations → compliance write-up.

---

### A15 — Safety Threshold (Wrong Answer) 🔴

**Ground truth:** 48°F exceeds FDA threshold of 40°F.

**Agent response (wrong):**
> "48°F is within acceptable range for brief temperature fluctuations. This is a normal delivery-related spike and doesn't require documentation."

**SM evaluation:** Does the SM know the FDA threshold and flag this as wrong?

**TL evaluation:** Does the TL proceed without escalating or documenting?

**Critical Role Error:** TL accepts agent's assessment → no documentation → compliance incident.

---

## Part 3: Role-Calibrated Output Test (A16–A20)

These sequences test whether the agent adjusts output appropriately when role is signaled — and whether output at the wrong calibration causes role-specific failures.

---

### A16 — Complex Multi-Factor Reasoning (SM context)

**Setup:** Role signaled as Store Manager in system context.

**Query:**
> What's driving the discrepancy between our traffic lift and revenue flatness this month?

**Pass:** Agent provides analysis-level response — multiple contributing factors, trade-off reasoning, no hand-holding on interpretation.

**Fail:** Agent over-explains basics that an SM already knows. Wastes time, signals the agent doesn't understand the user.

---

### A17 — Complex Multi-Factor Reasoning (TL context)

**Setup:** Role signaled as Team Lead in system context.

**Query:**
> What's driving the discrepancy between our traffic lift and revenue flatness this month?

**Pass:** Agent provides structured explanation with clear conclusions. Translates metrics into operational meaning. Tells TL what to take away from this, not just what the data shows.

**Fail:** Agent provides SM-level analysis. TL receives data-heavy response without operational conclusions. TL doesn't know what to do with it.

---

### A18 — Ambiguous Output (Inventory Context)

**Agent response to "What should I do about the dairy section?":**
> "Dairy velocity is up 12% this week. Current stock levels are at 18 units on the top 3 SKUs. Shrinkage is within target at 3.1%. The weekend delivery is confirmed."

**SM evaluation:** SM can synthesize this into a clear picture and decide whether action is needed.

**TL evaluation:** Does TL know if action is required? The response describes a situation but doesn't conclude — is everything fine, or is something needed?

**Pass:** Both roles can determine whether action is needed.
**Fail:** TL is uncertain whether to act or not.

---

### A19 — Ambiguous Output (Performance Context)

**Agent response to "How are we doing on shrinkage?":**
> "Shrinkage this month is 2.8%. Last month was 2.5%. The category average is 2.1%."

**SM evaluation:** SM immediately reads this as: we're above target and trending in the wrong direction.

**TL evaluation:** Does TL know this is bad? Does TL know what to do about it?

**Pass:** TL understands the direction (rising) and the reference (above category average = not good).
**Fail:** TL sees three numbers without understanding which direction is a problem.

---

### A20 — Role-Calibrated Response Quality

**Setup:** Two versions of the same query from two roles. Agent response should differ in structure and depth.

**SM query:** "Walk me through what's happening in the snack category."

**TL query:** "What's going on with snacks? I'm not sure what to focus on."

**Pass:**
- SM response: concise analysis, assumes operational context, focuses on insights and implications
- TL response: structured narrative, explains what the data means, ends with clear recommended action

**Fail:** Agent gives identical response to both. One version will be wrong for its recipient.

---

## After Evaluation

**TL score >= 85%, SM score >= 90%, zero Critical Role Errors:**
→ Pass.

**TL score 75-84%, SM >= 90%, zero Critical Role Errors:**
→ Conditional. Role-adaptive output needs improvement. See `remediation_p3.md` Level 2.

**Any Critical Role Error (A11-A15):**
→ FAIL. Agent cannot be deployed to Team Lead users without intervention. See `remediation_p3.md` Level 1.

**TL score < 75%:**
→ FAIL. Agent output is not TL-usable. Level 1 intervention required.

---

*GRADE Framework — P3 Full Evaluation | Slav Pechenevskyi | May 2026*
