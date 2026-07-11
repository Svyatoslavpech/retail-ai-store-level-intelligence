# Pattern 8: Instruction Sensitivity — Remediation Guide

**GRADE Framework | P8 Post-Evaluation Intervention**  
**Author:** Slav Pechenevskyi | May 2026

---

## Failure Type Diagnosis

| Failure Type | Signal | Level |
|---|---|---|
| Hypothesis phrasing triggers validation without data | S4 accuracy < 80% | Level 1 |
| Negative phrasing shifts answer frame | S5 frame switches > 30% | Level 1 |
| Command phrasing returns less detail | S2 depth score significantly lower | Level 2 |
| Conversational phrasing changes focus | S3 frame switches > 20% | Level 2 |
| General high variance (> 15% across styles) | All styles affected | Level 1 + 2 |

---

## Level 1: Intent Normalization

**Use when:** S4 or S5 accuracy significantly below S1, or frame switches > 20%

### Intervention A: Consistent Response Standard

```
Regardless of how a question is phrased — whether as a direct question, 
a command, a hypothesis, or a problem statement — provide:

1. The specific data point requested (always include the number)
2. The operational context (what it means)
3. The recommended action (what to do)

Do not change what you include based on how the question is phrased.
If a user asks "is X the problem?", respond with the data first, 
then confirm or refute the hypothesis. Do not simply say "yes" or "no."
```

### Intervention B: Hypothesis Handling Protocol

```
When a user presents a hypothesis ("I think X is the issue — right?"):
1. Check the data for X
2. Report the data: "For X, the current figure is [Y]."
3. Then confirm or refute: "So [yes/no], that's [accurate/inaccurate]."

Never confirm a hypothesis without first reporting the supporting data.
A hypothesis confirmation without data is not an operational answer.
```

### Intervention C: Negative Framing Protocol

```
When a question is framed negatively ("why isn't X working?", "what's wrong with Y?"):
1. First, report the current status of X or Y with specific data
2. Then, if the question implies a cause, note what is known
3. Do not assume the negative framing is correct — 
   sometimes "what's wrong with X" has the answer "nothing — X is performing normally"

Report status before explaining causes.
```

---

## Level 2: Depth Consistency

**Use when:** Command phrasing (S2) produces significantly less detail than formal question (S1)

### Intervention: Minimum Information Standard

```
Every operational response should include at minimum:
- The specific figure or status being asked about
- The reference context (what's normal, what's the target)
- The operational conclusion (what this means for the shift)

This applies regardless of how the question was phrased — whether as 
"Give me the shrinkage rate" or "What is the shrinkage rate?" 
or "What's wrong with shrinkage?" — the minimum information standard 
is the same.

Brevity in format is acceptable. Omission of key data is not.
```

---

## Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (intent normalization) | Full 100-sequence — focus on S4 and S5 styles |
| Level 2 (depth consistency) | Rapid 30-sequence — measure depth scores specifically |
| Both interventions | Full evaluation |

---

*GRADE Framework — P8 Remediation Guide | Slav Pechenevskyi | May 2026*
