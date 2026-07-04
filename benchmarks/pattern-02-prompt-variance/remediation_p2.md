# Pattern 2: Prompt Quality Variance — Remediation Guide

**GRADE Framework | P2 Post-Evaluation Intervention**  
**Author:** Slav Pechenevskyi | May 2026

---

## Failure Type Diagnosis

| Failure Type | Signal | Level |
|---|---|---|
| High variance on non-native prompts (> 25%) | Agent fails non-English phrasing patterns | Level 1 |
| High complete failure rate on fragments (> 10%) | Agent can't handle incomplete queries | Level 1 |
| High variance across all types (> 20%) | Agent is prompt-sensitive generally | Level 1 + 2 |
| Clarifying questions on clear-intent queries | Agent fails to infer intent | Level 2 |
| Correct answer but unnecessary friction | Agent adds meta-comments on phrasing | Level 3 |
| Continuation queries fail (pronoun reference) | Agent doesn't use conversation context | Level 2 |

---

## Level 1: Intent Extraction — System Prompt

**Use when:** High variance on non-native or fragment types, or high complete failure rate

The core problem: agent is parsing the surface form of the query rather than extracting the operational intent beneath it.

### Intervention A: Intent Extraction Instruction

```
You are receiving queries from a multicultural retail operations team.
Queries may be:
- Informal or colloquial ("how much milk do we have")
- Incomplete or fragmented ("dairy — stock?")
- Non-native English phrasing ("inventory dairy products how many currently")
- Emotionally loaded ("we're out of milk AGAIN what do I do")

Your job is to extract the operational intent and answer it.
Do not ask for clarification unless the query is genuinely ambiguous — 
meaning that two completely different operational questions could 
reasonably match the same words.

If intent is 95% clear — answer it. 
If intent is genuinely ambiguous — ask one focused question.
Do not comment on the phrasing or grammar of the query.
```

---

### Intervention B: Intent Mapping Reference

Provide the agent with an intent-to-query mapping for the most common operational domains:

```
Common query patterns and their operational intent:

"how much [product] do we have" → inventory count query
"do we need to order [product]" → reorder decision query  
"when is it busy" → traffic pattern query
"is [metric] bad/good/ok" → status check — return current figure + context
"are [things] right/correct" → compliance check
"what should I [do/order/focus on]" → recommendation query
"how did [thing] do" → performance retrospective
"[thing] — check" / "[thing] — status" → status check on named item
"[noun] [noun] [number]" → typically an inventory or metric query about named item

When in doubt: assume inventory, compliance, or safety — these are the highest-frequency query domains on the store floor.
```

---

### Intervention C: Non-native Phrasing Examples

Inject few-shot examples showing correct handling of non-native English patterns:

```
Example 1:
User: "dairy SKU 4721 quantity in stock how many currently"
Agent: "SKU 4721 (organic whole milk, 1 gallon) — 12 units in stock as of 5:43 AM."
[Agent answers directly without commenting on phrasing]

Example 2:
User: "endcap displays correct configuration this week yes or no"
Agent: "No — 3 endcaps are out of compliance: endcaps 2, 5, and 7 need to be reset to match this week's planogram."
[Agent answers yes/no as requested, then gives the detail]

Example 3:
User: "snack aisle shrinkage percent this week what is"
Agent: "Snack aisle shrinkage this week: 8.3%. That's above the store average of 2.1% and the category average of 3.4% — worth investigating."
[Agent extracts the metric query, returns figure with context]
```

---

## Level 2: Context Utilization — Conversation Memory

**Use when:** Fragment queries fail (pronoun reference errors), or continuation queries score below 70%

The problem: agent treats every query as a new conversation rather than using available context.

### Intervention A: Context Priority Instruction

```
When a query uses pronouns ("it," "those," "the ones," "them") or refers 
back to a prior exchange ("same as before," "and what about," "so"):
1. Check the conversation history for the most recent operational topic
2. Apply that context to the current query
3. Only ask for clarification if the pronoun reference is genuinely ambiguous
   given the prior conversation

Example of correct behavior:
Prior turn: "We're looking at dairy section performance."
User: "and the stock levels"
Agent: [Returns dairy section stock levels — does not ask "which section?"]

Example of failure:
Prior turn: "We're looking at dairy section performance."
User: "and the stock levels"
Agent: "Could you clarify which section's stock levels you'd like to review?"
[This is a P2 failure — intent was clear from context]
```

---

### Intervention B: Topic Anchoring

For multi-turn conversations, inject a running topic anchor:

```
CURRENT CONVERSATION TOPIC: [Auto-populated from prior turn]

Use this context to interpret ambiguous queries before asking for clarification.
```

---

## Level 3: Friction Reduction

**Use when:** Accuracy is acceptable but evaluators flagged unnecessary friction (meta-comments on phrasing, excessive clarification requests)

The problem: agent is technically correct but operationally inefficient. Under time pressure, friction kills adoption.

### Intervention: Direct Response Protocol

```
When you understand the query — even if it's informally phrased — answer it directly.

Do NOT:
- Acknowledge that the phrasing was informal ("I think you're asking about...")
- Ask if you've understood correctly when you have clearly understood
- Restate the query before answering
- Comment on missing punctuation or grammar

DO:
- Lead with the answer
- Follow with the supporting data
- Keep the response as short as the question warrants
```

---

## Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (intent extraction) | Full 100-sequence — focus on T4 non-native scores specifically |
| Level 2 (context utilization) | Full evaluation — V19-V20 continuation sequences most relevant |
| Level 3 (friction reduction) | Rapid 30-sequence — evaluators score friction separately from accuracy |

---

*GRADE Framework — P2 Remediation Guide | Slav Pechenevskyi | May 2026*
