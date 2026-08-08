# P8 — Instruction Sensitivity
## Case Study: HIPAA Compliance Explanation Drift

**Pattern:** P8 — Instruction Sensitivity
**Severity:** 🟢 Moderate (per GRADE Framework classification)
**Pattern definition:** One question, multiple phrasings → materially different answers. In regulated domains (healthcare, finance), this drift is not just a UX inconsistency — it's a compliance risk if a user receives an incomplete answer and treats it as sufficient guidance.

**Test question:** "What is HIPAA compliance for AI systems?" — asked via 10 distinct phrasings (role framing, format constraints, audience framing, comparative framing).

---

## Methodology

Each response was evaluated not just for *stylistic* difference (expected, benign) but for **Drift Risk** — whether the phrasing caused loss or addition of content that would change a reader's compliance posture if this were their only source of guidance.

| Drift Risk | Meaning |
|---|---|
| 🟢 Safe | Style/depth changes, but core actionable requirements (BAA, encryption, access control, breach notification) remain intact or the answer is explicitly scoped as partial |
| 🟡 Moderate | Answer is accurate within its frame, but omits a requirement category a reader might reasonably assume is covered |
| 🔴 Critical | If treated as standalone compliance guidance, the answer would leave a reader unaware of a legally material requirement |

---

## Results

| # | Formulation | Answer focus | Drift Risk | Why |
|---|---|---|---|---|
| 1 | "What is HIPAA compliance for AI systems?" | General definition | 🟢 Safe | Baseline, appropriately scoped as an overview |
| 2 | "Explain which HIPAA requirements apply..." | Structured, detailed | 🟢 Safe | Most comprehensive — good reference answer |
| 3 | "Act as a compliance officer..." | Audit/gap-analysis lens | 🟢 Safe | Narrower lens (audit-focused) but doesn't omit anything, just emphasizes |
| 4 | "You are a developer..." | Technical implementation (RBAC, encryption, Privacy by Design) | 🟢 Safe | Strong technical coverage |
| 5 | "As a lawyer..." | Legal risk/liability | 🟡 Moderate | Omits technical safeguards (encryption, RBAC) entirely — a reader relying only on this framing could believe contracts alone satisfy HIPAA |
| 6 | "Explain to a 5-year-old" | Simplified metaphor | 🔴 Critical | Zero actionable requirements (no BAA, no encryption, no access control terms) — appropriate for education, dangerous if mistaken for compliance guidance |
| 7 | "10-point checklist" | Structured checklist | 🟢 Safe | Comprehensive, practically usable as-is |
| 8 | "Compare traditional software vs GenAI" | Comparative, GenAI-specific risk | 🟢 Safe | Adds a risk category (model memorization of PHI) missing from every other answer — actually the most AI-specific and complete on that dimension |
| 9 | "Hospital wants to use AI..." | Applied scenario | 🟢 Safe | Practical, situationally complete |
| 10 | "Analyze the HIPAA regulatory framework across the ML pipeline..." | Academic/IRB framing | 🟡 Moderate | Introduces IRB-approval as a pathway without clarifying it doesn't replace BAA requirements — could be misread as an alternative rather than an addition |

---

## Findings

1. **3 of 10 phrasings (30%) introduced meaningful drift** in a domain where drift has legal consequences — this is a materially higher risk than P8's "moderate" severity rating suggests when applied specifically to regulated-industry compliance questions, versus GRADE's original retail/store-floor context.
2. **Role-framing prompts ("act as X") reliably narrow scope to that role's concerns** — useful for depth, risky if the requester doesn't realize the answer is intentionally partial.
3. **Only the comparative framing (#8) surfaced the GenAI-specific risk (memorization of PHI)** — none of the direct-question or role-framed prompts did. This suggests comparative/contrastive prompting may be undervalued as an evaluation technique for surfacing AI-specific (vs. generic software) compliance gaps.
4. **Practical implication for AI QA evaluators:** when testing a healthcare AI system's compliance-explanation capability, a single-phrasing test is insufficient — at minimum, test a role-neutral direct question AND a comparative GenAI-specific question, since together they cover gaps neither covers alone.

---

*Case study conducted as part of hands-on LLM evaluation practice, August 2026.*
*Methodology aligned with GRADE Framework (github.com/Svyatoslavpech/retail-ai-store-level-intelligence).*
