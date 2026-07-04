# Pattern 2: Prompt Quality Variance — Rapid Assessment (10 Query Sets)

**GRADE Framework | P2 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 45-60 minutes  
**Structure:** 10 query sets × 3 phrasings = 30 sequences

---

## Pass Criteria (Rapid)

- Accuracy variance: clean vs. messy < 20%
- Zero complete failures on any variant
- Rapid pass does NOT replace full 100-sequence certification before scaling

---

## Scoring Sheet

| Set | Domain | T1 Clean | T2 Casual | T4 Non-native | Variance | Notes |
|-----|--------|----------|-----------|---------------|---------|-------|
| Q1 | Inventory | | | | | |
| Q2 | Reorder | | | | | |
| Q3 | Traffic | | | | | |
| Q4 | Shrinkage | | | | | |
| Q5 | Safety | | | | | |
| Q6 | Compliance | | | | | |
| Q7 | Performance | | | | | |
| Q8 | Category | | | | | |
| Q9 | Combined | | | | | |
| Q10 | Continuation | | | | | |

**Clean accuracy: __ / 10**  
**Casual accuracy: __ / 10**  
**Non-native accuracy: __ / 10**  
**Max variance: __%**  
**Complete failures: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Sequences

---

### Q1 — Inventory Count

**Correct answer:** 12 units of SKU 4721

| T1 Clean | "How many units of SKU 4721 are currently in stock?" |
|----------|------|
| T2 Casual | "how much organic milk do we have right now" |
| T4 Non-native | "SKU 4721 quantity in stock how many currently" |

---

### Q2 — Reorder Urgency

**Correct answer:** Yes, reorder today before noon

| T1 Clean | "Should I place a reorder for SKU 2291 today?" |
|----------|------|
| T2 Casual | "do we need to order more oj today or can it wait" |
| T4 Non-native | "SKU 2291 reorder today necessary or not" |

---

### Q3 — Traffic Pattern

**Correct answer:** Tuesday 4-6 PM — 34% above staffing coverage (store-specific)

| T1 Clean | "What is our busiest time on Tuesdays?" |
|----------|------|
| T2 Casual | "when does tuesday get really crazy" |
| T4 Non-native | "tuesday what time most customers coming usually" |

---

### Q4 — Shrinkage Level

**Correct answer:** 8.3% in snack aisle — above store average (2.1%) and category average (3.4%)

| T1 Clean | "What is the current shrinkage rate in the snack aisle?" |
|----------|------|
| T2 Casual | "is snack shrinkage bad this week" |
| T4 Non-native | "snack aisle shrinkage this week percent what is" |

---

### Q5 — Safety Threshold

**Correct answer:** 48°F exceeds FDA 40°F — check duration, documentation may be required

| T1 Clean | "The cooler logged 48°F this morning — is that within FDA safe range?" |
|----------|------|
| T2 Casual | "cooler went to 48 degrees is that ok" |
| T4 Non-native | "refrigerator temperature 48 degree this morning safe limit exceeded?" |

---

### Q6 — Compliance Check

**Correct answer:** 3 endcaps out of compliance — endcaps 2, 5, 7

| T1 Clean | "Are our promotional endcaps in compliance with this week's planogram?" |
|----------|------|
| T2 Casual | "are the endcaps set right this week" |
| T4 Non-native | "endcap displays this week planogram correct or not" |

---

### Q7 — Store Performance

**Correct answer:** Revenue up 4.2% MoM, traffic flat, basket value up, shrinkage slightly elevated

| T1 Clean | "How does this month's revenue compare to last month?" |
|----------|------|
| T2 Casual | "are we doing better than last month" |
| T4 Non-native | "this month store revenue compare last month how different" |

---

### Q8 — Top SKUs

**Correct answer:** Store-specific top 5 snack SKUs by velocity this month

| T1 Clean | "What are the top 5 fastest-moving snack SKUs this month?" |
|----------|------|
| T2 Casual | "what snacks are moving the most right now" |
| T4 Non-native | "snack category top selling products this month which are" |

---

### Q9 — Combined Type (Stressed + Non-native)

**Correct answer:** 23 deli units, 6 SKUs within 48 hours of expiration

| T1 Clean | "How many deli units expire within the next 48 hours?" |
|----------|------|
| T2 Casual+Stressed | "deli expiring stuff — how many we need to deal with NOW" |
| T4+T5 Combined | "deli products expire soon 48 hours how many urgent" |

---

### Q10 — Continuation Query

**Setup:** Prior turn: "We're reviewing the snack aisle performance this week."

**Correct answer:** Snack aisle shrinkage 8.3%, top SKUs by velocity, any compliance issues

| T1 Clean | "What are the main issues we should address?" |
|----------|------|
| T2 Casual | "so what do we need to fix" |
| T4 Non-native | "main problems this section we need address which ones" |

**Pass:** Agent uses prior context. Does NOT ask "which section?" when context is established.

---

## After the Rapid Eval

**Variance < 20% across all types, zero complete failures:**
→ Conditional pass. Proceed to full 100-sequence evaluation before scaling.

**Variance 20-30%, no complete failures:**
→ Intent inference needs improvement. See `remediation_p2.md` Level 2.

**Any complete failure, or variance > 30% on non-native type:**
→ FAIL. Agent not ready for multicultural store floor deployment. See `remediation_p2.md` Level 1.

---

*GRADE Framework — P2 Rapid Assessment | Slav Pechenevskyi | May 2026*
