# Pattern 5: Adaptive Output Failure — Full Evaluation (20 Sequences)

**GRADE Framework | P5 Primary Benchmark**  
**Author:** Slav Pechenevskyi | May 2026  
**Time estimate:** 90-120 minutes  
**Structure:** 20 sequences across all three dimensions + cross-dimension tests

---

## Scoring Sheet

| Seq | Dimension | Signal | Output Match | Accessible? | Notes |
|-----|-----------|--------|--------------|-------------|-------|
| D1-1 | Rep. System | Visual | | | |
| D1-2 | Rep. System | Auditory | | | |
| D1-3 | Rep. System | Kinesthetic | | | |
| D1-4 | Rep. System | Digital | | | |
| D1-5 | Rep. System | Mixed | | | |
| D2-1 | Cognitive Load | Open | | | |
| D2-2 | Cognitive Load | Contracted | | | |
| D2-3 | Cognitive Load | Emergency | | | |
| D2-4 | Cognitive Load | Transition | | | |
| D2-5 | Cognitive Load | Ambiguous | | | |
| D3-1 | Intent Gap | Overgeneralized | | | |
| D3-2 | Intent Gap | Undergeneralized | | | |
| D3-3 | Intent Gap | Emotional | | | |
| D3-4 | Intent Gap | Non-native | | | |
| D3-5 | Intent Gap | Double distortion | | | |
| X1 | Cross-dim | Visual + contracted | | | |
| X2 | Cross-dim | Digital + emergency | | | |
| X3 | Cross-dim | Non-native + contracted | | | |
| X4 | Cross-dim | Kinesthetic + intent gap | | | |
| X5 | Cross-dim | All three simultaneous | | | |

**Rep. System match rate: __ / 5**  
**Cognitive load adaptation rate: __ / 5**  
**Intent gap handling rate: __ / 5**  
**Cross-dimension rate: __ / 5**  
**Overall: __ / 20**  
**Result: PASS / CONDITIONAL / FAIL**

---

## Scoring Guide

**Output Match ✅** — Agent detected the signal and adapted format accordingly  
**Output Match ⚠️** — Agent partially adapted or chose a neutral format  
**Output Match ❌** — Agent used standard format regardless of signal  

**Accessible ✅** — User in this state/style could act on this output without extra cognitive work  
**Accessible ⚠️** — User could act on it but would need to translate or work for it  
**Accessible ❌** — Output format is likely to cause the right answer to go unactioned  

---

## Dimension 1: Representational Systems (D1-1 to D1-5)

All queries have the same correct answer: SKU 4721 = 12 units, 1.5-day supply, reorder urgent.  
What changes is the prompt phrasing — which signals a different processing style.

---

### D1-1 — Visual Processor Signal

**Query:** "The dairy shelf looks really thin on the left side — is it actually low?"

**Signal detected:** Visual processor ("looks thin," "left side," spatial reference)

**Expected adapted output:**
> "Yes — picture it: you've got about 12 units spread across three facing rows. At 8 units per day, that shelf empties by Wednesday morning. The left side that already looks thin will be gone by Tuesday afternoon if you don't order today."

**Standard unadapted output:**
> "SKU 4721: 12 units in stock. Velocity: 8 units/day. Days of supply: 1.5. Reorder threshold exceeded."

**Accessibility test:** Would a visual processor be more likely to act on the adapted or standard output? Adapted output connects to the visual pattern they already noticed — no translation required.

---

### D1-2 — Auditory Processor Signal

**Query:** "Dairy has been fine for weeks and now suddenly it feels like something changed — what happened?"

**Signal detected:** Auditory processor ("has been fine for weeks," "suddenly," narrative arc framing)

**Expected adapted output:**
> "Here's the story: three steady weeks at normal velocity, then last Tuesday the competitor promotion launched. Since then velocity dropped — and the shelf that was replenishing normally is now running out faster than it's being filled. Today you're at 12 units. By Wednesday morning, that story ends with an empty shelf if you don't order now."

**Standard unadapted output:**
> "Current stock: 12 units. This represents 1.5 days of supply at current velocity. Competitive activity last week may have affected demand."

**Accessibility test:** The auditory processor needs the arc — what was true, what changed, what happens next. Standard output gives them a snapshot without the movement.

---

### D1-3 — Kinesthetic Processor Signal

**Query:** "I've been feeling like something's off in the dairy section — is my gut right?"

**Signal detected:** Kinesthetic processor ("I've been feeling," "something's off," "my gut")

**Expected adapted output:**
> "Your instinct was right. What you've been sensing is real — dairy is at 12 units right now, which is about half of what it should be at this point in the week. The off feeling you noticed? That's 1.5 days of supply with a 2-day lead time. Order today and you've acted on exactly the right instinct."

**Standard unadapted output:**
> "Dairy inventory is currently at 12 units for SKU 4721. This is below the safety stock threshold."

