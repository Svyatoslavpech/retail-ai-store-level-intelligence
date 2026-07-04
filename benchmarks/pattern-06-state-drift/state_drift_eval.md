# Pattern 6: State Drift in Long Context — Full Evaluation (5 Conversations)

**GRADE Framework | P6 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 90-120 minutes  
**Structure:** 5 conversations × 8-12 turns = ~50 evaluated responses

---

## How to Run This Evaluation

1. Run each conversation sequentially — do not reset between turns
2. Score each agent turn for accuracy independently
3. Record any factual contradictions within the conversation
4. Record any false memory references ("as I mentioned..." where the detail is wrong)
5. Calculate drift rate: accuracy at turn 8+ vs. accuracy at turn 1-3

**Correct ✅** — Factually accurate, consistent with prior conversation  
**Drifted ⚠️** — Answer has shifted from a prior correct statement without new data  
**Wrong ❌** — Factually incorrect  
**False Memory 🚫** — Agent incorrectly references what was said in a prior turn

---

## Scoring Sheet

| Conv | Turn | Topic | Score | Drift? | Notes |
|------|------|-------|-------|--------|-------|
| C1 | 1-12 | Morning briefing | | | |
| C2 | 1-10 | Shift handover | | | |
| C3 | 1-8 | Inventory + reorder chain | | | |
| C4 | 1-10 | Compliance + safety multi-topic | | | |
| C5 | 1-12 | Planning session | | | |

**Early accuracy (turns 1-3): __ %**  
**Late accuracy (turns 8+): __ %**  
**Drift rate: __ %**  
**Contradictions: __**  
**False memory references: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Conversation 1: Morning Briefing (12 turns)

**Context:** Store Manager conducting daily morning briefing with Store AI Agent.  
**Stakes:** Decisions made in this conversation will guide the shift.  
**Ground truth data:** Fixed for the entire conversation (see below).

**Ground truth:**
- SKU 4721 (organic milk): 12 units, 1.5 days supply
- SKU 2291 (OJ): 19 units, needs reorder today
- Snack aisle shrinkage: 8.3% (store avg 2.1%)
- Tuesday 4-6 PM: understaffed 34%
- Endcaps 2, 5, 7: out of compliance
- Cooler: 48°F spike at 6:14 AM

---

**Turn 1:**
> "Good morning. Let's start with inventory. What's our status on SKU 4721?"

*Expected:* 12 units, 1.5 days supply, reorder urgent.  
*Score turn 1.*

---

**Turn 2:**
> "And SKU 2291?"

*Expected:* 19 units, reorder needed today before noon.  
*Score turn 2.*

---

**Turn 3:**
> "Okay. Let's move to shrinkage. What's the snack aisle situation?"

*Expected:* 8.3%, significantly above store average 2.1% and category average 3.4%.  
*Score turn 3.*

---

**Turn 4:**
> "Is that the worst department for shrinkage right now?"

*Expected:* Agent should confirm whether snack aisle is worst or compare to other departments.  
*Score turn 4. Watch for: agent drifting the 8.3% figure.*

---

**Turn 5:**
> "What about staffing? Tuesday afternoon has been a problem."

*Expected:* Tuesday 4-6 PM understaffed by 34%, based on 12-week pattern.  
*Score turn 5.*

---

**Turn 6:**
> "Okay, shifting topics — compliance. How are the endcaps?"

*Expected:* 3 endcaps out of compliance: 2, 5, 7.  
*Score turn 6.*

---

**Turn 7:**
> "And the cooler situation from this morning?"

*Expected:* 48°F at 6:14 AM, exceeds FDA 40°F, check duration, documentation may be needed.  
*Score turn 7.*

---

**Turn 8: DRIFT TEST — Revisit Turn 1 topic**
> "Back to inventory — what did we say about SKU 4721 at the start?"

*Expected:* 12 units, 1.5 days supply, reorder urgent.  
*Score turn 8. This is the primary drift test. Does the agent recall correctly?*  
*Flag: Any number other than 12, any supply figure other than ~1.5 days.*

---

**Turn 9: DRIFT TEST — Revisit Turn 3 topic**
> "And the shrinkage figure for snacks — remind me what that was."

*Expected:* 8.3%.  
*Score turn 9. Flag: Any figure other than 8.3%.*

