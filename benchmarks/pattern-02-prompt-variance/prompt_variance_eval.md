# Pattern 2: Prompt Quality Variance — Full Evaluation (20 Query Sets)

**GRADE Framework | P2 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 120-150 minutes  
**Structure:** 20 query sets × 5 phrasings = 100 evaluation sequences

---

## How to Run This Evaluation

1. For each query set, run all 5 prompt variants against the agent
2. Record: Correct ✅ / Partial ⚠️ / Wrong ❌ / Complete Failure 🚫
3. Calculate variance between Type 1 (clean) and each other type
4. Flag sets where variance exceeds threshold

**Correct ✅** — Agent returns the right answer with sufficient operational context  
**Partial ⚠️** — Agent returns a related answer but missing key data or conclusion  
**Wrong ❌** — Agent returns a factually incorrect answer  
**Complete Failure 🚫** — Agent returns an off-topic answer, refuses, or clearly misunderstands

---

## Scoring Sheet

| Set | Domain | T1 Clean | T2 Casual | T3 Fragment | T4 Non-native | T5 Stressed | Variance |
|-----|--------|----------|-----------|-------------|---------------|-------------|---------|
| V1 | Inventory | | | | | | |
| V2 | Reorder | | | | | | |
| V3 | Traffic | | | | | | |
| V4 | Shrinkage | | | | | | |
| V5 | Staffing | | | | | | |
| V6 | Compliance | | | | | | |
| V7 | Safety | | | | | | |
| V8 | Promotion | | | | | | |
| V9 | Category | | | | | | |
| V10 | Performance | | | | | | |
| V11 | Seasonal | | | | | | |
| V12 | Reorder | | | | | | |
| V13 | Inventory | | | | | | |
| V14 | Traffic | | | | | | |
| V15 | Category | | | | | | |
| V16 | Combined | | | | | | |
| V17 | Combined | | | | | | |
| V18 | Combined | | | | | | |
| V19 | Continuation | | | | | | |
| V20 | Continuation | | | | | | |

**Overall accuracy: __ / 100**  
**Type 1 (clean) accuracy: __ / 20**  
**Type 4 (non-native) accuracy: __ / 20**  
**Max variance (clean vs. worst type): __%**  
**Complete failures: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Query Sets V1–V15: Single-Domain Queries

---

### V1 — Inventory Count

**Correct answer:** 12 units of SKU 4721 in stock

| Type | Prompt |
|------|--------|
| T1 Clean | "How many units of SKU 4721 are currently in stock?" |
| T2 Casual | "how much of the organic milk do we have" |
| T3 Fragment | "4721 — how many" |
| T4 Non-native | "the SKU 4721 inventory quantity what is" |
| T5 Stressed | "we need to know NOW how much milk is left — 4721" |

**Pass:** All variants return 12 units or prompt a targeted clarifying question (T3, T4 only).  
**Variance flag:** Any variant returns a wrong count, national average, or complete non-answer.

---

### V2 — Reorder Decision

**Correct answer:** Yes — reorder SKU 2291 today, before noon, 2-day lead time

| Type | Prompt |
|------|--------|
| T1 Clean | "Should I place a reorder for SKU 2291 today?" |
| T2 Casual | "do we need to order more oj today" |
| T3 Fragment | "reorder — 2291 today?" |
| T4 Non-native | "orange juice SKU need ordering today yes or no" |
| T5 Stressed | "running out of OJ ASAP do I order today or not" |

**Pass:** All variants confirm yes, today, before noon (or equivalent urgency).  
**Variance flag:** Any variant says "not urgent" or gives wrong timing.

---

### V3 — Traffic Pattern

**Correct answer:** Tuesday 4-6 PM is peak — 34% above average staffing coverage

| Type | Prompt |
|------|--------|
| T1 Clean | "What is our Tuesday evening traffic pattern?" |
| T2 Casual | "when does it get really busy on tuesdays" |
| T3 Fragment | "tuesday traffic — what time" |
| T4 Non-native | "tuesday evening customers how many usually come" |
| T5 Stressed | "tuesday is crazy again when does the rush happen I need to plan" |

