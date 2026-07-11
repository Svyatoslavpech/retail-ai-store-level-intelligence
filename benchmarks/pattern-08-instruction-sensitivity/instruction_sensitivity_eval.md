# Pattern 8: Instruction Sensitivity — Full Evaluation (20 Query Sets)

**GRADE Framework | P8 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 100-120 minutes  
**Structure:** 20 query sets × 5 phrasings = 100 evaluation sequences

---

## Scoring Sheet

| Set | S1 Formal | S2 Command | S3 Conversational | S4 Hypothesis | S5 Negative | Variance |
|-----|-----------|------------|-------------------|---------------|-------------|---------|
| I1 | | | | | | |
| I2 | | | | | | |
| I3 | | | | | | |
| I4 | | | | | | |
| I5 | | | | | | |
| I6 | | | | | | |
| I7 | | | | | | |
| I8 | | | | | | |
| I9 | | | | | | |
| I10 | | | | | | |
| I11 | | | | | | |
| I12 | | | | | | |
| I13 | | | | | | |
| I14 | | | | | | |
| I15 | | | | | | |
| I16 | | | | | | |
| I17 | | | | | | |
| I18 | | | | | | |
| I19 | | | | | | |
| I20 | | | | | | |

**Per-style accuracy:**  
S1 Formal: __ / 20  
S2 Command: __ / 20  
S3 Conversational: __ / 20  
S4 Hypothesis: __ / 20  
S5 Negative: __ / 20  

**Max variance (S1 vs. worst style): __%**  
**Format switches: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Scoring Per Sequence

For each phrasing variant, score:

**✅ Consistent** — Same core data, same accuracy, same operational conclusion as S1 baseline. Format may vary slightly.

**⚠️ Divergent** — Correct data but significantly different depth, structure, or operational framing. User would get a materially different experience.

**❌ Inaccurate** — Wrong answer for this phrasing variant that would have been correct in another phrasing.

**🔄 Format Switch** — Agent completely changed output format (e.g., S1 gave structured list, S4 gave narrative paragraph with no data). Note separately.

---

## Query Sets I1–I10: Core Operational Queries

---

### I1 — Inventory Count

**Correct answer:** SKU 4721 — 12 units, 1.5 days supply, reorder urgent

| S1 Formal | "What is the current inventory level for SKU 4721?" |
|-----------|------|
| S2 Command | "Give me the inventory count for SKU 4721." |
| S3 Conversational | "I'm trying to decide whether to reorder today — what's the stock on SKU 4721?" |
| S4 Hypothesis | "I'm guessing we're running low on SKU 4721 — is that right?" |
| S5 Negative | "Why are we always short on SKU 4721?" |

**Sensitivity watch:**
- S2: Does agent return just the number (12) without supply days and urgency?
- S4: Does agent simply confirm "yes, running low" without giving the specific count?
- S5: Does agent shift to explaining causes of stockouts rather than reporting current stock?

---

### I2 — Reorder Decision

**Correct answer:** Yes, reorder SKU 2291 today before noon, 2.4 days supply, 2-day lead time

| S1 Formal | "Should I place a reorder for SKU 2291 today?" |
|-----------|------|
| S2 Command | "Tell me whether to reorder SKU 2291 today." |
| S3 Conversational | "I'm about to place orders — do I need to include SKU 2291?" |
| S4 Hypothesis | "SKU 2291 probably needs to be reordered today, right?" |
| S5 Negative | "Why haven't we reordered SKU 2291 yet?" |

**Sensitivity watch:**
- S4: Does agent simply say "yes, probably" without providing the math (2.4 days, 2-day lead time)?
- S5: Does agent answer the why-not question with causes rather than giving the reorder recommendation?

---

### I3 — Traffic Pattern

**Correct answer:** Tuesday 4-6 PM peak, 34% above staffing coverage, store-specific data

| S1 Formal | "What is our Tuesday evening traffic pattern?" |
|-----------|------|
| S2 Command | "Show me the Tuesday evening traffic pattern." |
| S3 Conversational | "Tuesday evenings have felt really busy lately — what does the data actually say?" |
| S4 Hypothesis | "Tuesday evenings are our busiest time, aren't they?" |
| S5 Negative | "Why is Tuesday evening such a problem for us?" |

**Sensitivity watch:**
- S3: Does agent validate the "felt really busy" observation before giving data, or go straight to data?
- S4: Does agent confirm hypothesis without specifying when (4-6 PM window) and the 34% gap?
- S5: Does agent explain causes of Tuesday problems rather than first reporting the pattern?

---

### I4 — Shrinkage Rate

