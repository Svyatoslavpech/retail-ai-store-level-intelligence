# Pattern 3: Asymmetric Error Tolerance — Remediation Guide

**GRADE Framework | P3 Post-Evaluation Intervention**  
**Author:** Slav Pechenevskyi | May 2026

---

## Failure Type Diagnosis

| Failure Type | Signal | Remediation |
|---|---|---|
| Critical Role Error | TL acted on wrong answer without catching it | Level 1 — immediate |
| TL usability < 75% | Agent output consistently unclear to TL users | Level 1 + Level 2 |
| TL 75-84%, no CREs | Output usable but not optimized for TL | Level 2 |
| Role calibration missing | Same output regardless of user role | Level 2 + Level 3 |
| SM over-served, TL under-served | Output too analytical, not decision-ready | Level 2 |

---

## Level 1: Output Structure for Team Lead Usability

**Use when:** Any Critical Role Error, or TL usability < 75%

The core problem: agent output is organized around data, not around decisions. A Team Lead needs to know what to do — not just what is true.

### Intervention A: Decision-First Output Format

Add to system prompt:

```
When responding to operational queries, structure your output as follows:

1. RECOMMENDATION (one sentence): What should the user do?
2. KEY DATA (2-3 data points): What supports this recommendation?
3. TIMING (if applicable): When does this need to happen?
4. VERIFY (if applicable): What should the user check before acting?

Example:
Question: Should I reorder SKU 2291 today?

RECOMMENDATION: Yes — place the reorder before noon today.
KEY DATA: 19 units in stock / 8 units per day velocity / 2-day lead time
TIMING: Order by noon to ensure delivery before stockout on Thursday
VERIFY: Confirm lead time with supplier if unsure — standard is 2 days

This format ensures the response is actionable for users at all experience levels.
```

**Test after:** Run R1-R5 from rapid assessment with TL evaluator. Usability should improve significantly.

---

### Intervention B: Operational Translation Layer

Some agent outputs are factually correct but operationally opaque. Add explicit translation:

```
After providing data, always add an operational conclusion:
- "This means: [plain language operational implication]"
- "Action required: [specific step]" or "No action needed — [reason]"
- "Priority: [High / Medium / Monitor]"

Example:
"Shrinkage is running at 8.3% this week vs. the 2.1% store average and 3.4% category average.
This means: shrinkage in this aisle is 4x normal. This is not a rounding error — it needs investigation.
Action required: Physical count of snack endcaps. Check camera coverage for the east aisle section.
Priority: High — three consecutive weeks above 5%."
```

---

### Intervention C: Safety and Compliance Escalation Protocol

For safety and compliance queries specifically, inject explicit escalation guidance:

```
For any response involving:
- Temperature exceedances (any temp above 40°F for refrigerated goods)
- Compliance variances (planogram, promotional, regulatory)
- Product safety (expiration, cross-contamination risk)

Always end with:
"Next step: [specific action]
Escalate to: [role — Store Manager / Food Safety Lead / Department Manager]
Document: [Yes/No — and if yes, what to record]"
```

This ensures TL knows exactly what to do and who to involve — regardless of experience level.

---

## Level 2: Role-Adaptive Output

**Use when:** TL usability 75-84%, or agent gives identical output regardless of role

The problem: agent is not calibrating output to the user's operational level. The same response works for a Store Manager and fails a Team Lead.

### Intervention A: Role Signal in System Context

Ensure role is passed in system context for every conversation:

```
User role: [STORE_MANAGER / TEAM_LEAD / DEPARTMENT_LEAD / ASSOCIATE]
Experience level: [SENIOR (10+ years) / MID (3-9 years) / JUNIOR (0-2 years)]
```

Then add role-based output instructions:

```
If user role is STORE_MANAGER or experience is SENIOR:
- Lead with data and analysis
- Trust user to draw operational conclusions
- Be concise — SM doesn't need hand-holding
- Focus on insights and implications, not process

If user role is TEAM_LEAD or experience is JUNIOR:
- Lead with recommendation, then support with data
- Translate every metric into operational language
- Be explicit about next steps and timing
- Flag what needs escalation vs. what TL can handle independently
```

---

### Intervention B: Role-Calibrated Few-Shot Examples

Inject parallel examples showing same query handled differently by role:

```
STORE MANAGER — "What's happening with dairy this week?"
Response: "Velocity up 12% WoW. Stock adequate through weekend — 
18 units on top 3 SKUs. Shrinkage in target at 3.1%. Weekend delivery confirmed."
[Concise. Data-forward. SM synthesizes the picture.]

TEAM LEAD — "What's happening with dairy this week?"
Response: "Dairy is performing well this week — sales are up 12% from last week.
You have enough stock to get through the weekend without reordering.
One thing to watch: shrinkage is at 3.1%, which is right at the target. 
If it creeps above 4%, do a rotation check on the shorter-dated items.
Weekend delivery is confirmed, so no action needed there."
[Structured narrative. Conclusions stated. Action guidance explicit.]
```

---

### Intervention C: Ambiguous Output Resolution

For outputs that are numerically correct but directionally unclear, add a mandatory conclusion statement:

```
When presenting comparative data (this period vs. last period, store vs. benchmark),
always include a directional conclusion:
- "This is [better / worse / stable] because [reason]."
- "The trend is [improving / declining / stable]."
- "Relative to target, this is [above / below / at]."

Never present three numbers and leave the user to determine direction.
```

---

## Level 3: Verification Prompting for High-Stakes Outputs

**Use when:** CREs occurred on wrong-answer sequences; SM catch rate was low

The problem: agent output is accepted too readily. Neither role is prompted to verify before acting.

### Intervention: Explicit Verification Prompts

For high-stakes query domains, add a verification prompt to the output:

```
For inventory counts, safety thresholds, and compliance status:
End every response with one of:
- "Verify before acting: [what to check and where]"
- "This is based on system data as of [timestamp] — confirm with physical check if acting on this."
- "If this doesn't match your observation, trust your observation and check [source]."
```

This is not a disclaimer — it's an operational instruction that reduces the cost of a wrong answer by prompting the user to verify before the error becomes an action.

---

## Re-evaluation After Remediation

| Intervention | Re-evaluation |
|---|---|
| Level 1 (output structure) | Rapid 10-sequence with TL evaluator — focus R1-R5 |
| Level 2 (role-adaptive) | Full 20-sequence — both evaluators required |
| Level 3 (verification prompting) | Full 20-sequence — especially A11-A15 (wrong answer sequences) |
| After any CRE | Full 20-sequence mandatory before re-deployment to TL users |

---

## What Not to Do

**Don't simplify for TL by removing accuracy**
A response that tells a TL "you need to reorder" without the supporting data is not better — it just moves the error risk later, when TL can't explain why they ordered without context.

**Don't optimize for SM at TL's expense**
If resources are constrained, role-adaptive output feels expensive. The alternative is deploying an agent that systematically fails your highest-risk user group.

**Don't confuse verbosity with TL-readiness**
Longer responses don't help TL users. Clearer structure does. The Decision-First format (Level 1, Intervention A) works because it changes sequence — not length.

---

*GRADE Framework — P3 Remediation Guide | Slav Pechenevskyi | May 2026*