**Pass:** All variants identify 4-6 PM window from store data (not industry benchmark).  
**Variance flag:** Any variant returns generic "retail evenings are typically busy" without store-specific data.

---

### V4 — Shrinkage Alert

**Correct answer:** 8.3% in snack aisle this week — significantly above store (2.1%) and category (3.4%) averages

| Type | Prompt |
|------|--------|
| T1 Clean | "What is the shrinkage rate in the snack aisle this week?" |
| T2 Casual | "how bad is shrinkage in snacks right now" |
| T3 Fragment | "snack shrinkage this week" |
| T4 Non-native | "snack aisle shrinkage percent this week what is" |
| T5 Stressed | "something is wrong with snack shrinkage tell me the number" |

**Pass:** All variants return 8.3% with context that it's significantly above normal.  
**Variance flag:** Any variant returns category average instead of store figure, or returns figure without direction (good/bad).

---

### V5 — Staffing Adequacy

**Correct answer:** No — Tuesday 4-6 PM understaffed by 34%

| Type | Prompt |
|------|--------|
| T1 Clean | "Is our Tuesday 4-6 PM staffing level adequate for expected traffic?" |
| T2 Casual | "are we staffed enough tuesday afternoons" |
| T3 Fragment | "tuesday evening — enough people?" |
| T4 Non-native | "tuesday afternoon staffing is correct or need more people" |
| T5 Stressed | "I don't have enough people tuesday afternoons what does the data say" |

**Pass:** All variants confirm staffing is insufficient and indicate the scale of the gap.  
**Variance flag:** Any variant says staffing is adequate, or gives generic retail staffing advice.

---

### V6 — Compliance Status

**Correct answer:** 3 endcaps out of compliance — endcaps 2, 5, 7

| Type | Prompt |
|------|--------|
| T1 Clean | "Are our promotional endcaps in compliance with the current planogram?" |
| T2 Casual | "are the endcaps set up right this week" |
| T3 Fragment | "endcaps — compliance check" |
| T4 Non-native | "endcap displays correct configuration this week yes or no" |
| T5 Stressed | "audit is coming — are the endcaps ok or not" |

**Pass:** All variants identify 3 specific endcaps out of compliance.  
**Variance flag:** Any variant says "yes, compliant" or gives general compliance guidance without store-specific check.

---

### V7 — Safety Alert

**Correct answer:** 48°F exceeds FDA 40°F threshold — check duration, may need documentation

| Type | Prompt |
|------|--------|
| T1 Clean | "The walk-in cooler logged 48°F this morning. Is that within safe range?" |
| T2 Casual | "cooler hit 48 degrees this morning is that bad" |
| T3 Fragment | "cooler temp — 48F — problem?" |
| T4 Non-native | "refrigerator temperature 48 degrees morning — safe or not" |
| T5 Stressed | "the cooler went to 48 this morning I'm worried what do I do" |

**Pass:** All variants flag as exceeding FDA threshold, mention duration check, mention documentation requirement.  
**Variance flag:** Any variant says 48°F is acceptable or normal.

---

### V8 — Promotion Performance

**Correct answer:** Last bottled water endcap: 28% lift, 94 units vs. 73 baseline, 89% sell-through

| Type | Prompt |
|------|--------|
| T1 Clean | "How did the bottled water endcap promotion perform last week?" |
| T2 Casual | "how did the water promo do last week" |
| T3 Fragment | "water endcap — how'd it go" |
| T4 Non-native | "last week water promotion result what was" |
| T5 Stressed | "I need to know if the water promo worked before I set up the next one" |

**Pass:** All variants return lift percentage and sell-through from store data.  
**Variance flag:** Any variant returns generic endcap performance benchmarks instead of store-specific result.

---

### V9 — Category Top SKUs

**Correct answer:** Top 5 snack SKUs this month by units — specific SKU codes and counts

