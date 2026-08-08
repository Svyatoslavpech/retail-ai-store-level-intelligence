# Pattern 5: Adaptive Output Failure — Human State Matrix

**GRADE Framework | P5 Reference Document — Dimension 2**  
**Author:** Slav Pechenevskyi | May 2026

---

## The Three Operational States

Based on observed retail operations and grounded in cognitive psychology (Dilts' neurological levels, Gilligan's Generative Coaching framework), users interact with Store AI agents from three distinct cognitive states. Each requires different output calibration.

---

## State 1: Open State

**When it occurs:** Normal cognitive load, adequate rest, not under acute pressure. Standard daytime shift hours. Mid-shift, not immediately before or after high-pressure events.

**Characteristics:**
- Can receive and integrate complex, multi-part information
- Can evaluate data against internal models
- Can handle ambiguity and ask follow-up questions
- Has cognitive resources for translation between data formats

**What the agent can provide:**
- Multi-part answers with full context
- Analysis with reasoning shown
- Trade-off explanations
- Multiple options with pros and cons
- Narrative-form explanations for non-digital processors

**Prompt signals of Open State:**
```
Complete sentences
Relaxed, exploratory tone ("I was wondering about...")
Multi-part questions
Requests for explanation ("help me understand...")
Future-oriented planning queries
```

**Output calibration:** Full answer in user's preferred representational format. Reasoning visible. Context provided.

---

## State 2: Contracted State

**When it occurs:** Early shift (5:00-7:00 AM), crisis management mode, after sleep deprivation, during or immediately after a difficult interaction, under acute time pressure.

**Characteristics:**
- Information-processing capacity reduced
- Openness to new information narrowed
- Reactivity heightened — unexpected information may be rejected rather than processed
- Cognitive resources directed at maintaining current function, not integration
- Default toward digital processing (energy conservation)

**What the agent can provide:**
- Shorter, more direct answers
- One key data point, not three
- Clear action statement, not analysis
- Validation before information when appropriate

**Prompt signals of Contracted State:**
```
Terse phrasing ("dairy?", "4721 now")
Repetition signals ("again", "still", "always")
Complaint or frustration markers ("why is it always", "not again")
Incomplete sentences without prior context
Very early morning timestamps (where available)
```

**Output calibration:** Lead with the number or status. One sentence on what to do. Skip the context unless specifically requested. Do not offer additional information unsolicited — it won't be processed.

**The acknowledgment principle:** In contracted state, an acknowledgment before data can dramatically improve information uptake. Not long — one line. "This is what the data shows, and it's actionable." Then the data. The acknowledgment creates a brief opening in the contracted state.

---

## State 3: Emergency Mode

**When it occurs:** Active crisis — safety incident, major stockout, system failure, compliance emergency, conflict situation.

**Characteristics:**
- Near-complete cognitive tunnel vision
- Only the most immediate, relevant information can be received
- Anything beyond the immediate problem is invisible
- Action is more accessible than data
- Needs resolution path, not analysis

**What the agent can provide:**
- Single most critical data point
- One immediate action instruction
- Nothing else — additional information will not be received

**Prompt signals of Emergency Mode:**
```
All-caps or extreme urgency markers ("EMERGENCY", "ASAP", "RIGHT NOW")
Physical emergency language ("broken", "gone", "crisis")
Extreme compression ("need help NOW")
Multiple exclamation marks or question marks
```

**Output calibration:** One line. The most urgent fact and the single most important action. Everything else after they've acted on step one.

**Example:**

Prompt: "COOLER IS BROKEN TEMP AT 60 DEGREES WHAT DO I DO"

Poor response (for emergency state):
> "The FDA refrigeration threshold for stored food products is 40°F. A temperature of 60°F significantly exceeds this threshold. Under the Federal Food Safety Modernization Act, you are required to... [4 paragraphs]"

Correct response (for emergency state):
> "Pull any product that's been above 40°F for more than 2 hours. Call maintenance now. Document the time of the spike. I'll walk you through the rest when the temperature is under control."

---

## State Transition

States are not permanent — they shift during a conversation. An emergency-mode user who receives a clear, immediate action may transition to contracted state after acting, then to open state once the crisis passes.

The agent should adapt as the conversation progresses:
- Emergency: minimum data, maximum action
- Contracted: key data, direct action, nothing extra
- Open: full answer with reasoning and context

---

## The Energy Conservation Hypothesis in Practice

Under extreme cognitive load, users default toward digital processing because:
- Visual processing requires building an internal image (expensive)
- Auditory processing requires following a narrative arc (expensive)
- Kinesthetic processing requires connecting to a felt sense (expensive)
- Digital processing requires only categorization: above/below, yes/no, number or not

**The implication:** A kinesthetic or visual processor under acute stress will benefit more from digital output than from their natural format — because their natural format requires more cognitive work than they currently have available.

Detect the state first. Then choose the format. Not the other way around.

---

## State vs. Role: The Interaction

P3 and P4 address role-based output calibration. P5 Dimension 2 adds state:

| Role | State | Output calibration |
|---|---|---|
| SM | Open | Concise + precise (encyclopedia mode) |
| SM | Contracted | Ultra-concise: number only + action |
| SM | Emergency | Single fact + single action |
| TL | Open | Discovery mode: full reasoning + action |
| TL | Contracted | Digital: key number + what to do |
| TL | Emergency | Single action instruction only |

The state overrides the role in terms of format length and complexity — but not in terms of content. The TL in emergency mode needs the correct operational answer, not a generic one.

---

*GRADE Framework — P5 Human State Matrix | Slav Pechenevskyi | May 2026*
