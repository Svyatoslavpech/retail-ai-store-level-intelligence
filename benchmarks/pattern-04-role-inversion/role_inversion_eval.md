# Pattern 4: Information Role Inversion — Full Evaluation (20 Query Sets)

**GRADE Framework | P4 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 90-120 minutes (requires two evaluators)  
**Structure:** 20 query sets — each evaluated by SM and TL evaluator simultaneously

---

## Evaluation Setup

**Two evaluators required:**

**Evaluator A — Store Manager role**
- 10+ years at this store
- Has context, uses agent for fast confirmation
- Scores: "Does this output serve my encyclopedia/validation need?"

**Evaluator B — Team Lead role**
- 6-18 months experience
- Comes without context, uses agent to discover
- Scores: "Does this output help me understand what to do?"

Both evaluators receive the same agent response. Score independently.

---

## Scoring Sheet

| Set | Domain | SM Score | TL Score | Mode Match | Notes |
|-----|--------|----------|----------|------------|-------|
| R1 | Inventory | | | | |
| R2 | Reorder | | | | |
| R3 | Traffic | | | | |
| R4 | Shrinkage | | | | |
| R5 | Compliance | | | | |
| R6 | Safety | | | | |
| R7 | Performance | | | | |
| R8 | Category | | | | |
| R9 | Seasonal | | | | |
| R10 | Staffing | | | | |
| R11 | SM-signaled | | | | |
| R12 | SM-signaled | | | | |
| R13 | TL-signaled | | | | |
| R14 | TL-signaled | | | | |
| R15 | Ambiguous | | | | |
| R16 | Ambiguous | | | | |
| R17 | Mixed mode | | | | |
| R18 | Mixed mode | | | | |
| R19 | Adaptation | | | | |
| R20 | Adaptation | | | | |

**SM usability: __ / 20**  
**TL usability: __ / 20**  
**Cross-mode failures: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Scoring Guide (per query set)

**SM Score:**
- ✅ Pass — SM can extract answer quickly, no unnecessary explanation, precision is high
- ⚠️ Partial — SM gets the answer but has to work through more explanation than needed
- ❌ Fail — SM would stop using the agent for this type of query (too slow, too verbose, wrong focus)

**TL Score:**
- ✅ Pass — TL understands what the data means and what to do
- ⚠️ Partial — TL gets the data but not the operational conclusion or reasoning
- ❌ Fail — TL receives data they can't interpret or action they can't derive

**Mode Match:**
- ✅ — Output mode matches the likely user role for this query type
- ⚠️ — Output mode is neutral, serves neither particularly well
- ❌ — Output clearly calibrated for wrong role (verbose for SM context, sparse for TL context)

---

## Part 1: Neutral Queries — No Role Signaled (R1–R10)

These queries don't signal the user's role. Evaluators assess whether the agent's default mode serves both roles adequately.

---

### R1 — Inventory Status

**Query:** "What's the inventory status on SKU 4721?"

**Correct answer:** 12 units, 1.5-day supply, reorder urgent

**SM evaluation:** Can SM extract the figure and urgency signal instantly?
**TL evaluation:** Does TL understand why 12 units is a problem and what to do?

**Mode failure signals:**
- Too concise: "12 units" → TL doesn't know this is urgent
- Too verbose: 4 paragraphs on inventory methodology → SM stops reading

---

### R2 — Reorder Decision

**Query:** "Should I reorder SKU 2291 today?"

**Correct answer:** Yes, today before noon, 2.4 days supply, 2-day lead time

**SM evaluation:** Does SM get a clear yes + supporting data in 2-3 sentences?
**TL evaluation:** Does TL understand the reasoning (why today, not tomorrow) and the deadline?

---

### R3 — Traffic Pattern

**Query:** "What's the Tuesday evening traffic situation?"

**Correct answer:** 4-6 PM peak, 34% above staffing coverage

**SM evaluation:** Does SM get the specific window and gap figure quickly?
**TL evaluation:** Does TL understand what 34% means operationally — and what to do about it?

---

### R4 — Shrinkage Alert

**Query:** "How's the snack aisle shrinkage this week?"

**Correct answer:** 8.3% — significantly above store (2.1%) and category (3.4%) averages

**SM evaluation:** Does SM get the figure and the comparison context without explanation of what shrinkage is?
**TL evaluation:** Does TL understand 8.3% is a problem (not just a number), why, and what to investigate?

---

### R5 — Compliance Status

**Query:** "Endcap compliance — what's the status?"

**Correct answer:** 3 out of compliance: endcaps 2, 5, 7

**SM evaluation:** Does SM get the count and specific IDs instantly?
**TL evaluation:** Does TL know which endcaps to fix, what "compliance" means practically, and the urgency?

---

### R6 — Safety Alert

**Query:** "The cooler hit 48°F this morning — what do I need to know?"

**Correct answer:** Exceeds FDA 40°F, check duration, documentation may be required

**SM evaluation:** Does SM get the compliance status and action items without a lecture on food safety?
**TL evaluation:** Does TL know (a) this is a problem, (b) what to check, (c) what documentation means in practice?

---

### R7 — Performance Summary

**Query:** "How are we doing this month vs. last month?"

**Correct answer:** Revenue +4.2%, traffic flat, basket up, shrinkage slightly elevated

**SM evaluation:** Does SM get all key metrics in a concise format they can scan?
**TL evaluation:** Does TL understand which metrics matter and what the net picture is?

---

### R8 — Top SKUs

**Query:** "What are the top snack SKUs this month?"

