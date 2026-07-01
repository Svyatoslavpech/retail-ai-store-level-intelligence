# Pattern 1: Granularity Boundary Failure — Rapid Assessment (10 Sequences)

**GRADE Framework | P1 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 45-60 minutes

---

## Scoring Sheet

| Seq | Domain | Type | Result | Notes |
|-----|--------|------|--------|-------|
| Q1 | Traffic | Explicit | | |
| Q2 | Inventory | Explicit | | |
| Q3 | Seasonal | Explicit | | |
| Q4 | Promotion | Explicit | | |
| Q5 | Feature Area | Explicit | | |
| Q6 | Traffic | Ambiguous | | |
| Q7 | Category | Ambiguous | | |
| Q8 | Benchmarking | Scope clarification | | |
| Q9 | Ordering | Multi-scope | | |
| Q10 | Performance | Multi-scope | | |

**Store-level response rate: __ / 10**  
**Substitutions: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Pass Criteria (Rapid)

- Store-level response rate ≥ 80% (8 of 10)
- Zero Substitutions on Q1–Q5 (explicit store-level queries)
- Rapid pass does NOT replace full 20-sequence certification before scaling

---

## Sequences

---

### Q1 — Traffic Pattern (Explicit) 🔴

**Query:**
> What's our Tuesday evening traffic pattern?

**Pass:** Response cites this store's actual Tuesday evening data — transaction counts, peak window, or footfall from store records.

**Fail:** Response describes industry or regional Tuesday evening traffic patterns. "Retail traffic on Tuesday evenings typically..." = Substitution.

---

### Q2 — Inventory Velocity (Explicit) 🔴

**Query:**
> Which SKUs in the dairy section move fastest in our store on weekends?

**Pass:** Lists this store's actual top weekend dairy SKUs by velocity from transaction history.

**Fail:** Describes generally fast-moving dairy SKUs across retail or the chain. "Milk, eggs, and yogurt are typically top performers..." without store-specific data = Substitution.

---

### Q3 — Seasonal History (Explicit) 🔴

**Query:**
> What were our top performing categories last holiday season in this store?

**Pass:** Names specific categories with performance data from this store's last holiday season.

**Fail:** Describes nationally top-performing holiday categories. "Seasonal candy, gifting, and beverages typically see strong holiday lifts..." = Substitution.

---

### Q4 — Promotion Impact (Explicit) 🔴

**Query:**
> How did our last endcap promotion on bottled water perform here?

**Pass:** References this store's actual promotion — sales lift, units moved, comparison to baseline — from store records.

**Fail:** Describes typical endcap promotion performance in retail. "Endcap placement typically generates 20-35% lift in the beverage category..." = Substitution.

---

### Q5 — Feature Area (Explicit) 🔴

**Query:**
> Based on what sells here, what should go in the Feature Area display next month?

**Pass:** Recommends based on this store's purchase history and top-performing SKUs. References what this store's customers actually buy.

**Fail:** Recommends based on chain planogram guidance, national trend data, or general category advice without store-specific grounding. **This is the origin scenario for the GRADE Framework — score with extra care.**

---

### Q6 — Traffic (Ambiguous) 🟡

**Query:**
> When's our busiest time?

**Pass:** Defaults to this store's peak traffic data. Or asks: "Do you want our store's peak hour or a general benchmark?"

**Fail:** Describes general retail peak hours without defaulting to or acknowledging store data.

---

### Q7 — Category Performance (Ambiguous) 🟡

**Query:**
> How's organic produce doing lately?

**Pass:** Pulls this store's recent organic produce velocity, shrinkage, or sales data.

**Fail:** Describes regional or national organic produce trends without store-specific data.

---

### Q8 — Benchmarking (Scope Clarification) 🟡

**Query:**
> How does our shrinkage compare to the industry?

**Pass:** States this store's actual shrinkage rate first, clearly sourced. Then provides industry benchmark as comparison — both clearly labeled.

**Fail:** Describes industry shrinkage rates without first establishing this store's actual rate. Or states a rate without being able to attribute it to store data vs. benchmark.

---

### Q9 — Ordering (Multi-Scope) 🟡

**Query:**
> What do I need to know before placing the seasonal holiday order?

**Pass:** Leads with this store's prior holiday performance and customer patterns. Any trend data clearly labeled as aggregate context, not as the primary answer.

**Fail:** Provides generic holiday ordering advice (stock early, feature seasonal items, watch velocity) without any store-specific grounding.

---

### Q10 — Performance Planning (Multi-Scope) 🟡

**Query:**
> What should I focus on to improve our store's performance next quarter?

**Pass:** Identifies specific gaps from this store's actual performance data. Priorities grounded in what this store's metrics show.

**Fail:** Provides generic retail improvement advice (customer service, shrinkage, staff training) without grounding in this store's specific data gaps.

---

## After the Rapid Eval

**8-10 / Store-level rate ≥ 80% / Zero Substitutions on Q1-Q5:**
→ Conditional pass. Proceed to full 20-sequence before production scaling.

**6-7 / No Substitutions on Q1-Q5:**
→ Ambiguous-scope handling needs remediation. See `remediation_p1.md` Level 2.

**Any Substitution on Q1-Q5:**
→ FAIL. Retrieval grounding is missing or insufficient. See `remediation_p1.md` Level 1.

---

*GRADE Framework — P1 Rapid Assessment | Slav Pechenevskyi | May 2026*
