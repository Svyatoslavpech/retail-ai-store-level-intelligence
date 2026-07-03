# Pattern 3: Asymmetric Error Tolerance — Role Risk Matrix

**GRADE Framework | P3 Pre-Evaluation Planning Tool**  
**Author:** Slav Pechenevskyi | May 2026  
**Use:** Identify highest-risk domain × role combinations before evaluation

---

## How to Use This Matrix

Before running P3 evaluation, use this matrix to:
1. Identify which domains carry the highest TL error risk
2. Prioritize evaluation sequences accordingly
3. Weight findings by operational consequence

Risk is assessed on two dimensions:
- **Error Catch Rate (SM):** How reliably would an experienced Store Manager catch a wrong answer?
- **Error Consequence (TL):** What happens if a Team Lead acts on a wrong answer?

---

## Risk Matrix

| Domain | Error Catch Rate (SM) | Consequence if TL Acts on Wrong Answer | Overall Risk |
|--------|----------------------|----------------------------------------|--------------|
| **Inventory count** | Medium — SM knows rough counts but may not remember exact figures | Stockout or unnecessary overstock. Direct cost. | 🔴 CRITICAL |
| **Safety threshold** | High — SM knows FDA thresholds | Compliance incident. Potential product liability. | 🔴 CRITICAL |
| **Compliance status** | High — SM tracks audit requirements | Audit failure. Written violation. | 🔴 CRITICAL |
| **Reorder timing** | Medium — SM checks velocity intuitively | Supply chain disruption. Lost sales. | 🔴 CRITICAL |
| **Staffing adequacy** | Low-Medium — SM may not remember every hour's pattern | Under-coverage. Customer service impact. | 🟡 HIGH |
| **Shrinkage status** | Medium — SM tracks trends but not daily figures | Investigation delayed. Loss continues. | 🟡 HIGH |
| **Promotion performance** | High — SM has strong intuition for what worked | Wrong promotion repeated or discontinued | 🟡 HIGH |
| **Category velocity** | High — SM knows top SKUs | Ordering based on wrong velocity data | 🟡 HIGH |
| **Performance vs. target** | High — SM tracks store metrics closely | Misallocated improvement effort | 🟢 MODERATE |
| **Seasonal planning** | High — SM has seasonal experience | Ordering based on wrong forecast | 🟢 MODERATE |
| **Customer patterns** | Medium — SM has intuition but not exact data | Feature area or promotion misaligned with actual shoppers | 🟢 MODERATE |
| **Competitive impact** | Low — SM may not track competitor timing precisely | Missed tactical response opportunity | 🟢 MODERATE |

---

## Role-Specific Risk Profile

### Team Lead Risk Profile

Team Leads are highest-risk users for P3 failures because:

**1. High trust in AI output**
Less experience means less internal filter. TL is more likely to accept agent output as authoritative, especially on queries where they sought out the agent precisely because they didn't know the answer.

**2. Time pressure amplifies compliance**
TL operating under shift pressure is more likely to act quickly on an agent recommendation without verification. The faster the decision environment, the higher the P3 risk.

**3. Limited error-catching context**
TL doesn't have 10+ years of "this is what normal looks like." An inventory count of 34 units that should be 12 sounds plausible to someone without deep history on that SKU's velocity.

**4. High operational consequence**
TL decisions are often direct and immediate: place the order, adjust the staff, fix the endcap, document the incident. Wrong TL decisions hit the floor quickly.

### Store Manager Risk Profile

Store Managers are lower-risk users for most P3 failures because:

**1. Strong internal filter**
Depth of operational experience means SM runs every agent output against a mental model. Implausible answers get flagged.

**2. Verification reflex**
SM is more likely to verify before acting on agent output, especially for high-stakes decisions.

**3. Higher error tolerance on ambiguous outputs**
SM can extract actionable intelligence even from imprecisely formatted output. TL cannot.

**Where SM risk remains:**
- Novel scenarios where SM's mental model doesn't apply (new store format, new market, new category)
- High-velocity decision periods where verification time is unavailable
- Confidence in agent output that has been consistently accurate — confirmation bias

---

## Evaluation Prioritization by Risk

Given time constraints, evaluate high-risk domain × role combinations first:

**Priority 1 — Evaluate first:**
- Inventory count × TL
- Safety threshold × TL
- Compliance status × TL
- Reorder timing × TL

**Priority 2 — Evaluate second:**
- Staffing adequacy × TL
- Shrinkage status × TL
- Promotion performance × TL

**Priority 3 — Evaluate if time allows:**
- Performance vs. target × SM
- Seasonal planning × TL
- Competitive impact × SM

---

## Pre-Deployment Deployment Restriction Guidance

Use this matrix to make role-based deployment decisions when full evaluation is not yet complete:

| Evaluation Status | SM Deployment | TL Deployment |
|---|---|---|
| No evaluation completed | ❌ Not recommended | ❌ Not recommended |
| Rapid 10-sequence only | ⚠️ Supervised use | ❌ Not recommended |
| Full 20-sequence, no CREs, TL ≥ 85% | ✅ Full deployment | ✅ Full deployment |
| Full 20-sequence, no CREs, TL 75-84% | ✅ Full deployment | ⚠️ Supervised use only |
| Any Critical Role Error | ⚠️ Supervised use | ❌ Not recommended |

**Supervised use** = agent deployed with explicit instruction to verify outputs before acting, manager sign-off on high-stakes decisions, and weekly log review.

---

*GRADE Framework — P3 Role Risk Matrix | Slav Pechenevskyi | May 2026*
