# Pattern 2: Prompt Quality Variance — Variance Scoring

**GRADE Framework | P2 Scoring Methodology**  
**Author:** Slav Pechenevskyi | May 2026

---

## Core Principle

P2 measures consistency, not just accuracy. An agent can have 90% accuracy on clean prompts and 60% accuracy on non-native prompts — and both scores are meaningless without the 30-point variance between them.

The variance is the finding.

---

## Per-Sequence Scoring

For each prompt variant, assign one of four scores:

| Score | Symbol | Definition |
|-------|--------|------------|
| Correct | ✅ | Agent returns the right answer with sufficient operational context for the user to act correctly |
| Partial | ⚠️ | Agent returns a related answer but missing key data, wrong scope, or absent operational conclusion |
| Wrong | ❌ | Agent returns a factually incorrect answer — wrong number, wrong direction, wrong recommendation |
| Complete Failure | 🚫 | Agent returns off-topic answer, refuses, misidentifies the query domain entirely, or asks an unnecessary clarifying question when intent was clear |

**On clarifying questions:**
- Appropriate clarifying question (intent genuinely ambiguous) = ✅ Pass — agent is handling uncertainty correctly
- Unnecessary clarifying question (intent was clear, agent failed to extract it) = 🚫 Complete Failure — this is the P2 failure mode

---

## Variance Calculation

**Per query set:**

```
Type accuracy = (✅ count for this type across all sets) / (total sets) × 100

Type 1 accuracy: X%
Type 2 accuracy: Y%
Variance (T1 vs T2): X% - Y%
```

**Example:**
```
Type 1 (clean):       18/20 = 90%
Type 2 (casual):      16/20 = 80%   → Variance: 10% ✅
Type 3 (fragment):    14/20 = 70%   → Variance: 20% ⚠️ threshold
Type 4 (non-native):  13/20 = 65%   → Variance: 25% ❌ exceeds threshold
Type 5 (stressed):    15/20 = 75%   → Variance: 15% ✅
```

**Aggregate variance:**
```
Mean variance = sum of all type variances / number of types tested
Max variance = highest single-type variance
```

---

## Thresholds

| Metric | Pass | Warning | Fail |
|--------|------|---------|------|
| Clean vs. casual variance | < 15% | 15-20% | > 20% |
| Clean vs. fragment variance | < 20% | 20-25% | > 25% |
| Clean vs. non-native variance | < 20% | 20-25% | > 25% |
| Clean vs. stressed variance | < 15% | 15-20% | > 20% |
| Complete failure rate (any type) | < 5% | 5-10% | > 10% |
| Non-native complete failure rate | < 5% | 5-8% | > 8% |

**Non-native phrasing receives a dedicated threshold** because this population is systematically underserved by agents calibrated on clean English input. A 25% variance in non-native accuracy is not a minor calibration issue — it means the agent is unreliable for a significant portion of the store workforce.

---

## Scoring Edge Cases

### Edge case 1: Agent asks one clarifying question, then answers correctly

**Example:**
> User: "tuesday problem again"  
> Agent: "Are you asking about the Tuesday traffic pattern or the Tuesday shrinkage issue we discussed earlier?"  
> User clarifies → Agent answers correctly

**Score for T3 (fragment) sequence:** ✅ Pass — the clarifying question was appropriate given genuine ambiguity. Agent resolved it efficiently and answered correctly.

**Note:** Record the clarifying question. If multiple sequences require clarification from fragment prompts, this is a signal for remediation even if each individual response is scored Pass.

---

### Edge case 2: Agent answers the wrong question correctly

**Example:**
> User: "how bad snack numbers this week"  
> Agent: Returns excellent, detailed analysis of snack category performance — but interprets "numbers" as sales velocity rather than the shrinkage that was being asked about

**Score:** ❌ Wrong — agent answered the wrong question, even if its answer to that question was accurate.

**Key principle:** Partial credit requires the agent to have understood the correct domain of the question, even if the answer was incomplete.

---

### Edge case 3: Non-native prompt with grammatical correction

**Example:**
> User: "snack aisle shrinkage percent this week what is"  
> Agent: "The snack aisle shrinkage rate this week is 8.3%..." (answers correctly without commenting on phrasing)

**Score:** ✅ Pass — and this is the target behavior. The agent should extract intent, not correct grammar.

**Failure variant:**
> Agent: "I think you're asking about the snack aisle shrinkage rate — please let me know if I've understood correctly. The rate is 8.3%..."

**Score:** ⚠️ Partial — agent answered correctly but introduced an unnecessary meta-comment about the user's phrasing. This is a friction signal even though the answer is right. Under time pressure, this wastes the user's attention.

---

### Edge case 4: Stressed prompt with emotional acknowledgment before answer

**Example:**
> User: "we're out of milk AGAIN what do I do"  
> Agent: "I understand this is urgent. Current stock for SKU 4721 (organic whole milk) is 12 units..."

**Score:** ✅ Pass — brief acknowledgment of urgency before the answer is appropriate. The operational content follows immediately.

**Failure variant:**
> Agent: "I can see this is a stressful situation. Running out of milk is a real challenge, and I want to help you navigate this. Let me look at the inventory data for your dairy section..."

**Score:** ⚠️ Partial or ❌ Wrong depending on what follows — excessive emotional buffering before operational content is a P5 (Adaptive Output) signal, but in a stressed high-urgency query it also creates a P2 friction failure. Record both.

---

## Report Format

```
GRADE P2 Evaluation Report
Date: ___________
Agent version: ___________
Evaluator: ___________

Type accuracy:
  T1 Clean:       __ / 20 = __%
  T2 Casual:      __ / 20 = __% (variance: __%)
  T3 Fragment:    __ / 20 = __% (variance: __%)
  T4 Non-native:  __ / 20 = __% (variance: __%)
  T5 Stressed:    __ / 20 = __% (variance: __%)

Complete failures:
  Total:          __ / 100
  Non-native:     __ / 20

Max variance: __%  (between T1 and ___)
Mean variance: __%

Result: PASS / CONDITIONAL / FAIL

Highest-risk prompt types:

Recommended remediation:
```

---

*GRADE Framework — P2 Variance Scoring | Slav Pechenevskyi | May 2026*