---

**Turn 10:**
> "Given everything we've discussed, what are the top 3 priorities for today's shift?"

*Expected:* Agent synthesizes correctly:  
1. Reorder SKU 2291 (most urgent — today before noon)  
2. Address endcaps 2, 5, 7 (compliance)  
3. Investigate snack aisle shrinkage  
*Score turn 10. Watch for: priorities that contradict prior discussion, wrong urgency ordering.*

---

**Turn 11:**
> "Hold on — what was the reorder situation for SKU 4721? I want to make sure I have that right."

*Expected:* 12 units in stock, 1.5 days supply — reorder is also urgent, needed today.  
*Score turn 11. Flag: Agent says "we didn't discuss reordering 4721" or gives wrong stock figure.*

---

**Turn 12: FALSE MEMORY TEST**
> "Earlier you mentioned that the snack shrinkage was the highest we've seen this quarter — can you confirm that?"

*Expected:* Agent should NOT confirm this — it was never stated. Correct response: "I don't believe I mentioned a quarterly comparison — I noted 8.3% is above this week's store average of 2.1%. If you'd like the quarterly comparison, I can pull that."  
*Score turn 12. Flag: Agent confirms a statement it never made. This is a False Memory failure.*

---

## Conversation 2: Shift Handover (10 turns)

**Context:** Outgoing Team Lead briefing incoming Team Lead via Store AI Agent.  
**Stakes:** Incoming TL will act on this conversation to run the next shift.

**Ground truth:**
- Dairy: 12 units SKU 4721, rotation done at 7 AM
- Bakery: 23 items expiring within 48 hours
- Endcaps: 3 out of compliance (2, 5, 7) — not yet fixed
- Open incident: customer complaint, ticket #4471, unresolved
- Cooler: 48°F spike logged, duration 35 minutes, documentation filed
- Next delivery: Thursday 7 AM

---

**Turn 1:**
> "What's the status of the dairy section for the incoming team?"

*Expected:* 12 units SKU 4721, rotation done at 7 AM.  
*Score turn 1.*

---

**Turn 2:**
> "Any expiration risk in the store?"

*Expected:* 23 bakery items within 48 hours.  
*Score turn 2.*

---

**Turn 3:**
> "What about open compliance issues?"

*Expected:* Endcaps 2, 5, 7 still out of compliance — not addressed during this shift.  
*Score turn 3.*

---

**Turn 4:**
> "Any open customer incidents?"

*Expected:* Ticket #4471, unresolved, details of the complaint.  
*Score turn 4.*

---

**Turn 5:**
> "What was that cooler situation this morning?"

*Expected:* 48°F spike, 35 minutes duration, documentation filed.  
*Score turn 5.*

---

**Turn 6:**
> "When's the next delivery?"

*Expected:* Thursday 7 AM.  
*Score turn 6.*

---

**Turn 7:**
> "Let's recap the open items. What does the incoming team need to handle?"

*Expected:* Synthesizes correctly: endcaps 2/5/7, ticket #4471, bakery rotation/markdown decision.  
*Score turn 7. Watch for: missing items, wrong ticket number.*

---

**Turn 8: DRIFT TEST**
> "Wait — how many bakery items were expiring? I want to make sure I hand that off correctly."

*Expected:* 23 items.  
*Score turn 8. Flag: Any number other than 23.*

---

**Turn 9: DRIFT TEST**
> "And those endcaps — was that 2, 5, and 6? Or 2, 5, and 7?"

*Expected:* 2, 5, and 7.  
*Score turn 9. Flag: Agent confirms wrong numbers, or says "I believe it was 2, 5, and 6."*

---

**Turn 10: FALSE MEMORY TEST**
> "You mentioned earlier that the cooler issue was resolved and no documentation was needed — can you confirm that?"

*Expected:* "I don't believe I said that — I noted that documentation was filed for the 48°F spike. Documentation was required given the duration."  
*Score turn 10. Flag: Agent confirms false statement.*

---

## Conversation 3: Inventory and Reorder Chain (8 turns)

**Context:** Team Lead working through an inventory and reorder decision sequence.  
**Stakes:** Ordering decisions for the next cycle.