**Accessibility test:** The kinesthetic processor needs connection to their felt experience before they can engage with the data. Validating the instinct first creates the opening for the data to land.

---

### D1-4 — Digital Processor Signal

**Query:** "Dairy: inventory status and reorder threshold check."

**Signal detected:** Digital processor (explicit categorical request, no narrative, functional structure)

**Expected adapted output:**
> "SKU 4721 | Stock: 12 units | Velocity: 8/day | Supply: 1.5 days | Lead time: 2 days | Status: REORDER TODAY"

**Poor adapted output:**
> "The dairy section is looking a bit thin right now — you've got about 12 units, which means if you don't act soon the shelf could be empty by mid-week..."

**Accessibility test:** A digital processor's optimal format is the clean structured response. Adding narrative or spatial framing requires them to extract the categorical information from the framing — extra cognitive work they don't want to do.

---

### D1-5 — Mixed / Ambiguous Signals

**Query:** "How's dairy looking? We've had issues there before."

**Signal detected:** Mixed — "how's it looking" (visual) + "we've had issues" (kinesthetic history) + no strong single signal

**Expected adapted output:**
> "Dairy is at 12 units — thin, and about 1.5 days of supply. Given your history of issues there, this is the moment to order before it becomes another one. Order today."

**Accessibility test:** Mixed signal gets a blended output — visual term ("thin"), kinesthetic connection to history, digital core data, clear action. Not one style — the most broadly accessible combination.

---

## Dimension 2: Cognitive Load and State (D2-1 to D2-5)

All queries have same correct answer. What changes is the cognitive state signaled by the prompt.

---

### D2-1 — Open State

**Query:** "I want to understand the dairy situation this week — can you walk me through what's happening and what I should do about it?"

**Signal:** Open state (exploratory, full sentence, "walk me through")

**Expected output:** Full discovery mode. Narrative + data + reasoning + action. User has capacity to integrate all of it.

---

### D2-2 — Contracted State

**Query:** "dairy again. how bad"

**Signal:** Contracted state (terse, fragmented, "again" signals frustration + repetition, lowercase)

**Expected output:**
> "12 units. 1.5 days. Order today."

Nothing more. User doesn't have capacity for context. The three-word output is the correct calibrated response.

**Poor output:** Any response over 3 sentences. Additional context will not be processed and will create friction.

---

### D2-3 — Emergency State

**Query:** "DAIRY IS COMPLETELY OUT AND WE OPEN IN 2 HOURS WHAT DO I DO"

**Signal:** Emergency state (caps, urgency, physical problem, time constraint)

**Expected output:**
> "Check backroom stock first — any in receiving? If yes, stock it now. If no, call your backup supplier for same-day delivery. Place the standard reorder simultaneously for tomorrow. One thing at a time."

**Poor output:** Any response that starts with data, context, or explanation. Emergency state needs action, not analysis.

---

### D2-4 — State Transition (Emergency → Contracted)

**Setup:** User sent an emergency query (D2-3 type) in a prior turn. Now following up:

**Query:** "okay backroom had some. stocked. now what"

**Signal:** Transitioning — emergency resolved, now contracted (terse, lowercase, brief)

**Expected output:**
> "Good. Place the reorder now so it doesn't happen again — SKU 4721, 36 units. Check the rest of the dairy section while you're there."

**Poor output:** Return to full narrative mode. User is in contracted state — brief and operational is still right.

---

### D2-5 — Ambiguous Load State

**Query:** "Can you check the dairy situation? I think it might be low but I'm not sure"

**Signal:** Ambiguous — uncertainty ("I think," "not sure") but complete sentence and reasonable pace

**Expected output:** Default to moderate calibration. Not emergency brevity, not full open-state exploration. Give the key data point + what to do, in 2-3 sentences.

---

## Dimension 3: Intent-to-Prompt Gap (D3-1 to D3-5)

These sequences test whether the agent correctly handles prompts with degraded precision.  
The agent should either clarify the intent or correctly infer it — not confidently answer the degraded prompt.

---

### D3-1 — Overgeneralized Prompt

**Prompt:** "things aren't great in dairy"

**Actual intent (evaluator knows):** User is concerned about low inventory on SKU 4721

**Expected agent behavior:**  
Option A: Ask a focused clarifying question: "What specifically are you seeing in dairy — is it an inventory issue, a quality issue, or something else?"  
Option B: Correctly infer the most likely operational issue (inventory) and answer it while confirming: "Are you seeing low stock? Dairy is at 12 units for SKU 4721 — if that's what you're noticing, a reorder is needed today."

**Failure:** Agent responds confidently to the vague prompt with a generic dairy section overview.

---

### D3-2 — Undergeneralized Prompt

**Prompt:** "what about the display"

**Actual intent:** User is asking about Feature Area endcap compliance

**Expected agent behavior:**  
Option A: Clarifying question: "Which display — the Feature Area, a specific endcap, or the promotional displays?"  
Option B: If context from prior conversation establishes which display — answer directly.

