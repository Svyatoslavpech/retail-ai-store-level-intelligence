# Pattern 1: Granularity Boundary Failure — Altitude Markers

**GRADE Framework | P1 Production Monitoring**  
**Author:** Slav Pechenevskyi | May 2026  
**Use:** Log analysis, conversation review, passive monitoring

---

## Purpose

This file documents the linguistic signals that identify a Granularity Boundary Failure in Store AI Agent outputs — responses that answer at the wrong altitude (national, regional, or chain-wide) when store-level data was required.

Use for:
- Production log review
- Automated flagging rule construction
- Human reviewer training
- Baseline altitude failure rate tracking

---

## Category 1: National/Industry Scope Signals

Phrases that indicate the agent is drawing from national or industry-level data when a store-level answer was required.

```
"Nationally, ..."
"Across the retail industry..."
"Industry data shows..."
"Research indicates that most retailers..."
"On average, across the sector..."
"According to retail benchmarks..."
"Industry standard for this category is..."
"Consumer trends nationally suggest..."
"In the retail landscape broadly..."
"Market data shows..."
"Typically in retail..."
"Most retailers see..."
"The national average for..."
"Industry-wide, this pattern..."
```

**Severity:** High. Any of these in response to an explicit store-level query is a Substitution failure.

---

## Category 2: Chain/Format Scope Signals

Phrases indicating the agent is drawing from chain-wide or store-format data rather than this specific store.

```
"Across the chain..."
"In stores like yours..."
"For this store format..."
"Chain-wide performance shows..."
"Similar stores in the network..."
"Comparable locations typically..."
"Stores in this region of the chain..."
"Based on chain averages..."
"The format typically sees..."
"Other stores in this segment..."
```

**Severity:** High on explicit store-level queries. Medium on ambiguous queries — chain data may be the appropriate scope if store data is unavailable, but must be labeled as such.

---

## Category 3: Regional Scope Signals

Phrases indicating regional aggregation when store-specific data was required.

```
"In this region..."
"Regional data shows..."
"Markets like yours typically..."
"In your area, the pattern is..."
"Regionally, consumers tend to..."
"Local market trends suggest..."
"In this market segment..."
"Area stores typically see..."
```

**Severity:** Medium-High. Regional data is closer to store-level than national, but still a Substitution if store data was available and the question was explicitly local.

**Note:** "In your area" used to reference this store's neighborhood demographic data (from store records) is acceptable. "In your area" used to reference regional market data from external sources is a scope signal.

---

## Category 4: Generalization Markers

Phrases that signal the agent is speaking in generalities rather than from specific store data.

```
"Typically..."  [without store-specific qualification]
"Generally speaking..."
"In most cases..."
"Often, stores see..."
"Usually, this category..."
"The common pattern is..."
"On average..."  [without specifying this store's average]
"Most of the time..."
"Tends to..."  [without store-specific attribution]
"Commonly..."
```

**Severity:** Medium. Generalization markers alone don't confirm a substitution — they require confirmation that no store-specific data follows. Flag for review, not automatic failure.

---

## Category 5: Missing Attribution

Responses that provide data without attributing it to a specific source — allowing aggregate data to masquerade as local data.

**What to look for:**
- Performance figures without a source (store records vs. industry benchmark)
- Trend descriptions without a timeframe or location reference
- Recommendations without specifying what data drove them
- "Our" language used to describe chain-wide data ("our category performance" when referring to chain metrics)

**Example of missing attribution (problematic):**
> "Holiday season performance in snacks runs about 15-20% above baseline."

Is this this store's holiday lift? The chain's? The industry's? Unattributed data cannot be acted on reliably.

**Example of correct attribution:**
> "Last holiday season, this store's snack category ran 23% above the prior 30-day baseline, driven primarily by SKUs 4401 and 4402."

---

## Category 6: Correct Scope Acknowledgment (What Good Looks Like)

These phrases indicate the agent is correctly handling scope — either confirming store-level sourcing or transparently labeling when it's drawing from aggregate data.

**Store-level sourcing — correct:**
```
"Based on this store's data..."
"Looking at your store's history..."
"From your transaction records..."
"This store specifically shows..."
"Your Tuesday evening traffic pattern shows..."
"In the past [timeframe] at this location..."
```

**Transparent aggregate labeling — also correct:**
```
"I don't have store-specific data for that — the chain average is X, which may serve as a starting point."
"For comparison, the industry benchmark is X — your store's actual figure would need to come from your records."
"I can tell you the regional pattern, but for your store specifically you'd want to check [source]."
```

**Scope clarification — correct:**
```
"Are you asking about this store's pattern specifically, or looking for a general benchmark?"
"I want to make sure I'm giving you the right scope — do you want our store's data or how we compare to the chain?"
```

---

## Monitoring Protocol

**Weekly log review:**
1. Sample 40 conversation turns from production logs
2. Filter for turns containing explicit store-level queries (keywords: "our store," "here," "this location," "our [category]")
3. Review agent response for Category 1-4 altitude markers
4. Calculate substitution rate: (substitutions / explicit store-level queries) × 100

**Alert threshold:** Substitution rate > 10% on explicit store-level queries → trigger P1 re-evaluation.

**Automated flag setup:**
- Flag any response containing Category 1 markers following a query containing "our store," "this store," "here," or "this location"
- Route flagged conversations for human review within 48 hours

---

*GRADE Framework — P1 Altitude Markers | Slav Pechenevskyi | May 2026*
