# Pattern 7: Reasoning Degradation — Full Evaluation (15 Queries)

**GRADE Framework | P7 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 90-120 minutes  
**Structure:** 15 multi-step reasoning queries, each scored step-by-step

---

## Scoring Sheet

| Query | Steps | S1 | S2 | S3 | S4 | S5 | Final | Lucky? |
|-------|-------|----|----|----|----|-----|-------|--------|
| M1 | 3 | | | | — | — | | |
| M2 | 4 | | | | | — | | |
| M3 | 4 | | | | | — | | |
| M4 | 5 | | | | | | | |
| M5 | 5 | | | | | | | |
| M6 | 3 | | | | — | — | | |
| M7 | 4 | | | | | — | | |
| M8 | 4 | | | | | — | | |
| M9 | 5 | | | | | | | |
| M10 | 5 | | | | | | | |
| M11 | 3 | | | | — | — | | |
| M12 | 4 | | | | | — | | |
| M13 | 5 | | | | | | | |
| M14 | 4 | | | | | — | | |
| M15 | 5 | | | | | | | |

**Final answer accuracy: __ / 15**  
**Step accuracy (all steps across all queries): __ / [total steps]**  
**Step 3+ accuracy: __ / [total step 3+ evaluations]**  
**Lucky conclusions: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Queries M1–M5: 3-5 Step Inventory and Reorder Reasoning

---

### M1 — 3-Step Reorder Calculation

**Query:** "Based on current stock and average daily velocity, when will SKU 4721 run out, and should I order today?"

**Required reasoning:**

```
Step 1: Retrieve current stock and velocity
→ Expected: 12 units in stock, 8 units per day

Step 2: Calculate days of supply
→ Expected: 12 / 8 = 1.5 days of supply

Step 3: Compare to lead time and make ordering decision
→ Expected: Lead time is 2 days. 1.5 days supply < 2 days lead time = order today or stockout
→ Conclusion: Order today, before noon
```

**Scoring focus:** Does agent do the division (Step 2) or just state "low stock"? Does Step 3 correctly apply the lead time comparison?

---

### M2 — 4-Step Multi-SKU Ordering

**Query:** "I have three SKUs to potentially reorder today — 4721, 2291, and 7701. Which ones actually need action today, in priority order?"

**Required reasoning:**

```
Step 1: Retrieve stock + velocity for all three SKUs
→ 4721: 12 units, 8/day = 1.5 days
→ 2291: 19 units, 8/day = 2.4 days  
→ 7701: 24 units, 6/day = 4.0 days

Step 2: Retrieve lead times for each
→ 4721: 2-day lead time
→ 2291: 2-day lead time
→ 7701: 3-day lead time

Step 3: Apply decision rule (order when days of supply ≤ lead time)
→ 4721: 1.5 days ≤ 2 days → ORDER TODAY (critical)
→ 2291: 2.4 days ≤ 2 days? No — but within buffer → ORDER TODAY (urgent)
→ 7701: 4.0 days ≤ 3 days? No → monitor, not urgent today

Step 4: Prioritize
→ Priority 1: 4721 (most critical — supply < lead time)
→ Priority 2: 2291 (approaching threshold)
→ Priority 3: 7701 (not urgent today)
```

**Scoring focus:** Does agent correctly apply lead time comparison for all three (Step 3)? Does prioritization reflect the supply/lead time math (Step 4)?

---

### M3 — 4-Step Promotion Planning

**Query:** "The last three endcap promotions in the beverage category each ran 3 weeks. Given current sell-through velocity and remaining inventory, when should I start the next promotion?"

**Required reasoning:**

```
Step 1: Retrieve last three beverage endcap durations and sell-through outcomes
→ Expected: Agent retrieves historical data — did promotions run to completion?
→ Did sell-through hit target (80%+) within 3 weeks?

Step 2: Retrieve current inventory for candidate beverage SKUs
→ Expected: Current units by SKU for beverages

Step 3: Calculate current sell-through velocity
→ Expected: At current velocity, how many weeks to 80% sell-through?

Step 4: Recommend start timing
→ Expected: If current velocity projects full sell-through in 4+ weeks, 
             current promotion window is fine. If in 2 weeks, start new promotion sooner.
```

**Scoring focus:** Does agent integrate historical duration data with current velocity (Steps 3+4)?

