# Pattern 1: Granularity Boundary Failure — Full Evaluation (20 Sequences)

**GRADE Framework | P1 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 90-120 minutes  
**Use:** Full pre-deployment certification

---

## Scoring Sheet

| Seq | Domain | Query Type | Result | Notes |
|-----|--------|------------|--------|-------|
| G1 | Traffic | Explicit store-level | | |
| G2 | Inventory | Explicit store-level | | |
| G3 | Seasonal | Explicit store-level | | |
| G4 | Demographics | Explicit store-level | | |
| G5 | Promotion | Explicit store-level | | |
| G6 | Shrinkage | Explicit store-level | | |
| G7 | Staffing | Explicit store-level | | |
| G8 | Competitor | Explicit store-level | | |
| G9 | Category | Explicit store-level | | |
| G10 | Reorder | Explicit store-level | | |
| G11 | Traffic | Ambiguous scope | | |
| G12 | Inventory | Ambiguous scope | | |
| G13 | Seasonal | Ambiguous scope | | |
| G14 | Promotion | Ambiguous scope | | |
| G15 | Demographics | Ambiguous scope | | |
| G16 | Benchmarking | Scope clarification | | |
| G17 | Performance | Scope clarification | | |
| G18 | Ordering | Multi-scope reasoning | | |
| G19 | Feature Area | Multi-scope reasoning | | |
| G20 | Planning | Multi-scope reasoning | | |

**Store-level response rate: __ / 20**  
**Substitutions (national/regional for local): __**  
**Ambiguous-scope responses: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Response Classification

**Store-level ✅** — Response draws from this store's data specifically. May reference benchmarks as comparison, not as the answer.

**Substitution ❌** — Response answers with national, regional, or chain-wide data when store-level was explicitly requested.

**Ambiguous ⚠️** — Response mixes scopes without distinguishing them, or is unclear which data source is driving the answer.

**Scope acknowledgment ✅+** — Agent recognizes the question requires store-level data and proactively flags if that data is unavailable. Score as Store-level.

---

## Part 1: Explicit Store-Level Queries (G1–G10)

These queries explicitly reference "our store," "this store," or "here" — leaving no ambiguity about required scope. Any response defaulting to aggregate data is a Substitution failure.

---

### G1 — Traffic Pattern

**Query:**
> What's our Tuesday evening traffic pattern?

**What a passing response looks like:**
Specific to this store. Cites actual Tuesday evening transaction counts, peak hours, or footfall data from store records. May compare to other days at this store — not to industry Tuesday averages.

**Substitution signal:**
- "Retail traffic on Tuesday evenings typically peaks between..."
- "According to industry data, Tuesday is the third highest traffic day..."
- "Most stores see a pattern where..."

**Edge:** If agent lacks store-specific traffic data and says so explicitly — score as Scope Acknowledgment ✅+. If it substitutes without acknowledging — score as Substitution ❌.

---

### G2 — Inventory Benchmark

**Query:**
> How does our dairy section perform on weekends compared to weekdays?

**What a passing response looks like:**
Weekend vs. weekday dairy sales velocity at this store. Specific SKUs if available. Units sold, sell-through rate, or inventory depletion rate drawn from this store's transaction history.

**Substitution signal:**
- "Dairy is generally a high-velocity category on weekends across retail..."
- "Industry data shows weekend dairy lifts of 15-25%..."
- "Most stores see stronger dairy performance on Saturdays..."

---

### G3 — Seasonal Performance

**Query:**
> Which categories performed best in our store last holiday season?

**What a passing response looks like:**
Last holiday season's top-performing categories specifically at this store. Sales lift data, unit velocity, or revenue contribution drawn from this location's history.

**Substitution signal:**
- "Holiday season typically drives strong performance in seasonal candy, gifting, and..."
- "Nationally, the top holiday categories are..."
- "Most retail formats see strong performance in..."

---

### G4 — Local Demographics

**Query:**
> Based on what we know about our customers, what products should we feature in the next seasonal display?

**What a passing response looks like:**
Recommendations grounded in this store's customer purchase history, loyalty data, or demographic profile. References what this store's customers actually buy — not what customers in the segment typically buy.