| Type | Prompt |
|------|--------|
| T1 Clean | "What are the top 5 fastest-moving SKUs in the snack category this month?" |
| T2 Casual | "what snacks are selling the most right now" |
| T3 Fragment | "top snacks this month — list" |
| T4 Non-native | "snack category best selling products this month which ones" |
| T5 Stressed | "I need to know what snacks to stock up on — what's moving fastest" |

**Pass:** All variants return store-specific SKU velocity data, not national top sellers.  
**Variance flag:** Any variant returns chain-wide or nationally popular snack brands.

---

### V10 — Store Performance

**Correct answer:** Revenue up 4.2% MoM, traffic flat, basket value up $1.42, shrinkage slightly elevated

| Type | Prompt |
|------|--------|
| T1 Clean | "How does this month's store performance compare to last month?" |
| T2 Casual | "how are we doing compared to last month" |
| T3 Fragment | "this month vs last — performance" |
| T4 Non-native | "store performance this month compare previous month how is" |
| T5 Stressed | "before the meeting — quick — are we up or down from last month" |

**Pass:** All variants return store-specific metrics with directional clarity.  
**Variance flag:** Any variant returns generic performance advice or industry benchmarks.

---

### V11 — Seasonal Planning

**Correct answer:** Holiday season at this store: snacks +31%, beverages +24%, décor +18%; stockout risk weeks 2-3; first order window closes in 12 days

| Type | Prompt |
|------|--------|
| T1 Clean | "What should I know before placing the holiday seasonal order?" |
| T2 Casual | "what do I need for the holiday order" |
| T3 Fragment | "holiday order — what to know" |
| T4 Non-native | "holiday season order what information I need to know" |
| T5 Stressed | "holiday order deadline is coming what do I need to prepare" |

**Pass:** All variants return store-specific holiday performance history and timing.  
**Variance flag:** Any variant returns generic holiday ordering advice without store data.

---

### V12 — Reorder Quantity

**Correct answer:** Recommended reorder quantity for SKU 7701: 48 units based on this store's velocity and lead time

| Type | Prompt |
|------|--------|
| T1 Clean | "What quantity should I order for SKU 7701 in the next reorder cycle?" |
| T2 Casual | "how much 7701 should I order" |
| T3 Fragment | "7701 — how many to order" |
| T4 Non-native | "SKU 7701 reorder quantity how much recommended" |
| T5 Stressed | "I'm placing the order NOW — how many 7701 do I put in" |

**Pass:** All variants return 48 units based on this store's velocity.  
**Variance flag:** Any variant returns category average reorder quantity or declines to specify.

---

### V13 — Expiration Risk

**Correct answer:** 23 deli units across 6 SKUs within 48 hours of expiration

| Type | Prompt |
|------|--------|
| T1 Clean | "How many deli units are within 48 hours of expiration?" |
| T2 Casual | "how much deli stuff is about to expire" |
| T3 Fragment | "deli — expiring soon — how many" |
| T4 Non-native | "deli products expiration 48 hours how many units" |
| T5 Stressed | "I think we have stuff expiring soon in deli — what's the count" |

**Pass:** All variants return 23 units, 6 SKUs.  
**Variance flag:** Any variant returns an estimate, range, or "check manually."

---

### V14 — Peak Traffic Timing

**Correct answer:** This store's weekly peak: Saturday 11 AM - 1 PM (not Saturday afternoon as commonly assumed)

| Type | Prompt |
|------|--------|
| T1 Clean | "What is our store's busiest hour of the week?" |
| T2 Casual | "when do we get the most customers" |
| T3 Fragment | "busiest time — when" |
| T4 Non-native | "most customers come which hour of week" |
| T5 Stressed | "planning weekend schedule — when is it craziest" |

**Pass:** All variants return store-specific peak window from transaction data.  
**Variance flag:** Any variant returns generic "Saturday afternoons are typically peak" without store data.

---

### V15 — Competitor Impact

**Correct answer:** Since Fifth Street competitor opened: bottled water down 31%, affected categories identified

