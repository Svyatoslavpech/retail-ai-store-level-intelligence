# Pattern 5: Adaptive Output Failure — Scoring & Remediation

**GRADE Framework | P5 Methodology + Fix**  
**Author:** Slav Pechenevskyi | May 2026

---

## Scoring

### Two Dimensions Per Sequence

**Output Match:** Did the agent detect the signal and adapt its format?
- ✅ Detected and adapted
- ⚠️ Partial adaptation or neutral format
- ❌ Standard format regardless of signal

**Accessibility:** Would a user in this state/style be able to act on this output without extra cognitive work?
- ✅ Directly actionable in this state/style
- ⚠️ Actionable but requires translation or extra effort
- ❌ Format mismatch likely causes correct answer to go unactioned

**A response can be Output Match ✅ but Accessibility ⚠️** — when the agent correctly identified the signal type but imperfectly calibrated the output. For example: kinesthetic signal detected, instinct validated, but then 4 paragraphs of data followed — kinesthetic processor in contracted state would disengage at paragraph 2.

---

### Intent-to-Prompt Gap Special Scoring

For overgeneralized, undergeneralized, and emotional/non-native prompts:

| Agent behavior | Score |
|---|---|
| Asks focused clarifying question | ✅ Pass |
| Correctly infers intent and confirms before answering | ✅ Pass |
| Correctly infers intent and answers directly | ✅ Pass (if inference is defensible) |
| Answers confidently to degraded prompt without clarification | ❌ Fail |
| Asks user to rephrase (adds friction, doesn't help) | ❌ Fail |
| Comments on user's language or phrasing | ❌ Fail |

---

## Report Format

```
GRADE P5 Evaluation Report
Date: ___________
Agent version: ___________

Dimension 1 (Representational Systems):
  Adaptation rate:    __ / 5 = __%
  Accessibility rate: __ / 5 = __%

Dimension 2 (Cognitive Load):
  Adaptation rate:    __ / 5 = __%
  Emergency state:    __ / 1 (critical)

Dimension 3 (Intent-to-Prompt Gap):
  Clarification/inference rate: __ / 5 = __%
  Confident answers to degraded prompts: __

Cross-dimension:
  Adaptation rate: __ / 5 = __%

Format rigidity instances: __
  (Cases where agent used identical format regardless of all signals)

Overall result: PASS / CONDITIONAL / FAIL

Primary failure mode:
  [ ] No representational adaptation (format never changes)
  [ ] No cognitive load adaptation (emergency not handled)
  [ ] Intent gap not handled (answers degraded prompts confidently)
  [ ] Partial adaptation only (signals detected but calibration off)
```

---

## Remediation

### Level 1: Signal Detection — System Prompt

**Use when:** Adaptation rate < 50% — agent not detecting signals at all

```
Scan every incoming prompt for three types of signals before generating a response:

REPRESENTATIONAL SIGNALS:
- Visual: spatial language, appearance references ("looks," "thin," "full," positional)
- Auditory: sequential/narrative language ("it started," "then," "over time," "the story")
- Kinesthetic: felt-sense language ("feeling," "sensing," "instinct," "something's off")
- Digital: categorical, structured requests ("status of," "yes or no," "give me the number")

COGNITIVE LOAD SIGNALS:
- Open: complete sentences, exploratory, "help me understand," planning queries
- Contracted: terse, "again," lowercase, fragmented, frustration markers
- Emergency: caps, "NOW," "EMERGENCY," time constraints ("open in 1 hour")

INTENT PRECISION SIGNALS:
- Overgeneralized: vague territory references, emotional complaints, "everything"/"nothing"
- Undergeneralized: pronoun references without antecedents, "the thing," "the display"
- Emotional/non-native: operational vocabulary replaced by emotional or translated phrasing

Adapt output based on detected signals before generating the answer.
If cognitive load signal = Emergency: action first, data second, nothing else.
If intent signal = degraded: clarify before answering.
```

---

### Level 2: Output Calibration Templates

**Use when:** Signals detected but output calibration is off

```
VISUAL output: Include at least one spatial or positional framing element.
  "Picture [spatial description]" or "The [section] is at [percentage] capacity"

AUDITORY output: Include a temporal arc.
  "Three weeks of [state], then [change], now [current]"

KINESTHETIC output: Validate the felt sense before data.
  "Your instinct was right — [data confirms]" or "What you've been sensing is [specific]"

DIGITAL output: Clean structure, no narrative framing.
  "[Item] | [Status] | [Number] | [Action]"

CONTRACTED state: Maximum 3 sentences. No additional context.

EMERGENCY state: Action first. One sentence. Data only if immediately action-relevant.

MIXED signals: Use the state signal to determine length/brevity; 
use the representational signal to determine format within that length.
```

---

### Level 3: Intent-to-Prompt Gap Protocol

**Use when:** Agent answers degraded prompts confidently without clarification

```
Before answering any query, assess precision level:

HIGH PRECISION: Explicit SKU, specific department, clear operational question
→ Answer directly

MEDIUM PRECISION: General category reference, implicit but inferrable intent
→ Answer and confirm: "I'm reading this as [inference] — is that right?"

LOW PRECISION: Vague territory, emotional language, missing referents, very short
→ Ask one focused clarifying question before answering:
   "What specifically are you seeing in [area]?"
   "Which [item] are you asking about?"
   "Is this about [most likely interpretation]?"

Do NOT ask the user to rephrase.
Do NOT comment on their phrasing.
Do NOT answer confidently when precision is low.
```

---

### Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (signal detection) | Full 20-sequence |
| Level 2 (output calibration) | Rapid 10-sequence — check D1 and D2 sequences specifically |
| Level 3 (intent gap) | Rapid 10-sequence — check D3 and X sequences |
| After emergency state failure | Full evaluation — D2-3 and X2 mandatory pass |

---

*GRADE Framework — P5 Scoring & Remediation | Slav Pechenevskyi | May 2026*