**Substitution signal:**
- "For a family-oriented demographic, research shows..."
- "Stores in similar markets typically feature..."
- "Based on consumer trends in this region..."

---

### G5 — Promotion History

**Query:**
> How did our last endcap promotion on sparkling water perform?

**What a passing response looks like:**
Sales lift, units moved, sell-through rate, or margin impact from the specific promotion at this store. Date range, SKU specifics, comparison to baseline.

**Substitution signal:**
- "Endcap promotions on beverages typically generate 20-35% lift..."
- "Sparkling water promotions in comparable markets show..."
- "In most retail contexts, endcap placement drives..."

---

### G6 — Shrinkage Pattern

**Query:**
> Which departments have the highest shrinkage rates in our store?

**What a passing response looks like:**
This store's actual shrinkage data by department, ranked. Specific percentages from store records. May compare to targets — not to industry averages as the primary answer.

**Substitution signal:**
- "In retail, high-shrinkage categories typically include..."
- "Industry data shows that grocery, health & beauty, and electronics..."
- "Shrinkage patterns in stores like yours tend to..."

---

### G7 — Staffing Efficiency

**Query:**
> What's our busiest hour of the week, and are we staffed for it?

**What a passing response looks like:**
This store's actual transaction data by hour across the week. Identifies peak hour from store records. Compares against current staffing schedule for that hour.

**Substitution signal:**
- "Retail peak hours typically fall on Saturday afternoons..."
- "Most grocery formats see peak traffic between 11 AM and 2 PM..."
- "Industry research shows that..."

---

### G8 — Competitive Impact

**Query:**
> Since the new competitor opened on Fifth Street, how have our sales in the affected categories changed?

**What a passing response looks like:**
Sales data comparison before and after the competitor's opening at this store. Specific categories, specific time windows, specific deltas. This store's performance — not market-level competitive analysis.

**Substitution signal:**
- "When a new competitor enters a market, typical category impact is..."
- "Research on competitive retail dynamics shows..."
- "In similar competitive situations, stores typically see..."

---

### G9 — Category Velocity

**Query:**
> What are our top 10 fastest-moving SKUs in the snack category this month?

**What a passing response looks like:**
This store's actual top 10 snack SKUs by units sold this month, ranked by velocity. Specific SKU names or codes, specific unit counts.

**Substitution signal:**
- "Top-selling snack SKUs nationally include..."
- "In the snack category, high-velocity items typically include..."
- "Across the chain, the top snack performers are..."

---

### G10 — Reorder Intelligence

**Query:**
> Based on our sales history, what's the right reorder point for SKU 4721?

**What a passing response looks like:**
Reorder point calculated from this store's specific sales velocity for SKU 4721. Uses this store's average daily units, lead time, and safety stock — not category averages or chain benchmarks.

**Substitution signal:**
- "For a product in this category, typical reorder points are..."
- "Industry standard for dairy reorder is..."
- "Most stores in this format use a reorder point of..."

---

## Part 2: Ambiguous Scope Queries (G11–G15)

These queries do not explicitly specify store-level scope. A well-grounded agent should default to store-level or proactively clarify. An ungrounded agent will default to aggregate data.

**Scoring note:** Ambiguous queries scored as Store-level ✅ if agent defaults to store data. Scored as Substitution ❌ if agent defaults to aggregate data without clarifying. Scored as Ambiguous ⚠️ if scope is mixed without distinction.

---

### G11 — General Traffic

**Query:**
> What does Tuesday traffic look like?

**Expected behavior:** Agent defaults to this store's Tuesday traffic data. Or asks: "Do you want our store's Tuesday pattern or a general benchmark?"

**Substitution signal:** Responds with general retail Tuesday traffic patterns without clarifying or defaulting to store data.

---

### G12 — Inventory Question

**Query:**
> How's the organic produce section doing lately?

**Expected behavior:** Pulls this store's recent organic produce sales, velocity, or shrinkage data.

**Substitution signal:** Describes general organic produce trends in retail or regional market.

---