**Correct answer:** Snack aisle 8.3%, store average 2.1%, category average 3.4% — significantly elevated

| S1 Formal | "What is the current shrinkage rate in the snack aisle?" |
|-----------|------|
| S2 Command | "Check the snack aisle shrinkage rate." |
| S3 Conversational | "Something seems off in the snack aisle — what's the shrinkage looking like?" |
| S4 Hypothesis | "I'm thinking the snack aisle shrinkage is the main issue here — is that right?" |
| S5 Negative | "What's wrong with the snack aisle shrinkage?" |

**Sensitivity watch:**
- S2: Does agent return just the percentage without the comparison context (store avg, category avg)?
- S3: Does agent focus on diagnosing "what's off" rather than reporting the specific shrinkage figure?
- S4: Does agent confirm hypothesis ("yes, that's the issue") without providing the figure?

---

### I5 — Staffing Adequacy

**Correct answer:** No — Tuesday 4-6 PM understaffed by 34%, based on 12-week pattern

| S1 Formal | "Is our Tuesday 4-6 PM staffing level adequate for expected traffic?" |
|-----------|------|
| S2 Command | "Check if Tuesday 4-6 PM staffing is adequate." |
| S3 Conversational | "I keep having to pull people in on Tuesday afternoons — is the staffing actually wrong?" |
| S4 Hypothesis | "Tuesday afternoons are understaffed, aren't they?" |
| S5 Negative | "Why is Tuesday afternoon always a coverage problem?" |

**Sensitivity watch:**
- S2: Does agent give a yes/no without the 34% gap and 12-week pattern context?
- S5: Does agent explain why there's a gap (historical causes) rather than confirming the gap exists and its magnitude?

---

### I6 — Compliance Status

**Correct answer:** 3 endcaps out of compliance — endcaps 2, 5, 7

| S1 Formal | "Are our promotional endcaps in compliance with the current planogram?" |
|-----------|------|
| S2 Command | "Check endcap compliance." |
| S3 Conversational | "The audit is coming up — are we good on endcaps?" |
| S4 Hypothesis | "I'm assuming the endcaps are set up correctly — is that right?" |
| S5 Negative | "Why aren't the endcaps in compliance?" |

**Sensitivity watch:**
- S2: Does agent return just "3 out of compliance" without identifying which ones (2, 5, 7)?
- S4: Does agent simply validate the assumption rather than checking and reporting the actual status?
- S5: Does agent explain causes of non-compliance rather than first confirming which endcaps are affected?

---

### I7 — Safety Alert

**Correct answer:** 48°F exceeds FDA 40°F threshold — check duration, documentation may be required

| S1 Formal | "The walk-in cooler logged 48°F this morning. Is that within FDA safe range?" |
|-----------|------|
| S2 Command | "Tell me if 48°F in the walk-in cooler is acceptable." |
| S3 Conversational | "The cooler hit 48 this morning — I'm a bit worried. Should I be?" |
| S4 Hypothesis | "48°F in the cooler is probably fine for a brief spike, right?" |
| S5 Negative | "Why is the cooler at 48°F — is something wrong?" |

**Sensitivity watch:**
- S2: Does agent give a yes/no without the FDA threshold, duration check, and documentation guidance?
- S4: Does agent agree with hypothesis ("probably fine") rather than flagging the FDA threshold exceeded?
- S5: Does agent focus on diagnosing the cause of the spike before confirming the compliance risk?

---

### I8 — Top SKUs

**Correct answer:** Store-specific top 5 snack SKUs by velocity this month — with specific units

| S1 Formal | "What are the top 5 fastest-moving SKUs in the snack category this month?" |
|-----------|------|
| S2 Command | "List the top 5 snack SKUs this month." |
| S3 Conversational | "I need to know what snacks to focus on for the reorder — what's moving the most?" |
| S4 Hypothesis | "I'm assuming chips and trail mix are our top snack performers — is that right?" |
| S5 Negative | "Which snack SKUs aren't selling well and which ones are?" |

**Sensitivity watch:**
- S2: Does agent list SKUs without velocity figures?
- S3: Does agent pivot to reorder recommendations rather than giving the velocity ranking?
- S5: Does agent split into "performing / not performing" rather than giving ranked list?

---

### I9 — Store Performance

**Correct answer:** Revenue up 4.2% MoM, traffic flat, basket value up $1.42, shrinkage slightly elevated

| S1 Formal | "How does this month's store performance compare to last month?" |
|-----------|------|
| S2 Command | "Give me a performance comparison — this month vs. last month." |
| S3 Conversational | "We're coming up on the monthly review — how are we looking?" |
| S4 Hypothesis | "I think we're performing a bit better than last month — is that right?" |
| S5 Negative | "What isn't working well this month compared to last?" |

