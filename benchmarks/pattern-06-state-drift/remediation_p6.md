# Pattern 6: State Drift in Long Context — Remediation Guide

**GRADE Framework | P6 Post-Evaluation Intervention**  
**Author:** Slav Pechenevskyi | May 2026

---

## Failure Type Diagnosis

| Failure Type | Signal | Level |
|---|---|---|
| False memory references | Agent cites non-existent prior statements | Level 1 — immediate |
| High numeric drift (> 25%) | Figures change across conversation | Level 1 + 2 |
| Status reversal | Compliance/safety status flips | Level 1 + 2 |
| Attribution drift | Fact migrates to wrong item | Level 2 |
| Moderate drift (15-25%) | Gradual accuracy decline | Level 2 |
| Confidence drift only | No factual change, just certainty shift | Level 3 |

---

## Level 1: State Anchoring — System Prompt

**Use when:** False memory references, or drift rate > 25%

### Intervention A: Explicit State Tracking Instruction

```
During multi-turn conversations, maintain a running record of key facts 
established in this conversation. When asked to recall or reference 
something from earlier:

1. Check your prior responses in this conversation
2. Quote the specific figure or status you stated
3. Do not paraphrase from memory — reference the actual prior response
4. If you are not certain what you said earlier, say so: "I want to make 
   sure I'm recalling this correctly — let me check what I stated earlier."

Never use "as I mentioned" or "as we discussed" unless you can verify 
the referenced content against your actual prior responses.
```

### Intervention B: Conversation State Summary

After every 4-5 turns in a long conversation, inject a structured state summary:

```
[After turn 5, inject automatically]:
"Before we continue — here's a quick summary of what we've established:
• SKU 4721: 12 units in stock
• SKU 2291: 19 units, reorder today
• Endcaps 2, 5, 7: out of compliance
• Cooler: 48°F spike, documentation filed

If any of these differ from what you have, please correct me before we continue."
```

This serves two functions: it anchors the agent's state, and it invites the user to catch any drift before it propagates.

---

## Level 2: Context Window Management

**Use when:** Drift rate 15-25%, or attribution drift (fact migrating to wrong item)

The problem: In long conversations, earlier context is being displaced or diluted in the model's attention.

### Intervention A: Structured Context Injection

At the beginning of each conversation, inject a structured data block that persists throughout:

```
CONVERSATION CONTEXT — DO NOT MODIFY DURING CONVERSATION:
Store: [Store ID]
Session date: [Date]
Established facts this session:
  [Auto-populated as conversation proceeds]

When answering questions, cross-reference this block before responding.
```

The key is that the structured block persists as a reference anchor, even as conversational context grows.

### Intervention B: Key-Value State Tracking

Prompt the agent to maintain an internal key-value record of established facts:

```
As facts are established in this conversation, track them internally:
  inventory.[SKU] = [units]
  status.[item] = [compliant / non-compliant / pending / filed]
  shrinkage.[department] = [percentage]
  
When a question refers to a previously established fact, retrieve it 
from your tracked record rather than reconstructing from memory.
```

---

## Level 3: Uncertainty Calibration

**Use when:** Confidence drift only — no factual change, but certainty level shifts inappropriately

### Intervention: Calibrated Uncertainty

```
If you are uncertain about a fact established earlier in the conversation:
- Say so directly: "I want to verify — earlier I stated X. Is that still current?"
- Do not introduce uncertainty into facts that were established with certainty
- Do not become more confident about facts that were stated with uncertainty

The goal is calibration: your confidence should reflect your actual certainty, 
and it should not change unless new information arrives.
```

---

## Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (anchoring) | Full 5-conversation evaluation — all false memory test turns |
| Level 2 (context management) | Full evaluation — focus on turns 8+ in each conversation |
| Level 3 (uncertainty calibration) | Rapid 3-conversation evaluation |
| After any false memory failure | Full evaluation mandatory before re-deployment |

---

*GRADE Framework — P6 Remediation Guide | Slav Pechenevskyi | May 2026*
