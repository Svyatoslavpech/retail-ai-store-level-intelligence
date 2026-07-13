# Pattern 4: Information Role Inversion — Scoring & Remediation

**GRADE Framework | P4 Methodology + Fix**  
**Author:** Slav Pechenevskyi | May 2026

---

## Scoring

### SM Score Criteria

| Score | Definition |
|-------|-----------|
| ✅ Pass | SM can extract answer in under 10 seconds. No unnecessary explanation. Precision high. |
| ⚠️ Partial | SM gets the answer but had to work through more than needed. Minor friction. |
| ❌ Fail | SM would stop using agent for this query type. Too slow, too verbose, wrong focus. |

### TL Score Criteria

| Score | Definition |
|-------|-----------|
| ✅ Pass | TL understands what the data means and knows what to do. Reasoning is visible. |
| ⚠️ Partial | TL gets the data but not the operational conclusion or action path. |
| ❌ Fail | TL cannot determine what to do from this output. Data without meaning. |

### Cross-Mode Failure

A Cross-Mode Failure occurs when the output is clearly calibrated for one role and fails the other:

- **SM-optimized output to TL context:** Concise data summary, no reasoning, no action path → TL fails
- **TL-optimized output to SM context:** Lengthy explanation of basics SM already knows → SM fails

---

## Report Format

```
GRADE P4 Evaluation Report
Date: ___________

SM usability:       __ / 20 = __%
TL usability:       __ / 20 = __%
Cross-mode failures: __
Adaptation success (R17-R20): __ / 4

Default mode calibration:
  [ ] Correctly defaults to TL mode when role ambiguous
  [ ] Correctly uses SM mode when signaled
  [ ] Correctly uses TL mode when signaled
  [ ] Adapts mid-conversation when role changes

Result: PASS / CONDITIONAL / FAIL

Primary failure mode:
  [ ] Over-calibrated for SM (TL fails)
  [ ] Over-calibrated for TL (SM fails)
  [ ] No calibration (both fail at moderate rate)
  [ ] Doesn't adapt to role signals

Recommended remediation level:
```

---

## Remediation

### Level 1: Mode Definition — System Prompt

**Use when:** Both roles < 80%, or agent shows no mode differentiation

```
You serve two primary user types with different operational needs:

STORE MANAGER MODE (when role = SM or signals suggest SM):
- Lead with the data point, not the explanation
- Be concise — SM already has context
- Include adjacent relevant data they might have missed
- Do not explain concepts they know (inventory turns, lead time, etc.)
- Target: answer in 1-3 sentences

TEAM LEAD MODE (when role = TL or query signals uncertainty):
- Lead with what the data means, then the data itself
- Show the reasoning: "Here's why this matters..."
- Give explicit action guidance: "What to do: [step]"
- Provide context for what's normal vs. abnormal
- Target: answer in 3-6 sentences with reasoning

DEFAULT: When role is unclear, use TL mode. The cost of over-explaining 
to an SM (minor inefficiency) is lower than under-explaining to a TL 
(operational confusion).
```

---

### Level 2: Role Detection

**Use when:** One role fails while other passes — agent is calibrated for one only

Inject role detection from query signals:

```
Detect user mode from query signals:

SM signals (use concise encyclopedia mode):
"Quick...", "Just...", "Confirm...", "Only need...", 
"What did X come out to?", very short queries with implicit context

TL signals (use discovery mode with reasoning):
"Help me understand...", "I'm not sure...", "Walk me through...",
"What should I focus on?", "Why is X happening?",
"I've never dealt with this before..."

When explicit role context is provided in system prompt or conversation:
honor it precisely — SM gets SM mode, TL gets TL mode.
```

---

### Level 3: Output Templates Per Mode

**Use when:** Mode detection works but output quality still divergent

Provide explicit output templates:

```
SM MODE TEMPLATE:
[Direct answer to question] + [Key supporting figure] + [Adjacent relevant data if any]
Example: "Yes — 12 units, 1.5-day supply. Also check 2291: same urgency."

TL MODE TEMPLATE:
[What the data shows] + [What it means] + [Why it matters] + [What to do] + [By when]
Example: "SKU 4721 is at 12 units — that sounds like a lot, but at 8 units per day 
it's only 1.5 days of supply. Lead time is 2 days, so if you don't order today, 
you'll hit a stockout by Thursday morning. Order before noon today."
```

---

### Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (mode definition) | Full 20-sequence — both evaluators |
| Level 2 (role detection) | Rapid 10-sequence — focus Q6, Q7, Q9, Q10 |
| Level 3 (output templates) | Rapid 10-sequence — measure depth scores per role |

---

*GRADE Framework — P4 Scoring & Remediation | Slav Pechenevskyi | May 2026*