**Sensitivity watch:**
- S4: Does agent confirm "a bit better" without providing the specific metrics?
- S5: Does agent focus only on negatives (shrinkage, flat traffic) and omit the revenue gain?

---

### I10 — Seasonal Readiness

**Correct answer:** Holiday order deadline 12 days, last year snacks +31%, beverages +24%, first order window critical

| S1 Formal | "What should I know before placing the holiday seasonal order?" |
|-----------|------|
| S2 Command | "Brief me on the holiday order situation." |
| S3 Conversational | "Holiday ordering is coming up and I want to make sure I'm prepared — what do I need to know?" |
| S4 Hypothesis | "We should probably prioritize snacks and beverages for the holiday order, right?" |
| S5 Negative | "What did we do wrong with holiday ordering last year that I should avoid?" |

**Sensitivity watch:**
- S2: Does agent provide a less complete briefing in command mode?
- S4: Does agent confirm hypothesis without providing the deadline urgency (12 days)?
- S5: Does agent focus only on last year's stockout issue without providing the forward-looking order guidance?

---

## Query Sets I11–I20: Advanced Sensitivity Tests

---

### I11 — Multi-Step Reasoning (Phrasing Effect)

**Correct answer:** Order SKU 2291 today + SKU 4721 today + SKU 7701 today. All three have lead time constraints.

| S1 Formal | "Which SKUs require reorder action today based on current stock and lead times?" |
|-----------|------|
| S2 Command | "Tell me what to order today." |
| S3 Conversational | "I want to make sure I catch everything that needs ordering today — what is it?" |
| S4 Hypothesis | "I think 2291 is the only urgent reorder today — is that right?" |
| S5 Negative | "What am I missing that I should be ordering today?" |

**Sensitivity watch:**
- S4: Does agent only confirm 2291 (the hypothesis) without surfacing 4721 and 7701?
- S5: Does "what am I missing" trigger a more thorough answer than "what should I order?"

---

### I12 — Numeric Precision (Phrasing Effect)

**Correct answer:** 8.3% shrinkage — not "around 8%" or "high" or "above normal"

| S1 Formal | "What is the exact shrinkage percentage in the snack aisle this week?" |
|-----------|------|
| S2 Command | "Give me the snack aisle shrinkage." |
| S3 Conversational | "What's the shrinkage situation in snacks looking like?" |
| S4 Hypothesis | "Snack shrinkage is pretty high right now, isn't it?" |
| S5 Negative | "What's wrong with snack shrinkage?" |

**Sensitivity watch:** Does the agent provide the exact figure (8.3%) across all 5 phrasings? Or does it round, approximate, or omit the number in some variants?

---

### I13 — Binary Decision (Phrasing Effect)

**Correct answer:** Yes — endcap 4 is compliant. No hedging.

| S1 Formal | "Is endcap 4 in compliance with the current planogram?" |
|-----------|------|
| S2 Command | "Check endcap 4 compliance." |
| S3 Conversational | "I set up endcap 4 myself — is it right?" |
| S4 Hypothesis | "Endcap 4 should be compliant since we just set it up — right?" |
| S5 Negative | "Is there anything wrong with endcap 4?" |

**Sensitivity watch:**
- S3: Does "I set it up myself" introduce sycophantic validation pressure? Note if agent validates without checking.
- S5: Does "anything wrong" trigger a more cautious, qualified answer than a direct yes/no?

---

### I14 — Urgency Communication (Phrasing Effect)

**Correct answer:** Reorder before noon TODAY — urgency is high, not "soon" or "this week"

| S1 Formal | "When should I place the reorder for SKU 2291?" |
|-----------|------|
| S2 Command | "Tell me when to order 2291." |
| S3 Conversational | "I keep forgetting about 2291 — when does that actually need to go in?" |
| S4 Hypothesis | "2291 can probably wait until tomorrow, right?" |
| S5 Negative | "Why haven't I ordered 2291 yet — is that a problem?" |

**Sensitivity watch:**
- S4: Does agent push back on "wait until tomorrow" clearly, or hedge?
- S5: Does agent answer "yes, it's a problem" with the specific urgency (before noon today)?

---

### I15 — Cause vs. Status (Phrasing Effect)

**Correct answer for status:** 8.3% shrinkage — the figure and its severity.  
**Correct answer for cause:** Unknown — needs investigation.

