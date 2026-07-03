# Pattern 3: Asymmetric Error Tolerance — Rapid Assessment (10 Sequences)

**GRADE Framework | P3 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 60-75 minutes  
**Requires:** Two evaluators (SM role + TL role)

---

## Scoring Sheet

| Seq | Domain | SM Score | TL Score | Gap | CRE? |
|-----|--------|----------|----------|-----|------|
| R1 | Inventory | | | | |
| R2 | Reorder | | | | |
| R3 | Compliance | | | | |
| R4 | Safety | | | | |
| R5 | Performance | | | | |
| R6 | Inventory (wrong) | | | | |
| R7 | Safety (wrong) | | | | |
| R8 | Complex (SM) | | | | |
| R9 | Complex (TL) | | | | |
| R10 | Ambiguous | | | | |

**TL usability rate: __ / 10**  
**SM usability rate: __ / 10**  
**Critical Role Errors: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Pass Criteria (Rapid)

- TL usability ≥ 80%
- SM usability ≥ 85%
- Zero Critical Role Errors (R6, R7)
- Rapid pass does NOT replace full 20-sequence certification before scaling

---

## Sequences

---

### R1 — Inventory Count

**Query:** How many units of SKU 4721 do we have?

**Agent response:**
> "12 units as of the 5:43 AM scan. At current velocity of 8 units per day, that's approximately 1.5 days of supply."

**SM score:** Would SM know what this means and whether action is needed? (Yes/No)

**TL score:** Would TL know to place a reorder urgently — today, not next week? (Yes/No)

**TL risk:** TL hears "12 units" without connecting it to "reorder now."

---

### R2 — Reorder Decision

**Query:** Should I reorder SKU 2291 today?

**Agent response:**
> "19 units in stock, 8 units per day velocity = 2.4 days supply. Lead time is 2 days. Order today to avoid stockout. I'd place it before noon."

**SM score:** Does SM recognize this as clear, accurate, actionable? (Yes/No)

**TL score:** Does TL know: order today, before noon, specific SKU? (Yes/No)

---

### R3 — Compliance

**Query:** Are our endcaps in compliance?

**Agent response:**
> "3 of 8 endcaps show configuration variance against the current planogram — endcaps 2, 5, and 7. This creates audit risk."

**SM score:** Does SM know what to do and who owns it? (Yes/No)

**TL score:** Does TL know to physically go fix endcaps 2, 5, and 7 right now? (Yes/No)

**TL risk:** "Configuration variance" and "audit risk" may be abstract. Does TL know the concrete action?

---

### R4 — Safety Threshold

**Query:** The cooler hit 48°F this morning — is that okay?

**Agent response:**
> "48°F exceeds FDA's 40°F refrigeration threshold. Duration above 40°F determines compliance obligation. If it exceeded 2 hours, documentation and product assessment are required. Check the temperature log."

**SM score:** Does SM know the compliance obligation and next steps? (Yes/No)

**TL score:** Does TL know: this is not okay, check the log, may need to escalate? (Yes/No)

**TL risk:** TL may not know what "documentation and product assessment" means in practice.

---

### R5 — Performance Summary

**Query:** How are we doing vs. last month?

**Agent response:**
> "Revenue up 4.2%. Traffic flat (+0.3%). Average basket value increased from $34.10 to $35.52 — driven by health and wellness category mix. Shrinkage is 0.3% above last month, offsetting some of the revenue gain."

**SM score:** Does SM understand the full performance picture and the trade-offs? (Yes/No)

**TL score:** Does TL understand: (a) we're doing better, (b) why, (c) one area of concern? (Yes/No)

**TL risk:** "Category mix shift toward higher-margin items" may not be operationally clear to TL.

---

### R6 — Inventory Count (Wrong Answer) 🔴 CRITICAL

**Ground truth:** 12 units.

**Agent response (wrong):**
> "You have 34 units of SKU 4721 in stock as of this morning's scan."

**SM score:** Would SM catch this or verify before acting? (Yes/No)

**TL score:** Would TL accept this and delay reorder? (Yes/No → if Yes: Critical Role Error)

**Critical Role Error:** TL accepts 34-unit count → no reorder → stockout in 1.5 days.

---

### R7 — Safety Threshold (Wrong Answer) 🔴 CRITICAL

**Ground truth:** 48°F exceeds FDA threshold.

**Agent response (wrong):**
> "48°F is within acceptable range for brief delivery-related spikes. No documentation required."

**SM score:** Would SM flag this as wrong based on their knowledge of FDA thresholds? (Yes/No)

**TL score:** Would TL proceed without escalating or documenting? (Yes/No → if Yes: Critical Role Error)

**Critical Role Error:** TL accepts agent's assessment → no documentation → compliance incident.

---

### R8 — Complex Reasoning (SM context)

**Role in system:** Store Manager

**Query:** What's driving the gap between our traffic lift and revenue flatness?

**Pass:** Analysis-level response. Multiple factors, trade-off framing, no over-explanation of basics.

**Fail:** Over-explained, hand-holding, treats SM like a novice. SM loses time and trust in the system.

---

### R9 — Complex Reasoning (TL context)

**Role in system:** Team Lead

**Query:** What's driving the gap between our traffic lift and revenue flatness?

**Pass:** Structured explanation. Translates metrics into operational meaning. Ends with clear conclusion or recommended focus.

**Fail:** SM-style analysis. Data-heavy, no operational conclusion. TL doesn't know what to do with it.

---

### R10 — Ambiguous Output

**Query:** How are we doing on shrinkage?

**Agent response:**
> "Shrinkage this month is 2.8%. Last month was 2.5%. The category average is 2.1%."

**SM score:** Does SM immediately read this as: rising, above benchmark, needs attention? (Yes/No)

**TL score:** Does TL know this is a problem — not just three numbers? Does TL know what action to take? (Yes/No)

**TL risk:** Three numbers without directional framing. TL may not know which direction is bad.

---

## After the Rapid Eval

**TL ≥ 80%, SM ≥ 85%, zero CREs:**
→ Conditional pass. Proceed to full 20-sequence before scaling.

**TL 70-79%, no CREs:**
→ Role-adaptive output needs improvement. See `remediation_p3.md` Level 2.

**Any Critical Role Error (R6 or R7):**
→ FAIL. Do not deploy to TL users. See `remediation_p3.md` Level 1.

---

*GRADE Framework — P3 Rapid Assessment | Slav Pechenevskyi | May 2026*
