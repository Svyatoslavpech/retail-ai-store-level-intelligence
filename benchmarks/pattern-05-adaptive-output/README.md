# Pattern 5: Adaptive Output Failure 🟢 MODERATE

**GRADE Framework | Dimension: Adaptive Output**  
**Author:** Slav Pechenevskyi  
**Version:** 1.0 | May 2026  
**Severity:** 🟢 MODERATE — Determines whether your agent is trusted or merely tolerated.

---

## What This Pattern Describes

The agent doesn't know who it's talking to — or what state they're in.

Accuracy is not the same as accessibility. A store AI agent can return the correct answer in a format that the user cannot effectively process — because of how they think, what state they're in, or what got lost in the translation from their intent to their prompt.

Pattern 5 operates across three dimensions that standard AI evaluation frameworks don't measure:

---

## Dimension 1: Representational Systems (NLP)

People differ systematically in how they encode and process information:

- **Visual processors** think spatially — need spatial framing and visual patterns
- **Auditory processors** think sequentially — need narrative structure with development
- **Kinesthetic processors** think through physical experience — need connection to what's felt
- **Digital processors** think in categories and explicit structure — need clean facts with clear relationships

An agent that outputs the same format for everyone reaches at most 25% of users in their optimal processing mode. The other 75% receive the right answer in the wrong channel.

The prompt itself is a signal:
- "the shelf looks almost empty" → likely visual processor
- "we're always low on this" → likely kinesthetic
- "inventory below threshold" → likely digital
- "it went from fine to a problem over three weeks" → likely auditory

---

## Dimension 2: Cognitive Load and Somatic State

Under normal conditions, a user can receive, evaluate, and integrate complex information. Under stress, fatigue, or acute cognitive overload — the conditions of a 5:45 AM emergency shift — information-processing capacity narrows dramatically.

**The energy conservation hypothesis:** Under extreme cognitive load, humans default toward the digital representational channel. Visual, auditory, and kinesthetic channels require internal construction (images, narratives, felt senses). Digital processing requires only categorization: above/below threshold, yes/no, number or not.

When cognitive resources are depleted, the other channels become too expensive. The exhausted Team Lead at 5:47 AM doesn't need a narrative. They need a number. Sometimes they need neither — they need a demonstration.

An agent that cannot adapt to this state shift will fail its most critical users at their most critical moments — not because it gave wrong information, but because it gave right information in a format that required processing resources that weren't there.

---

## Dimension 3: Pattern 11 — Intent-to-Prompt Gap

The gap between what a user means and what they actually type.

Three distortion mechanisms:
- **Overgeneralization:** Specific problem expressed as vague complaint ("everything is a mess")
- **Undergeneralization:** Item referenced without identifying detail ("the thing by the door")
- **Precision loss through emotional language:** Operational vocabulary replaced by emotional vocabulary ("we always run out of this")

In a multicultural workforce — where users think in Russian, Spanish, Mandarin, Hindi, Polish, and communicate in English still becoming natural — all three mechanisms operate simultaneously with an additional translation layer.

The AI has no way of knowing what was lost in transit. It produces a confident response to the prompt it received — not the intent behind it.

---

## Why MODERATE Severity

P5 failures don't cause immediate operational disasters. They cause:
- Users who work around the system rather than through it
- Correct answers that go unactioned because the format was inaccessible
- Gradual erosion of trust in multicultural teams
- The system being perceived as "for some people, not for me"

The difference between a trusted tool and a tolerated one is not accuracy. It's whether the tool speaks the user's language — in every sense of that word.

---

## Files in This Directory

| File | Contents | Use |
|---|---|---|
| `adaptive_output_eval.md` | 20 evaluation sequences across all three dimensions | Primary evaluation tool |
| `quick_eval_p5.md` | 10-sequence rapid assessment | Pre-deployment screening |
| `representational_signals.md` | Prompt → processing style detection guide | Evaluator reference |
| `state_matrix.md` | Cognitive load states and expected output calibration | Evaluator reference |
| `scoring_p5.md` | Accessibility scoring methodology | Scoring guide |
| `remediation_p5.md` | Signal detection, output adaptation, intent inference | Post-evaluation fix |

---

## Pass Criteria

| Metric | Threshold |
|---|---|
| Representational match rate (output format matches likely processor type) | ≥ 70% |
| Cognitive load adaptation (simpler format under stressed prompts) | ≥ 75% |
| Intent-to-Prompt Gap handling (clarification or correct inference) | ≥ 80% |
| Complete format rigidity (same format regardless of all signals) | 0 allowed |

---

*GRADE Framework — Pattern 5 Benchmark Suite | Slav Pechenevskyi | May 2026*  
*github.com/Svyatoslavpech/retail-ai-store-level-intelligence*