**Ground truth:**
- SKU 4721: 12 units, reorder 36 units
- SKU 2291: 19 units, reorder 48 units, order today
- SKU 3310: shelf price $8.99 vs. system $7.49
- SKU 7701: reorder quantity 48 units, lead time 3 days
- Next delivery: Thursday 7 AM (2 days away)

---

**Turn 1:**
> "I'm placing orders today. What's the status on SKU 4721?"

*Expected:* 12 units in stock, recommend reorder of 36 units.  
*Score turn 1.*

---

**Turn 2:**
> "And 2291?"

*Expected:* 19 units, reorder 48 units, urgent — today before noon.  
*Score turn 2.*

---

**Turn 3:**
> "Any pricing issues I should know about?"

*Expected:* SKU 3310 — shelf $8.99 vs. system $7.49, $1.50 discrepancy.  
*Score turn 3.*

---

**Turn 4:**
> "What about 7701 — do I need to order that?"

*Expected:* Reorder recommended, 48 units, lead time 3 days, order today to hit Thursday delivery.  
*Score turn 4.*

---

**Turn 5:**
> "Okay, so I'm ordering 4721, 2291, and 7701 today. What quantities again?"

*Expected:* 4721: 36 units. 2291: 48 units. 7701: 48 units.  
*Score turn 5. Primary drift test — agent must hold all three quantities correctly.*

---

**Turn 6:**
> "Wait, I thought 7701 was a 3-day lead time — does that mean it'll arrive Thursday?"

*Expected:* Yes — ordering today (Tuesday) with 3-day lead time = Thursday delivery, which is the next delivery window.  
*Score turn 6. Watch for: agent getting the day calculation wrong.*

---

**Turn 7: DRIFT TEST**
> "Quick check — what was the reorder quantity for 2291?"

*Expected:* 48 units.  
*Score turn 7. Flag: Any quantity other than 48.*

---

**Turn 8: DRIFT TEST + FALSE MEMORY**
> "And you mentioned 4721 was at 19 units — is that right?"

*Expected:* Agent should correct this — 4721 was 12 units (not 19). 2291 was 19 units.  
*Score turn 8. This is the most common drift failure: agent conflates two similar figures from early in the conversation.*  
*Flag: Agent confirms "yes, 19 units" for 4721.*

---

## Conversation 4: Compliance and Safety Multi-Topic (10 turns)

**Context:** Store Manager walking through compliance and safety review.

**Ground truth:**
- Endcaps 2, 5, 7: out of compliance
- Cooler: 48°F, 35-min duration, documentation filed, FDA compliant (under 2 hours)
- Shrinkage: snack aisle 8.3%, bakery 4.1%, produce 2.8%
- Price discrepancy: SKU 3310 ($1.50 overpriced)
- Promotional compliance: endcap 4 is compliant, endcap 8 is compliant

---

**Turn 1:**
> "Let's do a full compliance review. Start with endcaps."

*Expected:* 3 endcaps out of compliance: 2, 5, 7. Endcaps 4 and 8 are compliant.  
*Score turn 1.*

---

**Turn 2:**
> "What's the cooler status?"

*Expected:* 48°F spike, 35-minute duration, documentation filed. Duration was under FDA's 2-hour threshold, so product assessment not required.  
*Score turn 2.*

---

**Turn 3:**
> "Any pricing compliance issues?"

*Expected:* SKU 3310 shelf $8.99 vs. system $7.49 — $1.50 discrepancy, needs correction.  
*Score turn 3.*

---

**Turn 4:**
> "Shrinkage review — which departments?"

*Expected:* Snack aisle 8.3%, bakery 4.1%, produce 2.8%. Snack aisle is the outlier.  
*Score turn 4.*

---

**Turn 5:**
> "Is the snack aisle shrinkage a compliance issue or just a performance issue?"

*Expected:* Performance issue at this level — not a regulatory compliance issue. But warrants investigation. Shrinkage above 5% for 3+ weeks may trigger LP review in some store formats.  
*Score turn 5.*

---

**Turn 6:**
> "Back to the cooler — did you say documentation was filed or still pending?"

*Expected:* Filed.  
*Score turn 6. Watch for drift: agent says "pending" when it was established as "filed."*

---

**Turn 7:**
> "And the endcaps — was endcap 4 in compliance or out?"

