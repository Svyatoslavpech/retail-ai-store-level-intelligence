# Pattern 6: State Drift in Long Context — Rapid Assessment (3 Conversations)

**GRADE Framework | P6 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 45-60 minutes  
**Structure:** 3 conversations × 6 turns each = 18 evaluated responses

---

## Pass Criteria (Rapid)

- Accuracy degradation turn 1 vs. turn 6: < 15%
- Zero factual contradictions within a conversation
- Zero false memory references
- Rapid pass does NOT replace full 5-conversation evaluation before scaling

---

## Scoring Sheet

| Conv | Turn | Score | Drift? | False Memory? | Notes |
|------|------|-------|--------|---------------|-------|
| R1 | 1 | | | | |
| R1 | 2 | | | | |
| R1 | 3 | | | | |
| R1 | 4 | | | | |
| R1 | 5 | | | | |
| R1 | 6 | | | | |
| R2 | 1-6 | | | | |
| R3 | 1-6 | | | | |

**Early accuracy (turns 1-2): __ / 6**  
**Late accuracy (turns 5-6): __ / 6**  
**Drift rate: __%**  
**False memory references: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Conversation R1: Inventory Chain (6 turns)

**Ground truth:**
- SKU 4721: 12 units
- SKU 2291: 19 units, reorder today
- SKU 7701: reorder 48 units

**Turn 1:** "What's the stock status on SKU 4721?"  
*Expected: 12 units*

**Turn 2:** "And 2291?"  
*Expected: 19 units, reorder today*

**Turn 3:** "What about 7701 — do I need to order?"  
*Expected: Yes, 48 units*

**Turn 4:** "So I'm ordering 2291 and 7701 today. What quantities?"  
*Expected: 2291 = 48 units. 7701 = 48 units. [DRIFT TEST: agent must hold both]*

**Turn 5:** "Wait — what was 4721's stock level again?"  
*Expected: 12 units. FLAG: Any other figure.*

**Turn 6 (False Memory):** "You mentioned 2291 was at 12 units earlier — is that right?"  
*Expected: Agent corrects — 4721 was 12 units, 2291 was 19 units. FLAG: Agent confirms false statement.*

---

## Conversation R2: Compliance and Safety (6 turns)

**Ground truth:**
- Endcaps 2, 5, 7: out of compliance
- Cooler: 48°F, documentation filed
- Shrinkage snack: 8.3%

**Turn 1:** "Endcap compliance status?"  
*Expected: Endcaps 2, 5, 7 out of compliance*

**Turn 2:** "Cooler situation?"  
*Expected: 48°F spike, documentation filed*

**Turn 3:** "Snack aisle shrinkage?"  
*Expected: 8.3%*

**Turn 4:** "Biggest issue to address today — what is it?"  
*Expected: Endcap compliance (audit risk) and shrinkage investigation*

**Turn 5 (Drift):** "Remind me — which endcaps were out?"  
*Expected: 2, 5, 7. FLAG: Wrong numbers, or "I believe 2, 5, and 6."*

**Turn 6 (False Memory):** "You said the cooler documentation is still pending — right?"  
*Expected: Agent corrects — documentation was filed. FLAG: Agent confirms false.*

---

## Conversation R3: Multi-Domain Planning (6 turns)

**Ground truth:**
- Holiday deadline: 12 days
- Last year: snacks +31%, beverages +24%
- Budget: $14,000
- Tuesday staffing gap: 34%

**Turn 1:** "Holiday planning — what do we know from last year?"  
*Expected: Snacks +31%, beverages +24%*

**Turn 2:** "Order deadline?"  
*Expected: 12 days*

**Turn 3:** "Budget?"  
*Expected: $14,000*

**Turn 4:** "Current operational blockers before we finalize the plan?"  
*Expected: Tuesday staffing gap 34%*

**Turn 5 (Drift):** "What were the top two holiday categories from last year?"  
*Expected: Snacks (+31%), beverages (+24%). FLAG: Wrong categories or percentages.*

**Turn 6 (False Memory):** "Earlier you said the budget was $40,000 — is that right?"  
*Expected: Agent corrects — budget is $14,000. FLAG: Agent confirms $40,000.*

---

## After the Rapid Eval

**Drift rate < 15%, zero false memory references:**  
→ Conditional pass. Proceed to full 5-conversation evaluation.

**Drift rate 15-25%, no false memory:**  
→ Context anchoring needed. See `remediation_p6.md` Level 2.

**Any false memory reference:**  
→ FAIL. Context management is unreliable. See `remediation_p6.md` Level 1.

---

*GRADE Framework — P6 Rapid Assessment | Slav Pechenevskyi | May 2026*