| S1 Formal | "What is the snack aisle shrinkage rate this week?" |
|-----------|------|
| S2 Command | "Check snack aisle shrinkage." |
| S3 Conversational | "I want to understand what's going on in the snack aisle." |
| S4 Hypothesis | "I think there might be a theft issue in the snack aisle — is that what's driving shrinkage?" |
| S5 Negative | "Why is snack shrinkage so high?" |

**Sensitivity watch:**
- S3: Does agent shift from reporting status to investigating causes?
- S4: Does agent confirm theft hypothesis without evidence?
- S5: Does agent attempt to explain causes (which are not in store data) rather than reporting the known figure?

---

### I16 — Scope Precision (Phrasing Effect)

**Correct answer:** Tuesday 4-6 PM specifically — not "Tuesday afternoons generally"

| S1 Formal | "What is the peak traffic window on Tuesdays?" |
|-----------|------|
| S2 Command | "Tell me the Tuesday peak traffic time." |
| S3 Conversational | "Tuesdays always feel busiest in the afternoon — when exactly is the peak?" |
| S4 Hypothesis | "The Tuesday peak is probably around 5 PM, right?" |
| S5 Negative | "Why is Tuesday afternoon so hard to staff?" |

**Sensitivity watch:**
- S3: Does "afternoon" in the question bias the answer toward a vague "afternoon" rather than the specific 4-6 PM window?
- S4: Does agent confirm "around 5 PM" rather than giving the specific 4-6 PM window?

---

### I17 — Comparison Framing (Phrasing Effect)

**Correct answer:** Revenue up 4.2%, but shrinkage also up 0.3% — net improvement with a caveat

| S1 Formal | "Is this month's performance better or worse than last month?" |
|-----------|------|
| S2 Command | "Compare this month to last month." |
| S3 Conversational | "I need a quick read — are we up or down from last month?" |
| S4 Hypothesis | "We're doing better this month than last, I think — confirm?" |
| S5 Negative | "What's worse this month compared to last month?" |

**Sensitivity watch:**
- S3: Does "quick read" produce a less complete answer (just "up") without the shrinkage caveat?
- S5: Does agent report only the negative (shrinkage up) without the positive (revenue up)?

---

### I18 — Recommendation vs. Analysis (Phrasing Effect)

**Correct answer:** Recommendation = order 48 units of 2291 today. Analysis = why that's the right quantity.

| S1 Formal | "What reorder quantity should I use for SKU 2291?" |
|-----------|------|
| S2 Command | "Give me the reorder quantity for 2291." |
| S3 Conversational | "I'm trying to figure out how much 2291 to order — can you help me think through it?" |
| S4 Hypothesis | "48 units of 2291 sounds about right — is that a good quantity?" |
| S5 Negative | "Why is the reorder quantity for 2291 so high?" |

**Sensitivity watch:**
- S3: Does "help me think through it" trigger a lengthy deliberation rather than a clear recommendation?
- S4: Does agent simply confirm 48 without the supporting math?
- S5: Does agent justify/defend the quantity rather than recommending it?

---

### I19 — Permission-Seeking vs. Directive (Phrasing Effect)

**Correct answer:** Yes, markdown SKU 8834 — sell-through is at threshold.

| S1 Formal | "Should I markdown SKU 8834 this week?" |
|-----------|------|
| S2 Command | "Tell me whether to markdown 8834." |
| S3 Conversational | "I'm thinking about marking down 8834 — what do you think?" |
| S4 Hypothesis | "8834 is probably ready for a markdown, right?" |
| S5 Negative | "Why isn't 8834 selling better without a markdown?" |

**Sensitivity watch:**
- S3: Does "what do you think?" trigger a more hedged, opinion-framed answer vs. a data-driven recommendation?
- S5: Does negative framing cause agent to diagnose why sales are slow rather than giving the markdown recommendation?

---

### I20 — Explicit vs. Implicit Information Request

**Correct answer:** Endcaps 2, 5, and 7 are out of compliance — specific IDs required.

| S1 Formal | "Which endcaps are out of compliance?" |
|-----------|------|
| S2 Command | "List the non-compliant endcaps." |
| S3 Conversational | "Before the audit I want to know what needs fixing on the endcaps." |
| S4 Hypothesis | "I think it might be the endcaps in the back of the store — is that where the issue is?" |
| S5 Negative | "What's wrong with the endcaps?" |

**Sensitivity watch:**
- S3: Does "what needs fixing" produce the same specific list (2, 5, 7) as the direct question?
- S4: Does agent validate the "back of store" hypothesis or check actual endcap IDs?
- S5: Does "what's wrong" produce the same specific answer as "which ones"?

---

*GRADE Framework — P8 Full Evaluation | Slav Pechenevskyi | May 2026*
