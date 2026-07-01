# Pattern 1: Granularity Boundary Failure — Remediation Guide

**GRADE Framework | P1 Post-Evaluation Intervention**  
**Author:** Slav Pechenevskyi | May 2026

---

## Failure Type Diagnosis

Before applying interventions, identify the failure type:

| Failure Type | Signal | Remediation |
|---|---|---|
| No retrieval grounding | Agent has no access to store-specific data | Level 1 — architecture |
| Retrieval exists but not triggered | Agent has store data but defaults to training data | Level 2 — system prompt |
| Retrieval triggered but scope blurred | Agent mixes store and aggregate data | Level 3 — prompt + examples |
| Ambiguous queries default to aggregate | Store-level only fails on ambiguous queries | Level 3 — default scope |

---

## Level 1: Architecture — Retrieval Grounding

**Use when:** Agent fails explicit store-level queries with no store-specific data in responses.

This is an architecture problem, not a prompt problem. The agent lacks access to store-level data. Prompt interventions will not fix this.

**Required:**
- Connect agent to store-specific data sources: POS transaction logs, inventory system, planogram database, store calendar
- Implement RAG (Retrieval-Augmented Generation) with store-scoped retrieval
- Ensure retrieval pipeline filters by store ID before passing context to the model

**Validation after:**
- Verify retrieval is returning store-specific documents, not chain-wide averages
- Check that retrieved documents contain this store's SKU-level data, not category aggregates
- Run rapid 10-sequence evaluation — if Level 1 interventions are working, store-level response rate should jump significantly

**Level 1 is a prerequisite for all other interventions.** Prompt-level fixes on an agent without retrieval grounding will produce confident-sounding responses that are still wrong.

---

## Level 2: System Prompt — Scope Constraint

**Use when:** Agent has retrieval access to store data but still defaults to aggregate data on explicit queries.

The model is choosing its training data over retrieved store data. This is a grounding priority issue.

### Intervention A: Explicit Scope Hierarchy

Add to system prompt:

```
You are a Store Intelligence Agent for [STORE ID / STORE NAME].

When answering operational questions:
1. Always prioritize data retrieved from this store's records over your general knowledge.
2. If retrieved store data is available, use it. If it conflicts with general industry patterns, the store data takes precedence.
3. If you cannot find store-specific data for a query, say so explicitly before offering any general benchmark.
4. Never substitute national, regional, or chain-wide data for store-level data without labeling it clearly.

When using aggregate data (industry benchmarks, chain averages, regional trends):
- Label it explicitly: "For comparison, the industry average is X — your store's actual figure is Y."
- Use it as context, not as the answer.
```

**Test after:** Run Q1-Q5 from rapid assessment. Substitution rate should drop to near zero.

---

### Intervention B: Store Identity Anchor

Add store identity at the top of every system prompt and every retrieved context block:

```
STORE CONTEXT:
Store ID: [ID]
Location: [City, State]
Format: [Store format]
Data currency: [Last updated timestamp]

All responses should be grounded in the data above.
```

**Why this works:** The model is more likely to prioritize store-level data when store identity is explicitly established at the beginning of context, before any query is processed.

---

### Intervention C: Fallback Protocol

Explicitly instruct the agent what to do when store data is unavailable — preventing it from defaulting silently to aggregate data:

```
When you cannot find store-specific data to answer a question:
1. Say clearly: "I don't have store-specific data for that."
2. Offer what you can: "The chain average / industry benchmark is X."
3. Label it: "This is a general figure — your store's actual number may differ."
4. Do not present aggregate data as if it were this store's data.
```

---

## Level 3: Few-Shot Examples — Scope Behavior

**Use when:** Level 2 interventions reduce Substitutions but ambiguous-scope queries still default to aggregate data.

Inject correct scope-handling examples into system prompt or conversation history:

### Example Set — Correct Scope Handling

```
Example 1 — Explicit store-level query, data available:
User: What's our Tuesday evening traffic pattern?
Agent: Based on this store's transaction data from the past 12 Tuesdays,
evening traffic peaks between 5:30 and 7:00 PM, with an average of 
143 transactions in that window — about 34% higher than Tuesday morning.
The pattern has been consistent across the past three months.

Example 2 — Explicit store-level query, data unavailable:
User: How does our customer satisfaction score compare to last year?
Agent: I don't have this store's customer satisfaction scores in the 
current data set. For context, the chain average this quarter is 4.2/5.0 —
but to see how this store specifically compares year over year, 
you'd need to pull from the customer feedback system directly.

Example 3 — Ambiguous query, defaults to store data:
User: How's organic produce doing lately?
Agent: Looking at this store's organic produce section over the past 30 days:
velocity is up 12% compared to the prior period, driven mainly by 
bagged salads and berries. Shrinkage is running at 6.3% in that subcategory,
which is above the 4.0% target. Worth a rotation check this week.

Example 4 — Multi-scope query, labels both:
User: How does our shrinkage compare to the industry?
Agent: This store's overall shrinkage rate is currently 2.8%. 
For comparison, the grocery retail industry average is 1.6%, 
and the chain average is 2.1%. This store is running above both — 
the snack and health & beauty departments are the main contributors.
```

**Test after:** Full 20-sequence evaluation. Expect ambiguous-scope handling to improve significantly.

---

## Re-evaluation After Remediation

| Intervention Applied | Re-evaluation |
|---|---|
| Level 1 (architecture) | Full 20-sequence — retrieval must be verified end-to-end |
| Level 2 (system prompt) | Rapid 10-sequence minimum |
| Level 3 (few-shot) | Full 20-sequence recommended |
| Any intervention | Check ambiguous sequences specifically — these are the last to improve |

---

## Escalation Criteria

Escalate to architecture/engineering review if:
- Level 1 interventions are in place but store-specific data still doesn't appear in responses
- Retrieval pipeline returns store data but model ignores it in favor of training data
- Substitution rate remains > 20% after Level 2 + Level 3 interventions
- Scope blurring persists on explicit queries despite system prompt constraints

At this point, the issue is likely in retrieval pipeline configuration, context window management, or model fine-tuning — beyond prompt-level intervention.

---

*GRADE Framework — P1 Remediation Guide | Slav Pechenevskyi | May 2026*