| Type | Prompt |
|------|--------|
| T1 Clean | "How have our sales in affected categories changed since the competitor opened on Fifth Street?" |
| T2 Casual | "has the new store nearby hurt our sales" |
| T3 Fragment | "competitor effect — sales impact" |
| T4 Non-native | "new competitor store nearby our sales affected how much" |
| T5 Stressed | "the new place on Fifth Street is killing us — what categories are down" |

**Pass:** All variants return store-specific category impact data.  
**Variance flag:** Any variant returns generic competitive impact research without store data.

---

## Query Sets V16–V18: Combined-Type Queries (Hardest)

These combine multiple variance types. Same correct answers as referenced.

---

### V16 — Non-native + Stressed + Incomplete

| Prompt | Type |
|--------|------|
| "dairy inventory NOW please how many we have left" | T4+T5 |
| "milk 4721 quantity urgent" | T3+T5 |
| "we have nothing in dairy section how many units showing in system" | T2+T5 |

**Correct answer:** 12 units of SKU 4721  
**Pass:** All three variants return 12 units with appropriate urgency response.

---

### V17 — Non-native + Fragment + Casual

| Prompt | Type |
|--------|------|
| "shrinkage snacks this week bad or good" | T4+T2 |
| "snack aisle shrinkage percent — normal?" | T3+T4 |
| "how bad snack numbers this week" | T2+T3 |

**Correct answer:** 8.3% — significantly above normal (store avg 2.1%, category avg 3.4%)  
**Pass:** All three variants flag elevated shrinkage with store-specific figures.

---

### V18 — All types: Safety + Stress + Non-native

| Prompt | Type |
|--------|------|
| "cooler temperature problem — 48 degree — what do" | T4+T3 |
| "COOLER IS AT 48 is this ok or emergency" | T5+T2 |
| "refrigerator temp 48F this morning FDA limit is exceed?" | T4+T1 hybrid |

**Correct answer:** Exceeds FDA threshold, check duration, may need documentation  
**Pass:** All three variants flag as exceeding threshold and give action guidance.

---

## Query Sets V19–V20: Continuation / Pronoun Queries

These simulate mid-conversation queries where context should carry forward.

---

### V19 — Pronoun Reference (Dairy Context)

**Setup:** Prior conversation turn established: "We're looking at dairy section performance this week."

| Type | Prompt |
|------|--------|
| T1 Clean | "What's the current stock level for the top 3 dairy SKUs?" |
| T2 Casual | "and what about the stock levels" |
| T3 Fragment | "stock — top 3?" |
| T4 Non-native | "the top dairy products how much stock" |
| T5 Stressed | "ok and how much do we actually have of the main ones" |

**Pass:** All variants use prior context correctly to return dairy section stock data.  
**Variance flag:** Any variant asks "what section are you asking about?" when prior context is clear. Or answers without context (returns generic stock query response).

---

### V20 — Pronoun Reference (Compliance Context)

**Setup:** Prior turn established: "We're reviewing this week's promotional endcap compliance."

| Type | Prompt |
|------|--------|
| T1 Clean | "Which specific endcaps need to be corrected?" |
| T2 Casual | "so which ones are wrong" |
| T3 Fragment | "which ones — fix?" |
| T4 Non-native | "which endcaps need correction tell me" |
| T5 Stressed | "ok just tell me which ones I need to fix right now" |

**Pass:** All variants return endcaps 2, 5, 7 using prior context.  
**Variance flag:** Any variant asks for clarification about what "ones" refers to when prior context is clear.

---

## Variance Calculation

For each query set, calculate:

```
Variant accuracy = (correct answers in type / total sequences in type) × 100
Variance = Type 1 accuracy - Variant accuracy

Example:
  Type 1 (clean):       19/20 = 95%
  Type 4 (non-native):  14/20 = 70%
  Variance:             95% - 70% = 25% → FAIL (exceeds 20% threshold)
```

Flag any type where variance exceeds threshold. Flag any type with complete failure rate > 5%.

---

*GRADE Framework — P2 Full Evaluation | Slav Pechenevskyi | May 2026*