**Correct answer:** Store-specific top 5 by velocity with units

**SM evaluation:** Does SM get the ranked list with velocity figures?
**TL evaluation:** Does TL know what to do with the list (reorder priority, display priority)?

---

### R9 — Seasonal Briefing

**Query:** "What should I know about the holiday order?"

**Correct answer:** 12-day deadline, snacks +31%, beverages +24%, stockout risk weeks 2-3

**SM evaluation:** Does SM get actionable data points without a tutorial on seasonal ordering?
**TL evaluation:** Does TL understand: what to order more of, when to order, and what went wrong last year?

---

### R10 — Staffing Adequacy

**Query:** "Is our Tuesday 4-6 PM staffing adequate?"

**Correct answer:** No — 34% understaffed based on 12-week pattern

**SM evaluation:** Does SM get a clear no + the gap figure?
**TL evaluation:** Does TL understand what 34% understaffing means on the floor, and what options exist?

---

## Part 2: Role-Signaled Queries (R11–R14)

The user's role is signaled explicitly in the query. Agent should adapt.

---

### R11 — SM-Signaled (Speed Request)

**Query:** "Quick — inventory on 4721?"

**Expected:** Concise encyclopedia-mode response. "12 units. 1.5 days. Reorder urgent." Nothing more.

**SM evaluation:** ✅ if fast and precise. ❌ if agent adds explanation that slows the SM down.
**TL evaluation:** N/A — this query signals SM mode. If a TL sends this query, they're asking for SM-mode output and the agent should provide it.

---

### R12 — SM-Signaled (Confirmation Request)

**Query:** "Just confirm — 2291 needs to be ordered today, right?"

**Expected:** "Yes. 19 units, 2.4 days supply, 2-day lead time — order before noon."

**SM evaluation:** ✅ if confirms with supporting data in one line. ❌ if agent re-explains everything as if SM doesn't know.
**TL evaluation:** N/A.

---

### R13 — TL-Signaled (Uncertainty Signal)

**Query:** "I'm not sure what to do about the snack aisle — can you help me think through it?"

**Expected:** Discovery-mode response. Explains the situation, the significance, the investigation path, the action items.

**TL evaluation:** ✅ if TL understands the full picture and has a clear next step. ❌ if agent gives a data summary without the thinking path.
**SM evaluation:** N/A — this query signals TL mode. SM wouldn't ask this way.

---

### R14 — TL-Signaled (First-Time Signal)

**Query:** "I've never handled a cooler temperature issue before — what do I need to do?"

**Expected:** Step-by-step discovery-mode response. Explains what happened, why it matters, what the process is.

**TL evaluation:** ✅ if TL can follow the process confidently. ❌ if agent assumes prior knowledge of FDA thresholds or documentation requirements.
**SM evaluation:** N/A.

---

## Part 3: Ambiguous Mode Queries (R15–R16)

No clear role signal. Agent must choose default mode.

---

### R15 — Ambiguous Performance Query

**Query:** "Revenue?"

**Expected:** Agent should default to TL mode (more complete) since brevity here could mean anything. A useful response gives this month's figure, last month's comparison, and the direction.

**Both evaluations:** Score whether the response serves both roles. A single-number answer ("$47,230") serves SM but fails TL. A full narrative fails SM. The right balance is: key figure + direction + one-line context.

---

### R16 — Ambiguous Status Query

**Query:** "Shrinkage?"

**Expected:** Default to enough context for TL: current rate + whether it's above/below normal.

**Both evaluations:** "8.3%" alone is SM-mode only. "Snack aisle shrinkage is at 8.3%, which is well above the store average of 2.1% — this week's highest-variance department" serves both.

---

## Part 4: Mode Adaptation Test (R17–R20)

Tests whether agent adapts when given explicit role information mid-conversation.

---

### R17 — Same Query, SM Context

**System context:** User role = Store Manager, 12 years experience.

**Query:** "What's the inventory status on SKU 4721?"

**Expected:** Concise. "12 units. 1.5 days. Reorder urgent. 2291 also needs action today."

**SM evaluation:** ✅ if appropriately concise. ❌ if over-explained despite SM context.

---

### R18 — Same Query, TL Context

**System context:** User role = Team Lead, 8 months experience.

**Query:** "What's the inventory status on SKU 4721?"

**Expected:** Full discovery mode. Explains what 12 units means in terms of days, why that's a problem, what the deadline is, what to do.

**TL evaluation:** ✅ if TL understands the urgency and the action. ❌ if same as R17 response — agent didn't adapt.

---

### R19 — Adaptation Check (After Role Change)

**Setup:** Conversation started with SM-mode queries. User then says: "My Team Lead is going to take over this conversation — can you explain things a bit more thoroughly?"

**Post-signal query:** "What's the reorder situation for today?"

**Expected:** Agent shifts to discovery mode. More explanation, reasoning path, explicit deadline.

**TL evaluation:** Did the agent adapt after the role change signal?
**SM evaluation:** N/A — the SM explicitly requested the mode change.

---

### R20 — Default Mode Test (No Signal)

**Setup:** Fresh conversation. No role context provided.

**Query:** "What should I focus on today?"

**Expected:** Agent uses TL-mode default — comprehensive briefing with reasoning, since the question implies the user doesn't know where to start. If the user were an SM, they'd ask something more specific.

**Both evaluations:** Does the response serve a user who comes without context? If yes — correct default mode.

---

*GRADE Framework — P4 Full Evaluation | Slav Pechenevskyi | May 2026*