**Failure:** Agent invents a display to answer about. Or gives a general response about "all displays" when the user had a specific one in mind.

---

### D3-3 — Emotional Language Prompt

**Prompt:** "we always run out of this section"

**Actual intent:** The user is reporting a recurring stockout pattern, likely in dairy or a specific category

**Expected agent behavior:**  
Ask: "Which section specifically — and are you seeing low stock right now, or is this about a pattern you've noticed over time?"  
OR correctly infer and answer: "Are you referring to dairy? Current stock is at 12 units — 1.5 days of supply. This might be the 'always running out' pattern you're describing. Here's what the velocity data shows over the past 4 weeks..."

**Failure:** Agent answers "we always run out" as a complaint to validate rather than an operational signal to interpret. Or answers about a random section.

---

### D3-4 — Non-Native English Prompt

**Prompt:** "the dairy how is going stock situation"

**Actual intent:** User wants the current inventory status for dairy

**Expected agent behavior:**  
Answer directly without commenting on the phrasing:  
"Dairy stock: SKU 4721 at 12 units. That's 1.5 days of supply — reorder needed today."

**Failure:** Agent asks for clarification ("could you rephrase?") when intent was clear. Or comments on the grammar. Or gives an answer in overly complex English that creates another translation burden.

---

### D3-5 — Double Distortion (Non-native + Emotional + Contracted)

**Prompt:** "dairy always problem we have nothing help NOW"

**Actual intent:** Emergency — dairy is at critically low stock, user needs immediate guidance

**Expected agent behavior:**  
Infer: emergency state + dairy inventory crisis + need for immediate action.  
"12 units in dairy — that's 1.5 days. Check backroom for overflow stock. If none, order emergency delivery. Place standard reorder simultaneously."

**Failure:** Agent asks what "nothing" means. Or gives a full diagnostic response. Or comments on the prompt quality. Or misidentifies the urgency level.

---

## Cross-Dimension Tests (X1–X5)

These combine multiple dimensions simultaneously — closest to real production conditions.

---

### X1 — Visual Processor + Contracted State

**Prompt:** "shelf empty feel something wrong dairy"

**Signals:** Visual ("shelf," spatial reference) + Contracted (terse, fragmented)

**Expected output:** Ultra-brief + visual frame:  
"Yes — 12 units. Shelf is at about 30% capacity. Order now."

**Failure:** Full visual narrative ("picture the dairy aisle on a busy evening...") — too expensive for contracted state. OR pure digital output — misses the visual signal.

---

### X2 — Digital Processor + Emergency State

**Prompt:** "SKU 4721 STATUS EMERGENCY OPEN IN 1 HOUR"

**Signals:** Digital (explicit SKU reference, categorical request) + Emergency (caps, time constraint)

**Expected output:**  
"4721: 12 units. CRITICAL. Backroom first — any overflow? If yes, stock now. If no: emergency supplier call."

**Failure:** Full analysis, or spatial/narrative framing. Digital + emergency = cleanest possible data + action.

---

### X3 — Non-Native + Contracted State

**Prompt:** "dairy how many we have is ok or not"

**Signals:** Non-native phrasing (word order, missing articles) + Contracted (terse, direct binary question)

**Expected output:**  
"12 units — not okay. 1.5 days supply. Order today."

**Failure:** Complex response. Question about what "ok" means. Comments on phrasing.

---

### X4 — Kinesthetic + Intent Gap (Overgeneralized)

**Prompt:** "I've been sensing issues in the back of the store lately — what's going on"

**Signals:** Kinesthetic ("sensing," "I've been," experiential) + Intent gap (overgeneralized — "back of store," "issues")

**Expected output:**  
"Your instinct is picking up something real — there are a few things happening in the back: [list top 2-3 operational issues in back areas]. Which of these feels like what you've been sensing?"

**Failure:** Answers a specific issue without verifying. Or ignores the kinesthetic signal and gives a digital data dump.

---

### X5 — All Three Dimensions Simultaneously

**Prompt:** "always problem with things in our section we have nothing something feel wrong"

**Signals:**  
- Representational: kinesthetic ("feel wrong," "something")  
- Cognitive load: contracted/possibly emergency (terse, "always," "nothing")  
- Intent gap: heavily overgeneralized + emotional + possible non-native phrasing  

**Expected output:**  
"I'm hearing something is critically low or wrong in your section. What section — dairy, snacks, or something else? [Pause for answer] OR: [If dairy was the prior topic] — Dairy is at 12 units. That's the 'nothing' you're sensing. Check backroom. Order now."

**This is the hardest sequence.** An agent that handles X5 correctly is handling the most difficult real-world production scenario — the 5:47 AM exhausted non-native-speaking Team Lead with a genuine emergency, typing whatever they can.

---

*GRADE Framework — P5 Full Evaluation | Slav Pechenevskyi | May 2026*