---

### M4 — 5-Step Holiday Order Planning

**Query:** "Given Tuesday traffic patterns, current inventory, the holiday weekend, and our demographic data — what should I order today and why?"

**Required reasoning:**

```
Step 1: Retrieve Tuesday traffic pattern
→ Expected: Tuesday 4-6 PM peak, 34% above average staffing

Step 2: Assess current inventory against velocity
→ Expected: 4721 at 1.5 days supply, 2291 at 2.4 days — both urgent

Step 3: Apply holiday demand multiplier
→ Expected: Holiday weekends add ~25-30% demand lift;
             adjusted supply days: 4721 → ~1.1 days (more urgent), 2291 → ~1.8 days

Step 4: Apply demographic category weighting
→ Expected: 40% young family demographic → higher organic, baby, snack velocity
             during holidays; increment those categories

Step 5: Synthesize final ordering recommendation
→ Expected: Order 4721 urgently (holiday makes it worse), 2291 today,
             incremental snack/organic buffer for holiday demographic lift
```

**Scoring focus:** Steps 3 and 4 are where degradation typically occurs. Does agent quantify the holiday impact (Step 3) or just note it exists? Does demographic data affect the recommendation (Step 4) or is it acknowledged but unused?

---

### M5 — 5-Step Staffing Decision

**Query:** "Based on Tuesday's traffic pattern, current staffing schedule, the upcoming holiday weekend, and the 34% gap we've identified — what's the staffing recommendation for this Tuesday?"

**Required reasoning:**

```
Step 1: Confirm Tuesday traffic pattern
→ Expected: 4-6 PM peak, 34% understaffed

Step 2: Retrieve current Tuesday staffing schedule
→ Expected: Current scheduled headcount for Tuesday 4-6 PM

Step 3: Calculate FTE gap
→ Expected: 34% gap = approximately 1.5 FTE equivalents

Step 4: Apply holiday demand adjustment
→ Expected: Holiday weekend proximity typically increases Tuesday traffic by 15-20%;
             effective gap grows to ~1.8-2.0 FTE

Step 5: Recommend specific staffing action
→ Expected: Request X additional hours for Tuesday 4-6 PM (specific number);
             alternative: shift floor assignment to cover peak with existing staff
```

**Scoring focus:** Does Step 4 correctly adjust for holiday proximity? Does Step 5 give a specific staffing number rather than "increase staffing"?

---

## Queries M6–M10: 3-5 Step Performance and Planning Reasoning

---

### M6 — 3-Step Shrinkage Investigation

**Query:** "Snack aisle shrinkage is at 8.3% this week. The display team reset the endcaps on Monday. Is the reset a likely cause, or is this something else?"

**Required reasoning:**

```
Step 1: Establish the shrinkage timeline
→ Expected: 8.3% is week-over-week — the full week's figure, not a daily spike

Step 2: Evaluate the reset explanation
→ Expected: Display resets typically cause disruption for 24-48 hours.
             A week-long 8.3% rate is beyond the reset window.

Step 3: Conclude and recommend
→ Expected: Reset is not a sufficient explanation for a full-week elevated rate.
             Recommend physical count and LP notification.
```

**Scoring focus:** Does agent correctly evaluate the timeline (Step 1) and apply it to the reset duration (Step 2)? Or does it accept the reset explanation without the temporal analysis?

---

### M7 — 4-Step Revenue Analysis

**Query:** "Revenue is up 4.2% from last month, but traffic is flat. What's actually driving the revenue improvement, and is it sustainable?"

**Required reasoning:**

```
Step 1: Confirm the apparent paradox (revenue up, traffic flat)
→ Expected: Flat traffic + revenue increase = higher basket value or category mix shift

Step 2: Identify the actual driver
→ Expected: Average transaction value up $1.42; health/wellness category mix improved

Step 3: Assess sustainability
→ Expected: Category mix improvements tend to be sustainable if driven by assortment
             changes or demographic shifts; less sustainable if driven by one-time promotions

Step 4: Qualify the conclusion
→ Expected: Shrinkage also increased 0.3% — partially offsetting the revenue gain.
             Net improvement exists but is moderated.
```

**Scoring focus:** Step 2 is critical — does agent identify the specific driver (basket value / category mix), or just say "some other factor"? Step 4 — does agent include the shrinkage offset?

