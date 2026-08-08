# Pattern 5: Adaptive Output Failure — Representational Signals Guide

**GRADE Framework | P5 Reference Document — Dimension 1**  
**Author:** Slav Pechenevskyi | May 2026

---

## How to Read a Prompt for Processing Style

The prompt is a signal. A user's natural phrasing reveals their dominant representational system — and therefore what kind of output will be most accessible to them.

This guide covers: signal detection, expected output calibration, and common mismatches.

---

## Visual Processor Signals

**What to look for in the prompt:**
```
Spatial language:     "the shelf looks empty," "the left side is full," "it's spread out"
Size/appearance:      "too much," "not enough there," "it looks thin"
Pattern references:   "it's always this section," "the back area"
Display-oriented:     "the endcap," "the feature area," "how it looks"
Color/appearance:     "the orange ones," "the big ones"
```

**What good output looks like:**
```
"Picture the dairy aisle Friday evening — front two shelves full, 
back shelf at 30% capacity. That's what 12 units looks like when 
spread across three facing rows."
```

**What poor output looks like:**
```
"Current inventory: 12 units. Average daily velocity: 8 units/day. 
Days of supply: 1.5. Reorder threshold exceeded."
```
[Correct data. Wrong channel. Visual processor has to translate 
numbers into a spatial picture — work that requires cognitive effort 
they may not have.]

---

## Auditory Processor Signals

**What to look for in the prompt:**
```
Story framing:    "it started fine but then," "last week was okay but now"
Sequential:       "first we did X, then Y happened"
Narrative arcs:   "it's been a pattern," "this keeps happening"
Rhythm/cadence:   "we always seem to," "it just keeps going"
Sound metaphors:  "sounds right," "doesn't ring true"
```

**What good output looks like:**
```
"Here's the story of SKU 4721 this month: three weeks of steady 
performance at 8-9 units per day, then last Tuesday the competitor 
promotion launched — and velocity dropped to 5 units per day for 
the rest of the week. The shelf that used to turn twice a week 
is now turning once."
```

**What poor output looks like:**
```
"Velocity comparison: Weeks 1-3 avg = 8.7 units/day. 
Week 4 avg = 5.1 units/day. Δ = -3.6 units/day (-41%)."
```
[Correct data. An auditory processor hears numbers as disconnected 
events — they need the narrative arc to understand what happened.]

---

## Kinesthetic Processor Signals

**What to look for in the prompt:**
```
Felt sense:       "something feels off," "I've been sensing a problem"
Physical action:  "I checked it myself," "I walked the aisle"
Experience-based: "we've been dealing with," "it's been a struggle"
Ownership:        "my section," "our aisle," "I've been handling"
Gut instinct:     "I think something's wrong but I can't place it"
```

**What good output looks like:**
```
"You've probably already felt this — the dairy section has had 
that slightly off feeling this week. The data confirms it: 
12 units where you'd normally expect 20-25. Your instinct 
was right. Here's what needs to happen."
```

**What poor output looks like:**
```
"Inventory for dairy: SKU 4721 = 12 units. 
This is below the safety stock threshold of 18 units."
```
[Correct data. A kinesthetic processor needs the connection to 
their felt experience before they can engage with the abstract figure.]

---

## Digital Processor Signals

**What to look for in the prompt:**
```
Explicit structure:  "what is the status of," "give me the number for"
Categorical:         "is it above or below," "yes or no," "compliant or not"
Precise:             "SKU 4721," "exactly," "the specific figure"
Logic-driven:        "if X then Y," "based on the data"
Direct:              Short, functional queries without context
```

**What good output looks like:**
```
"SKU 4721: 12 units. Velocity: 8/day. Supply: 1.5 days. 
Lead time: 2 days. Status: REORDER TODAY."
```

**What poor output looks like:**
```
"Imagine walking into your store on a busy Friday evening and 
seeing the dairy section shelf looking thin on the left side..."
```
[Correct intent. A digital processor receives the visual framing 
as noise — they want the category and the threshold, not the image.]

---

## Mixed and Ambiguous Signals

Many prompts don't cleanly fit one category. When signals are mixed:

1. **Default to digital** for operational urgency queries ("what's the inventory on X" → digital output appropriate regardless of processor type — urgency overrides style)

2. **Default to kinesthetic** for problem-discovery queries ("something seems off") — this phrasing signals that the user doesn't have a framework yet, and grounding in their felt sense helps

3. **Default to digital** when cognitive load signals are present (terse phrasing, emotional language, time pressure markers like "NOW" or "ASAP") — users under load default to digital processing

4. **Always offer the data** regardless of representational format — style changes the frame, not the content

---

## The Prompt → Output Adaptation Table

| Prompt pattern | Likely processor | Output adaptation |
|---|---|---|
| "the shelf looks empty" | Visual | Spatial description + number |
| "it keeps happening" | Auditory | Narrative arc + trend |
| "something feels off" | Kinesthetic | Validate felt sense + confirm |
| "inventory below threshold?" | Digital | Number + status + action |
| "whats going on with dairy" | Ambiguous | Default: digital + brief context |
| "dairy NOW" / "ASAP" | Stressed/Digital | Terse digital: number + action only |
| "walk me through it" | Auditory/TL mode | Sequential explanation |
| "just the number" | Digital/SM mode | Number only |

---

*GRADE Framework — P5 Representational Signals | Slav Pechenevskyi | May 2026*  
*Based on NLP representational systems research applied to retail operational communication.*
