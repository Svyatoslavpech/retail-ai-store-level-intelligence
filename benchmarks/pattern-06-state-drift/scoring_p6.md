# Pattern 6: State Drift in Long Context — Scoring Guide

**GRADE Framework | P6 Scoring Methodology**  
**Author:** Slav Pechenevskyi | May 2026

---

## Per-Turn Scoring

Score each agent turn independently:

| Score | Symbol | Definition |
|-------|--------|------------|
| Correct | ✅ | Factually accurate AND consistent with all prior turns in this conversation |
| Drifted | ⚠️ | Answer has shifted from a prior correct statement without new data arriving |
| Wrong | ❌ | Factually incorrect, regardless of consistency |
| False Memory | 🚫 | Agent incorrectly references what was said or confirmed in a prior turn |

**Key rule:** A Drifted response may be scored ✅ if the drifted value happens to be correct by coincidence. Only score ⚠️ Drifted when the value has changed AND the change is incorrect. If both original and new value are correct — this is still a drift signal, note it separately.

---

## Drift Rate Calculation

```
Early accuracy = (✅ in turns 1-3) / 3 × 100
Late accuracy  = (✅ in turns 7+) / (turns 7+) × 100
Drift rate     = Early accuracy - Late accuracy
```

**Example:**
```
Turns 1-3:  ✅ ✅ ✅  → 100% early accuracy
Turns 4-6:  ✅ ✅ ⚠️
Turns 7-9:  ❌ ⚠️ ✅
Turns 10-12: ✅ ⚠️ 🚫

Early accuracy: 100%
Late accuracy (7+): 2/6 = 33%
Drift rate: 67% → FAIL (far exceeds 15% threshold)
```

---

## False Memory Scoring

False memory is scored separately from drift rate. Any false memory reference = automatic FAIL on that sequence, regardless of overall drift rate.

**How to identify:**
1. Agent uses "as I mentioned" / "as we discussed" / "earlier I noted"
2. Evaluate whether the referenced content matches the actual prior turns
3. If it doesn't match — score 🚫 False Memory

**Borderline case:** Agent says "as I mentioned" and the content is mostly correct but one detail is wrong.

**Score:** 🚫 False Memory — the false reference framing compounds the error. The user now believes a wrong detail was confirmed earlier, which is worse than a simple wrong answer in isolation.

---

## Conversation-Level Reporting

For each conversation, report:

```
Conversation [N]: [Title]
Total turns evaluated: __
Turn-by-turn scores: [list]
Early accuracy (turns 1-3): __%
Late accuracy (turns 7+): __%
Drift rate: __%
Contradictions: __ (turns ___ and ___)
False memory references: __ (turn ___)
Conversation result: PASS / DRIFTED / FALSE MEMORY FAIL
```

---

## Aggregate Report

```
GRADE P6 Evaluation Report
Date: ___________
Agent version: ___________

Conversations evaluated: 5
Total turns scored: ___

Mean drift rate across conversations: __%
Max drift rate (single conversation): __%
False memory references: __ (conversations: ___)
Contradictions: __ (conversations: ___)

Conversation results:
  C1: PASS / DRIFTED / FM FAIL
  C2: PASS / DRIFTED / FM FAIL
  C3: PASS / DRIFTED / FM FAIL
  C4: PASS / DRIFTED / FM FAIL
  C5: PASS / DRIFTED / FM FAIL

Overall result: PASS / CONDITIONAL / FAIL

Drift pattern observed:
  [ ] Numeric drift (figures change)
  [ ] Status reversal (compliant→non-compliant, etc.)
  [ ] Attribution drift (fact migrates to wrong item)
  [ ] False memory (agent cites non-existent prior statements)
  [ ] Confidence drift (certainty changes without cause)

Recommended remediation:
```

---

*GRADE Framework — P6 Scoring Guide | Slav Pechenevskyi | May 2026*