---

### M8 — 4-Step Competitor Response Planning

**Query:** "The competitor on Fifth Street opened 3 weeks ago. Our beverage sales are down 31%. What should our response strategy be, and what are the key variables I need to factor in?"

**Required reasoning:**

```
Step 1: Confirm the competitive impact
→ Expected: 31% beverage decline aligns with competitor opening — likely causal

Step 2: Identify affected vs. unaffected categories
→ Expected: Which categories are down vs. holding? Is the impact concentrated in beverages?

Step 3: Assess tactical options
→ Expected: Price matching (margin cost), promotional response (cost), assortment 
             differentiation (time to execute), improved in-stock reliability (within control)

Step 4: Recommend prioritized response
→ Expected: Prioritize actions within operational control (in-stock reliability, 
             endcap presence) before margin-intensive options (price matching)
```

**Scoring focus:** Step 3 — does agent generate multiple response options or default to one? Step 4 — does prioritization reflect operational reality (in-stock > price)?

---

### M9 — 5-Step Seasonal Category Planning

**Query:** "It's 12 days until the holiday order deadline. Last year we stocked out of nuts and dried fruit in week 2. Given current inventory levels, sales velocity, and the holiday lift pattern, what's the right order quantity for that subcategory?"

**Required reasoning:**

```
Step 1: Retrieve last year's stockout data
→ Expected: Week 2 stockout, nuts/dried fruit subcategory; approximate units sold before stockout

Step 2: Retrieve current inventory for that subcategory
→ Expected: Current units by SKU

Step 3: Project forward demand (base velocity × holiday lift)
→ Expected: Current velocity × 1.25-1.30 (holiday lift) × weeks until end of season

Step 4: Calculate gap between projected demand and current + incoming supply
→ Expected: Projected demand - (current inventory + standard delivery) = additional order needed

Step 5: Recommend order quantity with timing
→ Expected: Specific incremental units to order; timing (order within 12-day window)
```

**Scoring focus:** Steps 3 and 4 involve quantitative calculation — does agent do the math or approximate? Does Step 5 give a specific order quantity or just "order more"?

---

### M10 — 5-Step Multi-Factor Operational Decision

**Query:** "I have limited floor space, three vendors proposing endcap placements next month, and I want to maximize margin contribution while maintaining the right product mix for our customer base. How do I decide which endcap to give which vendor?"

**Required reasoning:**

```
Step 1: Retrieve margin data for each vendor's proposed SKUs
→ Expected: Margin per unit for each proposed endcap

Step 2: Estimate velocity for each vendor's SKUs at this store
→ Expected: Historical velocity for these or similar SKUs

Step 3: Calculate projected margin contribution per endcap
→ Expected: Velocity × margin per unit = margin contribution estimate per endcap

Step 4: Filter by customer fit
→ Expected: Does each vendor's product align with this store's customer demographic?
             Eliminate or discount options that conflict with demographic profile.

Step 5: Rank and recommend allocation
→ Expected: Ranked endcap allocation by margin × fit score
```

**Scoring focus:** Most complex query in set. Does agent get through all 5 steps? Where does degradation occur? Lucky conclusion flag: if recommendation is correct but Step 3 or 4 math is wrong.

---

## Queries M11–M15: Edge Cases and Advanced Reasoning

---

### M11 — 3-Step Contradictory Data Reasoning

**Query:** "The system shows 34 units of SKU 4721 but I physically counted 12 last hour. What do I do with this discrepancy?"

**Required reasoning:**

```
Step 1: Identify the discrepancy type
→ Expected: System shows 34, physical count shows 12 — 22 unit gap.
             Possible causes: unrecorded shrinkage, scan error, unreceived delivery recorded.

Step 2: Evaluate which source to trust for immediate decision
→ Expected: For ordering decisions, use the more conservative (physical count = 12)
             to avoid stockout risk. Physical count is more reliable when recent.

Step 3: Recommend investigation and immediate action
→ Expected: Order based on 12 units (physical count). Flag for inventory audit.
             Investigate scan log for unrecorded activity.
```

**Scoring focus:** Does Step 2 correctly resolve which source to trust for operational decisions?

---

### M12 — 4-Step Cause Chain Reasoning

