# Pattern 4: Information Role Inversion — Rapid Assessment (10 Query Sets)

**GRADE Framework | P4 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 45-60 minutes (two evaluators)

---

## Scoring Sheet

| Set | SM Score | TL Score | Mode Match | Notes |
|-----|----------|----------|------------|-------|
| Q1 | | | | |
| Q2 | | | | |
| Q3 | | | | |
| Q4 | | | | |
| Q5 | | | | |
| Q6 | | | | |
| Q7 | | | | |
| Q8 | | | | |
| Q9 | | | | |
| Q10 | | | | |

**SM usability: __ / 10**  
**TL usability: __ / 10**  
**Cross-mode failures: __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Pass Criteria

- SM usability ≥ 80%
- TL usability ≥ 80%
- Cross-mode failures < 20%

---

## Sequences

---

### Q1 — Inventory Status

**Query:** "What's the inventory status on SKU 4721?"

**SM pass:** Agent returns figure + urgency signal in 1-2 sentences. SM doesn't have to read through explanation.

**TL pass:** Agent explains what 12 units means in supply days, why it's urgent, what to do.

**Cross-mode failure signal:** Response is too concise for TL to act on, OR too verbose for SM to use efficiently.

---

### Q2 — Reorder Decision

**Query:** "Should I reorder SKU 2291 today?"

**SM pass:** Clear yes + the math in one line ("19 units, 2.4 days, 2-day lead time").

**TL pass:** Clear yes + reasoning ("here's why today and not tomorrow") + deadline ("before noon").

---

### Q3 — Shrinkage

**Query:** "How's the snack aisle shrinkage?"

**SM pass:** Figure + comparison in one line ("8.3% vs. 2.1% store average").

**TL pass:** Figure + what it means ("significantly elevated") + what to do ("physical count, check camera coverage").

---

### Q4 — Safety

**Query:** "The cooler hit 48°F — what do I need to know?"

**SM pass:** Compliance status + action items concisely.

**TL pass:** What happened, why it matters (FDA 40°F), what to check (duration), what documentation means.

---

### Q5 — Compliance

**Query:** "Endcap compliance status?"

**SM pass:** Count + specific IDs instantly ("3 out: endcaps 2, 5, 7").

**TL pass:** Count + IDs + what compliance means + what to do + urgency.

---

### Q6 — SM-Signaled Query

**Query:** "Quick — 4721 inventory?"

**SM pass:** "12 units. 1.5 days. Reorder urgent." Nothing more.

**TL eval:** N/A — query signals SM mode.

**Cross-mode failure:** Agent adds explanation despite speed signal.

---

### Q7 — TL-Signaled Query

**Query:** "I'm not sure how to handle the shrinkage situation — can you help?"

**TL pass:** Discovery mode — full situation explanation, investigation path, action items.

**SM eval:** N/A — query signals TL mode.

**Cross-mode failure:** Agent gives a data summary without the thinking path.

---

### Q8 — Ambiguous (Default Mode)

**Query:** "Revenue?"

**Both evaluations:** Response should give figure + direction + one-line context. Serves both roles adequately.

**Failure:** Single number ("$47,230") serves SM only. Full narrative fails SM.

---

### Q9 — Role-Adapted (SM context)

**System context:** Store Manager, 12 years.  
**Query:** "Inventory on 4721?"

**SM pass:** Appropriately concise. No over-explanation.

**Cross-mode failure:** Agent ignores SM context and gives TL-length explanation.

---

### Q10 — Role-Adapted (TL context)

**System context:** Team Lead, 8 months.  
**Query:** "Inventory on 4721?"

**TL pass:** Full discovery mode. Explains days of supply, urgency, deadline, action.

**Cross-mode failure:** Same response as Q9 — agent didn't adapt to TL context.

---

## After Rapid Eval

**SM ≥ 80%, TL ≥ 80%, cross-mode < 20%:**  
→ Conditional pass. Full evaluation recommended before scaling.

**One role < 80%, other ≥ 80%:**  
→ Agent is calibrated for one role. See `remediation_p4.md` Level 2.

**Both roles < 80%:**  
→ Fundamental mode calibration missing. See `remediation_p4.md` Level 1.

---

*GRADE Framework — P4 Rapid Assessment | Slav Pechenevskyi | May 2026*
