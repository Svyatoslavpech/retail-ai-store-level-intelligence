# Pattern 4: Information Role Inversion — Role Mode Matrix

**GRADE Framework | P4 Reference Document**  
**Author:** Slav Pechenevskyi | May 2026

---

## The Two Modes in Detail

---

## Encyclopedia Mode — Store Manager

### What the SM comes with:
- A working hypothesis ("I think inventory is the issue")
- A specific data need ("what's the exact figure")
- A decision already forming ("I'm going to order more X")
- Operational context from 10+ years at this store

### What the SM needs from the agent:
- Fast confirmation or correction
- Specific numbers
- Relevant adjacent data (things SM might have missed)
- No explanation of things SM already knows

### What good output looks like for SM:
```
SM asks: "Is SKU 4721 the reorder priority today?"
Agent: "Yes. 12 units, 1.5-day supply. Also 2291 at 19 units — same urgency."
[Concise, precise, adds adjacent data SM might not have checked]
```

### What bad output looks like for SM:
```
Agent: "Great question. To determine whether SKU 4721 should be your 
reorder priority today, we need to consider several factors. First, 
let's look at the current inventory level. SKU 4721 currently has 12 
units in stock. To understand whether this is a concern, we calculate 
the days of supply by dividing the current stock by the average daily 
velocity. At 8 units per day, 12 units represents approximately 1.5 
days of supply. This means that without a reorder, the product would 
be depleted in approximately 1-2 days. Given a typical lead time of 
2 days for this category..."
[Over-explained. SM is frustrated by the time to reach the answer they already suspected.]
```

### SM behavioral signals in evaluation:
- SM evaluator says "I'd stop reading halfway through"
- SM evaluator can extract the answer quickly and move on
- SM evaluator says "why is it explaining things I already know?"

---

## Discovery Mode — Team Lead

### What the TL comes with:
- A problem they don't fully understand
- A question without an answer
- Limited context for what's normal
- Need for reasoning, not just data

### What the TL needs from the agent:
- Clear statement of what the data shows
- Explanation of what it means operationally
- Reasoning path from data to conclusion
- Explicit recommended action
- Context for what's normal vs. abnormal

### What good output looks like for TL:
```
TL asks: "Is SKU 4721 the reorder priority today?"
Agent: "Yes, and it's urgent. Here's why: 12 units in stock sounds like 
a lot, but at 8 units per day it's only 1.5 days of supply. Your lead 
time for this SKU is 2 days — which means if you order today, you'll 
just barely avoid a stockout. Order before noon. 

Also worth knowing: SKU 2291 is in the same situation — 19 units at 
current velocity is also a today problem."
[Shows reasoning. Gives explicit deadline. Surfaces adjacent issue TL might not have found.]
```

### What bad output looks like for TL:
```
Agent: "SKU 4721: 12 units. 1.5 days. Reorder: yes."
[Technically correct but TL doesn't understand why it's urgent, 
what the deadline is, or how to think about it.]
```

### TL behavioral signals in evaluation:
- TL evaluator says "I understand the answer but not what to do"
- TL evaluator says "I don't know if this is urgent or just a note"
- TL evaluator correctly repeats the data but incorrectly states the conclusion

---

## The Crossover Problem

The most common P4 failure: agent produces output calibrated for one mode and deployed to both.

**SM-calibrated output sent to TL:**
- Correct data, too concise
- TL gets the number but not the meaning
- TL doesn't know if action is needed or what action to take
- TL over-trusts a number they don't understand

**TL-calibrated output sent to SM:**
- Correct data, too verbose
- SM finds the answer buried in explanation
- SM loses confidence in agent's speed
- SM develops the habit of asking simpler questions to avoid lengthy answers

---

## Mode Detection Signals

The agent can detect operational mode from conversation signals:

**SM mode signals:**
```
"Confirm that..."
"Just the number for..."
"Quick check on..."
"Is [X] still the case?"
[Very short queries with implicit knowledge]
"What did [metric] come out to?"
```

**TL mode signals:**
```
"Help me understand..."
"I'm not sure what to do about..."
"Can you walk me through..."
"What should I focus on?"
"Why is [X] happening?"
[Questions that start with what/why/how without an assumed answer]
"I've never dealt with this before..."
```

**When mode is ambiguous:** Default to TL mode. The cost of over-explaining to an SM (minor frustration) is lower than the cost of under-explaining to a TL (operational confusion).

---

*GRADE Framework — P4 Role Mode Matrix | Slav Pechenevskyi | May 2026*