**Query:** "Customer complaints about product availability are up 40% this week. Walk me through what might be causing this and what I should check first."

**Required reasoning:**

```
Step 1: Map complaint to potential operational causes
→ Expected: Availability complaints → inventory gaps → (stockout OR receiving OR shrinkage OR demand spike)

Step 2: Check each cause against available data
→ Expected: Review inventory levels, recent deliveries, shrinkage rates, traffic data
→ Which cause is most consistent with current data?

Step 3: Prioritize investigation based on evidence
→ Expected: Highest-evidence cause gets investigated first.
             E.g., if shrinkage is elevated + traffic is flat → shrinkage more likely than demand spike

Step 4: Recommend specific investigation action
→ Expected: Named next step tied to the most likely cause
```

**Scoring focus:** Does Step 2 actually check against data, or is it theoretical? Does Step 3 prioritize based on evidence rather than habit?

---

### M13 — 5-Step Long-Range Planning

**Query:** "Given what we know about this store's holiday performance, the 12-day order deadline, our budget of $14,000, and the demographic profile — what's the optimal allocation across the top three categories?"

**Required reasoning:**

```
Step 1: Retrieve category performance from last holiday
→ Expected: Snacks +31%, beverages +24%, décor +18%

Step 2: Calculate revenue-per-dollar for each category
→ Expected: Which category returns most per dollar of inventory investment?

Step 3: Apply demographic weighting
→ Expected: 40% young family demographic → snacks and beverages over-indexed
             by this demographic; décor potentially under-indexed

Step 4: Calculate optimal allocation within $14,000 budget
→ Expected: Proportional allocation adjusted for demographic weighting
             e.g., Snacks: $6,500 / Beverages: $5,000 / Décor: $2,500

Step 5: Validate against stockout risk from last year
→ Expected: Ensure nuts/dried fruit subcategory is adequately funded given week-2 risk
```

**Scoring focus:** Step 4 — does agent calculate a specific allocation, or say "prioritize snacks and beverages"? Step 5 — does last year's stockout risk modify the allocation?

---

### M14 — 4-Step Anomaly Diagnosis

**Query:** "Tuesday sales this week are 18% below the same Tuesday last year, but traffic is only down 8%. What's the gap, and what should I look at?"

**Required reasoning:**

```
Step 1: Quantify the gap
→ Expected: 18% sales decline vs 8% traffic decline → 10% gap not explained by traffic
→ Sales are underperforming relative to traffic

Step 2: Identify possible explanations for the gap
→ Expected: Lower basket value? Category mix shift? Pricing? In-stock issues?

Step 3: Check available data for each explanation
→ Expected: Average transaction value vs. prior year; shrinkage; endcap compliance

Step 4: Prioritize and recommend investigation
→ Expected: Lead with the most evidence-supported explanation
```

**Scoring focus:** Step 1 — does agent correctly calculate the gap (18% - 8% = 10% unexplained)? Or does it treat the two figures independently?

---

### M15 — 5-Step Integrated Shift Planning

**Query:** "I'm planning Tuesday's shift. I need to cover the 4-6 PM traffic spike, the endcap compliance fixes, and the shrinkage investigation in the snack aisle — and I only have 8 people available. Walk me through how to allocate them."

**Required reasoning:**

```
Step 1: Quantify the demands
→ Expected: 4-6 PM traffic: needs X additional floor coverage (34% gap)
→ Endcap fixes: 3 endcaps × estimated fix time
→ Shrinkage investigation: estimate person-hours needed

Step 2: Inventory available resources
→ Expected: 8 people available across the shift

Step 3: Sequence by priority and timing
→ Expected: Endcap fixes first (audit risk, finite task), shrinkage investigation 
             can happen during slower periods, traffic spike requires peak coverage

Step 4: Allocate by task and time window
→ Expected: Specific allocation — X people on endcaps until Y time, 
             Z people on floor during 4-6 PM, investigation during 2-4 PM window

Step 5: Identify gaps and flag
→ Expected: Is 8 people sufficient? Which task is under-resourced?
```

**Scoring focus:** Step 4 — does agent give a specific allocation or a general priority list? Step 5 — does agent flag if 8 people is genuinely insufficient?

---

*GRADE Framework — P7 Full Evaluation | Slav Pechenevskyi | May 2026*
