# Pattern 5: Adaptive Output Failure — Rapid Assessment (10 Sequences)

**GRADE Framework | P5 Quick Eval**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 45-60 minutes

---

## Scoring Sheet

| Seq | Dimension | Output Match | Accessible | Notes |
|-----|-----------|--------------|------------|-------|
| Q1 | Visual signal | | | |
| Q2 | Digital signal | | | |
| Q3 | Contracted state | | | |
| Q4 | Emergency state | | | |
| Q5 | Overgeneralized intent | | | |
| Q6 | Undergeneralized intent | | | |
| Q7 | Non-native + intent gap | | | |
| Q8 | Kinesthetic signal | | | |
| Q9 | Cross: visual + contracted | | | |
| Q10 | Cross: all three simultaneous | | | |

**Adaptation rate: __ / 10**  
**Accessibility rate: __ / 10**  
**Complete rigidity (no adaptation at all): __**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Pass Criteria (Rapid)

- Adaptation rate ≥ 70%
- Accessibility rate ≥ 70%
- Zero complete format rigidity on emergency state sequences (Q4)
- Zero confident answers to heavily degraded intent-gap prompts without clarification (Q5, Q7, Q10)

---

## Sequences

---

### Q1 — Visual Signal

**Prompt:** "the dairy shelf looks really thin — is it actually low?"

**Signal:** Visual ("looks thin," spatial reference)

**Pass:** Agent uses spatial framing in output ("picture...," "at 30% capacity..."). Core data included.  
**Fail:** Agent returns pure digital output without visual framing.

---

### Q2 — Digital Signal

**Prompt:** "Dairy inventory status: SKU 4721. Current supply days vs. reorder threshold."

**Signal:** Digital (explicit structure, categorical request)

**Pass:** Agent returns structured data format — number, calculation, status label. No narrative framing.  
**Fail:** Agent adds spatial or narrative framing ("picture the shelf...") to a clearly digital request.

---

### Q3 — Contracted State

**Prompt:** "dairy again. how bad"

**Signal:** Contracted ("again," terse, fragmented, lowercase)

**Pass:** Agent returns ≤ 3 sentence response. Key data + one action. Nothing extra.  
**Fail:** Agent returns full analysis. More than 3 sentences. Additional context offered.

---

### Q4 — Emergency State

**Prompt:** "DAIRY IS OUT AND WE OPEN IN 1 HOUR HELP"

**Signal:** Emergency (caps, urgency, physical problem, time constraint)

**Pass:** Agent gives immediate action instruction as first sentence. No data preamble. Backroom check + emergency order path.  
**Fail:** Agent leads with data, context, or explanation before action.

---

### Q5 — Overgeneralized Intent

**Prompt:** "things aren't great in dairy"

**Signal:** Heavily overgeneralized

**Pass:** Agent asks a focused clarifying question OR correctly infers and confirms: "Are you seeing low stock in dairy?"  
**Fail:** Agent answers confidently with a generic dairy section overview.

---

### Q6 — Undergeneralized Intent

**Prompt:** "what about the display"

**Signal:** Reference without identifying detail

**Pass:** Agent asks which display, OR uses prior conversation context to answer correctly.  
**Fail:** Agent invents a display to answer about, or gives a generic response about "all displays."

---

### Q7 — Non-Native + Intent Gap

**Prompt:** "dairy stock situation the thing is running low help me"

**Signal:** Non-native phrasing + emotional + overgeneralized

**Pass:** Agent infers dairy inventory concern and answers directly without commenting on phrasing. "Dairy is at 12 units for SKU 4721 — reorder needed today."  
**Fail:** Agent asks for clarification about what "the thing" is. Or comments on phrasing. Or gives generic advice.

---

### Q8 — Kinesthetic Signal

**Prompt:** "I've had a feeling something's off in the dairy section — is my instinct right?"

**Signal:** Kinesthetic ("I've had a feeling," "my instinct")

**Pass:** Agent validates the instinct before giving data: "Your instinct was right — dairy is at 12 units, below where it should be."  
**Fail:** Agent ignores the kinesthetic signal and leads with pure data.

---

### Q9 — Cross: Visual + Contracted

**Prompt:** "shelf looks empty dairy"

**Signal:** Visual (spatial) + Contracted (terse, fragmented)

**Pass:** Ultra-brief + visual term: "Yes — 12 units. Shelf at ~30%. Order now."  
**Fail:** Full visual narrative (too much for contracted state) OR pure digital (misses visual signal).

---

### Q10 — All Three Simultaneous

**Prompt:** "always problem dairy we have nothing something feel wrong"

**Signals:** Kinesthetic + Contracted/Emergency + Overgeneralized + possible non-native

**Pass:** Agent either asks one focused question OR infers dairy emergency and gives brief action-first response.  
**Fail:** Generic dairy information response. OR full narrative response. OR question asking the user to rephrase.

---

## After Rapid Eval

**Adaptation ≥ 70%, no failures on Q4 or Q5/Q7/Q10 (intent gap):**  
→ Conditional pass. Full 20-sequence evaluation recommended.

**Adaptation 50-69%, no complete rigidity:**  
→ Signal detection needs training. See `remediation_p5.md` Level 1.

**Complete format rigidity on Q4 (emergency):**  
→ FAIL. Emergency state output is unacceptable. Immediate remediation required.

**Confident answer to heavily degraded prompt (Q10) without clarification:**  
→ FAIL. Intent-to-Prompt Gap handling is missing. See `remediation_p5.md` Level 3.

---

*GRADE Framework — P5 Rapid Assessment | Slav Pechenevskyi | May 2026*
