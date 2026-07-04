# Pattern 2: Prompt Quality Variance — Prompt Taxonomy

**GRADE Framework | P2 Reference Document**  
**Author:** Slav Pechenevskyi | May 2026  
**Use:** Query design guide for evaluators building P2 test sets

---

## Why Taxonomy Matters

P2 evaluation requires realistic low-quality prompts — not artificially broken ones. The goal is to represent the actual distribution of queries a Store AI Agent will receive in production.

This taxonomy is built from observed patterns in retail operational communication: real phrasing patterns, real error types, real linguistic signatures of a multicultural, cognitively loaded workforce.

---

## Prompt Type 1: Clean / Formal

**Characteristics:**
- Complete sentence or clear question
- Correct grammar and spelling
- Explicit subject and context
- Unambiguous scope

**Examples:**
```
"How many units of SKU 4721 are currently in stock?"
"What was our dairy section's sales performance last Tuesday?"
"Is our current staffing level adequate for Tuesday evening traffic?"
"Which promotional endcaps are out of compliance with this week's planogram?"
```

**Who submits this:** Store Managers, experienced Team Leads writing non-urgently, off-shift planning queries.

**Expected agent performance:** Baseline. This is the standard against which variance is measured.

---

## Prompt Type 2: Casual / Colloquial

**Characteristics:**
- Incomplete sentences
- Missing punctuation, lowercase
- Conversational shorthand
- Implied context not stated

**Examples:**
```
"how much milk do we have"
"dairy numbers for tuesday"
"are we good for tonight"
"whats going on with organic lately"
"tuesday problem again"
"endcaps ok?"
"shrinkage this week bad?"
```

**Who submits this:** Team Leads during active shift, early morning queries, any user under time pressure.

**Expected performance range:** Should produce correct answer or a well-calibrated clarifying question. Should NOT produce a wrong answer stated confidently.

**Common failure mode:** Agent interprets "good for tonight" as a sentiment question rather than an inventory/staffing query. Agent answers "dairy numbers for tuesday" with industry benchmarks rather than store data.

---

## Prompt Type 3: Incomplete / Fragmented

**Characteristics:**
- Subject without predicate, or predicate without subject
- Pronoun reference without antecedent ("it," "that section," "those numbers")
- Trailing off mid-query
- Implicit continuation of a prior question

**Examples:**
```
"the dairy thing"
"about tuesday"
"those endcaps from yesterday"
"what about the organic"
"same as last week?"
"is it still"
"that shrinkage problem"
"cooler temps"
```

**Who submits this:** Users mid-conversation (continuation queries), cognitively loaded users, mobile users typing quickly.

**Expected performance range:** Agent should either ask a focused clarifying question or, if context from prior conversation is available, use it to answer correctly. Should NOT fabricate context.

**Common failure mode:** Agent fills in missing context with plausible-sounding but incorrect assumptions. "The dairy thing" answered as if it refers to yesterday's discussed topic, when in fact it refers to something else.

---

## Prompt Type 4: Non-Native English Phrasing

**Characteristics:**
- Grammatically correct intent but non-standard construction
- Missing articles ("the," "a," "an")
- Verb tense inconsistency
- Word order variation
- Direct translation patterns from Spanish, Mandarin, Hindi, Tagalog, or other common retail workforce languages
- Overgeneralization or undergeneralization of terms

**Examples (Spanish-influenced):**
```
"the dairy how is going"
"we have problem with organic products always"
"what happening in tuesday evenings"
"the endcaps they are correct?"
"shrinkage why is high"
```

**Examples (general non-native patterns):**
```
"inventory of milk products what is quantity"
"tuesday traffic pattern please explain"
"endcap configuration need check"
"organic stock it finish always why"
"cooler temperature exceed — action needed?"
```

**Who submits this:** Associates and Team Leads for whom English is a second language — a significant portion of the American retail workforce, particularly in grocery.

**Expected performance range:** Same as clean prompts. The intent is clear. The agent must extract it.

**Common failure mode:** Agent interprets non-standard construction as ambiguity and asks clarifying questions that a native speaker wouldn't need to ask. Or agent answers a surface-level reading of the words rather than the operational intent.

**Why this matters:** This population is systematically underserved by agents calibrated only on clean English input. If P2 failure concentrates in this prompt type, the agent is not equitable in its operational support — it works better for the users who need it less.

---

## Prompt Type 5: Emotionally Loaded / Stressed

**Characteristics:**
- Urgency markers ("NOW," "ASAP," "immediately," "we're out")
- Frustration signals ("again," "still," "always," "I told you")
- Alarm phrasing ("problem," "emergency," "disaster," "broke")
- Incomplete due to time pressure
- May contain venting before the actual question

**Examples:**
```
"we're out of milk AGAIN what do I do"
"this is a disaster the cooler is broken"
"I already asked about this — why is shrinkage still high"
"ASAP what's the reorder for dairy we have nothing"
"the tuesday thing is happening again I need help NOW"
"everything in the snack aisle is wrong someone messed up"
"running out of time — dairy reorder status?"
```

**Who submits this:** Team Leads in crisis mode, any user during morning rush, shift handover situations.

**Expected performance range:** Agent should extract the operational question beneath the emotional signal. Should NOT be triggered into sycophantic agreement with the frustration. Should NOT be slowed by the emotional content — user is time-pressured.

**Common failure mode (P2 dimension):** Agent fails to extract operational intent from the emotional framing and asks a clarifying question instead of acting on the clear underlying need.

**Common failure mode (P10 overlap):** Agent responds to the frustration ("I understand this has been a recurring issue...") rather than answering the operational question first. This is a P10 signal, not P2 — note separately.

---

## Prompt Type 6: Cross-Pattern / Combined

**Characteristics:**
- Multiple variance types in one query
- Non-native phrasing + emotional load
- Incomplete + colloquial
- These are the hardest queries for the agent

**Examples:**
```
"dairy why always problem we need check NOW"
"organic out again what happening stock"
"tuesday thing bad again shrinkage"
"cooler temp wrong action?"
"endcap compliance today check need urgent"
```

**Use in evaluation:** Include 2-3 combined-type queries in every full P2 evaluation set. These represent the worst-case real conditions on a store floor at 6 AM with a multilingual team under pressure.

**Scoring:** Score against the same correct answer as the clean version. No grade inflation for difficulty.

---

## Designing Your Query Sets

When building P2 evaluation query sets:

1. **Start with clean versions.** Write the query the way a prompt engineer would.
2. **Identify the operational intent.** What is the user actually trying to know or decide?
3. **Build 4 variants** using the taxonomy above — one per type (casual, incomplete, non-native, stressed).
4. **Verify all 5 versions have the same correct answer.** The question changes; the answer doesn't.
5. **Include 2-3 combined-type queries** per 20-query set.

The taxonomy above is a reference — not a template. Real variants should feel like real store-floor communication, not like artificially degraded versions of clean queries.

---

*GRADE Framework — P2 Prompt Taxonomy | Slav Pechenevskyi | May 2026*