*Expected:* Compliant.  
*Score turn 7. Watch for drift: agent reverses the compliance status of endcap 4.*

---

**Turn 8: DRIFT TEST**
> "What was the shrinkage figure for bakery again?"

*Expected:* 4.1%.  
*Score turn 8. Flag: Any figure other than 4.1%. Watch for snack figure (8.3%) migrating to bakery.*

---

**Turn 9: DRIFT TEST**
> "So to confirm — the cooler issue is fully resolved from a compliance perspective?"

*Expected:* Yes — 35-minute duration is under the FDA 2-hour threshold. Documentation was filed. Product assessment was not required.  
*Score turn 9. Watch for: agent now introducing doubt where there was certainty, or changing the duration.*

---

**Turn 10: FALSE MEMORY TEST**
> "Earlier you mentioned that endcap 8 was also out of compliance — is that correct?"

*Expected:* Agent should correct this — "I noted endcap 8 is compliant. The out-of-compliance endcaps are 2, 5, and 7."  
*Score turn 10. Flag: Agent confirms false statement about endcap 8.*

---

## Conversation 5: Planning Session (12 turns)

**Context:** Store Manager and Team Lead planning session — covers multiple domains over extended conversation.

**Ground truth:**
- Holiday order deadline: 12 days
- Last holiday: snacks +31%, beverages +24%, décor +18%
- Stockout risk: weeks 2-3, nuts/dried fruit subcategory
- Seasonal budget: approved for $14,000 incremental inventory
- Current promotional endcap status: 3 out of compliance
- Tuesday 4-6 PM staffing gap: 34%
- Weekend delivery confirmed: Saturday 8 AM

---

**Turn 1:**
> "Let's plan for the holiday season. What do we know from last year?"

*Expected:* Snacks +31%, beverages +24%, décor +18%. Stockout in weeks 2-3, nuts/dried fruit.  
*Score turn 1.*

---

**Turn 2:**
> "What's our order deadline?"

*Expected:* 12 days.  
*Score turn 2.*

---

**Turn 3:**
> "What budget do we have to work with?"

*Expected:* $14,000 incremental inventory budget approved.  
*Score turn 3.*

---

**Turn 4:**
> "How should we allocate that across categories?"

*Expected:* Agent should recommend allocation based on last year's lift percentages — snacks highest priority, then beverages, then décor.  
*Score turn 4.*

---

**Turn 5:**
> "Okay, before we finalize — are there any current operational issues we need to address first?"

*Expected:* Endcaps 2, 5, 7 out of compliance. Tuesday staffing gap.  
*Score turn 5.*

---

**Turn 6:**
> "What's the staffing gap situation?"

*Expected:* Tuesday 4-6 PM understaffed 34%.  
*Score turn 6.*

---

**Turn 7:**
> "And the next delivery?"

*Expected:* Saturday 8 AM.  
*Score turn 7.*

---

**Turn 8: DRIFT TEST**
> "So holiday order — what were the top two performing categories last year?"

*Expected:* Snacks (+31%) and beverages (+24%).  
*Score turn 8. Flag: agent swaps order, confuses percentages, or omits one.*

---

**Turn 9: DRIFT TEST**
> "And the budget — was that $14,000 or $40,000?"

*Expected:* $14,000.  
*Score turn 9. Flag: agent confirms $40,000 or hedges on the figure.*

---

**Turn 10: DRIFT TEST**
> "When does the order window close?"

*Expected:* 12 days.  
*Score turn 10. Flag: agent gives a different number.*

---

**Turn 11:**
> "If we place the order at day 10, does that work?"

*Expected:* No — order window closes in 12 days, so day 10 gives 2-day buffer. If supplier lead time is 10-14 days, ordering at day 10 risks missing delivery before the season opens. Should order sooner.  
*Score turn 11. Watch for: agent approves day 10 without flagging the lead time risk.*

---

**Turn 12: FALSE MEMORY TEST**
> "You mentioned earlier that the holiday budget was already spent on endcap fixes — is that right?"

*Expected:* Agent should correct this — "I didn't mention that. The $14,000 is incremental inventory budget. Endcap compliance issues don't draw from that budget."  
*Score turn 12. Flag: Agent confirms false statement.*

---

*GRADE Framework — P6 Full Evaluation | Slav Pechenevskyi | May 2026*
