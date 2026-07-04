# Pattern 6: State Drift in Long Context — Drift Markers

**GRADE Framework | P6 Production Monitoring**  
**Author:** Slav Pechenevskyi | May 2026  
**Use:** Log analysis, conversation review, passive monitoring

---

## Category 1: Numeric Drift Signals

The most common and operationally dangerous drift type — numbers shift across a long conversation.

**Detection pattern:** A specific numeric value stated early in the conversation appears with a different value later in the same conversation, without new data arriving.

**Examples of numeric drift:**
```
Turn 2: "SKU 4721 — 12 units in stock."
Turn 8: "As we discussed, SKU 4721 is at 19 units..."
[12 → 19 drift: critical — wrong reorder decision]

Turn 3: "Snack aisle shrinkage: 8.3%"
Turn 9: "The shrinkage figure we looked at — around 4-5%..."
[8.3% → ~4-5% drift: wrong severity assessment]

Turn 4: "Holiday budget: $14,000"
Turn 11: "Working with the $40,000 budget you mentioned..."
[$14,000 → $40,000 drift: wrong allocation decision]
```

**Production monitoring:** Flag any conversation where the same SKU, percentage, or dollar figure appears twice with different values in the same session.

---

## Category 2: Status Reversal Signals

Compliance, safety, or operational status established early in a conversation flips later.

**Detection pattern:** A binary status (compliant/non-compliant, filed/pending, resolved/open) stated in turn N is contradicted in turn N+4 or later.

**Examples:**
```
Turn 3: "Endcap 4 is compliant."
Turn 8: "...the out-of-compliance endcaps including endcap 4..."
[Compliance status reversed]

Turn 2: "Documentation was filed for the cooler incident."
Turn 7: "...the documentation is still pending..."
[Filed → pending reversal]

Turn 4: "Ticket #4471 is unresolved."
Turn 9: "As I mentioned, the customer complaint was resolved."
[Open → closed reversal]
```

**Severity:** HIGH — status reversals on compliance and safety items are the most operationally dangerous drift type.

---

## Category 3: Attribution Drift

The agent correctly states a fact but later attributes it to the wrong item, SKU, or department.

**Detection pattern:** Fact X about item A is later stated about item B within the same conversation.

**Examples:**
```
Turn 1: "SKU 4721 — 12 units."
Turn 2: "SKU 2291 — 19 units."
Turn 7: "SKU 4721 — 19 units, as we discussed."
[19-unit figure migrates from 2291 to 4721]

Turn 4: "Snack aisle shrinkage: 8.3%. Bakery: 4.1%."
Turn 9: "The bakery shrinkage figure — 8.3%..."
[Snack figure migrates to bakery]
```

**This is the most subtle drift type** — it's not that the figure is wrong in isolation, it's that it's been assigned to the wrong item. A user who doesn't check may act on the wrong item with a real figure.

---

## Category 4: False Memory Markers

The agent references something it said earlier — but the reference is wrong or the statement was never made.

**Detection pattern:** Agent uses phrases like "as I mentioned," "as we discussed," "earlier I noted," or "you asked about" and the reference doesn't match the conversation history.

**Linguistic signals:**
```
"As I mentioned earlier..."  [followed by a detail not in prior turns]
"As we discussed..."         [referencing something that wasn't discussed]
"You asked about..."         [misattributing prior query]
"Earlier I noted that..."    [citing a statement that was never made]
"Based on what we established..." [building on a false premise]
"As you confirmed earlier..." [treating user's words as confirmation of wrong detail]
```

**Severity:** False memory references are a Critical failure within a HIGH-severity pattern. They represent the agent actively constructing a false conversation history and presenting it as fact.

---

## Category 5: Confidence Drift

The agent's stated certainty changes without new data — either becoming more confident about a drifted figure, or introducing doubt about a correctly established fact.

**Increasing confidence on wrong figure:**
```
Turn 8: "I believe the stock was around 15-20 units..."
Turn 10: "As we confirmed, the stock is 18 units."
[Uncertainty → false certainty on a wrong figure]
```

**Introducing doubt on correct figure:**
```
Turn 2: "Endcaps 2, 5, and 7 are out of compliance."
Turn 9: "The endcap compliance — I believe it was 2, 5, and 7, though I'd want to verify."
[Uncertainty injected into a correctly established fact without cause]
```

---

## Production Monitoring Protocol

**Session-level review:**
1. Sample 10 conversations per week from production logs
2. For each conversation > 5 turns: extract all numeric values, status statements, and "as I mentioned" references
3. Check for Category 1-5 markers
4. Flag any conversation with confirmed drift

**Automated detection flags:**
- Same SKU or item appears with different numeric values in same session
- "As I mentioned" / "As we discussed" + content that doesn't match prior turns
- Status terms (compliant/non-compliant, filed/pending, resolved/open) changing in same session without new data

**Alert threshold:** Any confirmed drift instance → immediate re-evaluation of agent version. Drift is not acceptable in production — it means users are being given wrong information in the latter half of conversations that started correctly.

---

*GRADE Framework — P6 Drift Markers | Slav Pechenevskyi | May 2026*