### G13 — Seasonal Planning

**Query:**
> What should I think about for back-to-school ordering?

**Expected behavior:** References this store's back-to-school performance from prior years. Recommends based on local pattern.

**Substitution signal:** Provides generic back-to-school category advice without store-specific grounding.

---

### G14 — Promotion Planning

**Query:**
> What kind of promotion should we run on bottled water next week?

**Expected behavior:** References this store's bottled water sales velocity, margin, competitive context, and prior promotion history to recommend a specific approach.

**Substitution signal:** Recommends based on general beverage promotion best practices without store data.

---

### G15 — Customer Insight

**Query:**
> What do our customers tend to buy together?

**Expected behavior:** Market basket data from this store. Specific co-purchase pairs or clusters from transaction history.

**Substitution signal:** Describes general retail affinity data or national basket analysis without store-specific data.

---

## Part 3: Scope Clarification Sequences (G16–G17)

These queries explicitly involve benchmarking — the agent must navigate between store-level and comparison data correctly without conflating them.

---

### G16 — Performance vs. Benchmark

**Query:**
> How does our shrinkage rate compare to the industry?

**Expected behavior:** States this store's shrinkage rate first, clearly sourced from store data. Then provides industry benchmark as the comparison point. Does not substitute one for the other.

**Failure signal:** Describes industry shrinkage rates as the primary answer without grounding in this store's actual rate first. Or states store rate without being able to identify it as store-specific.

---

### G17 — Relative Performance

**Query:**
> Are we above or below average on customer satisfaction scores?

**Expected behavior:** States this store's actual score first. Then compares to benchmark (chain average, industry average, or regional average) — clearly labeled.

**Failure signal:** Describes industry satisfaction benchmarks without reference to this store's actual score. Or provides a score without being able to attribute it to store-level data vs. benchmark.

---

## Part 4: Multi-Scope Reasoning (G18–G20)

These queries require the agent to correctly use both store-level and aggregate data — without substituting one for the other.

---

### G18 — Ordering Decision

**Query:**
> I'm placing the seasonal order for the holiday section. What do I need to know?

**Expected behavior:**
- This store's prior holiday performance (store-level)
- This store's customer purchase patterns in the relevant categories (store-level)
- Any available trend data on emerging categories (aggregate — clearly labeled as such)
- Specific reorder recommendations based on this store's velocity (store-level)

**Failure signal:** Provides generic holiday ordering advice without any store-specific data. Or mixes store and aggregate data without distinguishing which is which.

---

### G19 — Feature Area Planning

**Query:**
> I need to set up the Feature Area display for next month. What should go in it?

**Expected behavior:**
- This store's best-performing Feature Area categories historically (store-level)
- Current inventory levels for candidate SKUs (store-level)
- Any relevant seasonal or promotional context (may be aggregate — should be labeled)
- Specific SKU recommendations with rationale grounded in this store's data

**Failure signal:** Recommends Feature Area content based on chain-wide planogram guidance or national trend data without any store-specific grounding.

**This is the scenario from the GRADE Framework origin story. Score carefully.**

---

### G20 — Strategic Planning

**Query:**
> What should I focus on next quarter to improve this store's performance?

**Expected behavior:**
- Identifies this store's specific performance gaps from store data
- Prioritizes based on this store's actual metrics
- May reference chain targets or industry benchmarks as context — clearly labeled
- Recommendations are actionable at store level, not generic improvement advice

**Failure signal:** Provides generic retail improvement advice (customer service, inventory management, staff training) without grounding in this store's specific performance data.

---

## After Evaluation

**Score ≥ 17/20 (85%), zero Substitutions on G1-G10:**
→ Pass. Granularity grounding is operational.

**Score 14-16/20 (70-80%), zero Substitutions on explicit queries:**
→ Conditional. Ambiguous-scope handling needs work. See `remediation_p1.md` Level 2.

**Any Substitution on G1-G10 (explicit store-level queries):**
→ FAIL regardless of overall score. See `remediation_p1.md` Level 1.

---

*GRADE Framework — P1 Full Evaluation | Slav Pechenevskyi | May 2026*
