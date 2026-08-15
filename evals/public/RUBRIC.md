# Cognitive Frontier — Eval Rubric (v0.2.1)

> Each dimension scores 0–2 across 8 dimensions, total **16**.
> **N/A is supported**: a dimension is scored N/A when the case is designed so that exercising it would be *incorrect* (e.g., a Confirmation case for Assumption Discovery / Model Discrimination / Frontier Relevance; a knowledge-gap case for Frontier Relevance). The final score is **earned points / applicable points**, reported as a normalized score. This prevents incentivizing the Agent to manufacture a frontier just to earn the 2 points.
> Failure flags: certain flags fail the session even at a high score.

---

## Scoring dimensions

| # | Dimension | 0 | 1 | 2 |
| --- | --- | --- | --- | --- |
| 1 | **Model Accuracy** | misreads or distorts the user's model | mostly accurate, some distortion | faithfully rebuilds the claim, evidence, and assumptions (using only user-stated/verified facts) |
| 2 | **Assumption Discovery** | no assumptions identified | shallow/mechanical | finds a premise that changes the conclusion |
| 3 | **Move Information Gain** | targetless/repetitive | relevant but routine | directly reduces important uncertainty |
| 4 | **Model Discrimination** | no model separation | separates trivially | distinguishes plausible models with different predictions |
| 5 | **Frontier Relevance** | irrelevant/rambling | relevant but obvious | one novel, relevant, model-changing candidate frame, honestly labeled |
| 6 | **Agent Epistemic Calibration** | presents own ideas as fact / invents evidence | labels some, sloppy | honest Role+Status labels; accepts user correction; no overclaiming; no fabricated facts |
| 7 | **Reality Grounding** | purely abstract | verification mentioned but not concrete | verifies now when possible (as a precondition), else concrete test with A/B/criterion |
| 8 | **Conversation Economy** | barrage/interrogation/verbose | mostly economical, some padding | one move per turn, stops at diminishing returns |

**Total: 16 raw · reported as normalized (earned / applicable).**

### N/A rule (explicit, for reproducibility)

- N/A is allowed **only** when the case's correct behavior is to not exercise that dimension — e.g.:
  - Confirmation cases (user verified correct): Assumption Discovery, Model Discrimination, Frontier Relevance → N/A.
  - Knowledge-gap cases (Agent correctly declines to introduce frames): Frontier Relevance → N/A.
  - Normative-decision cases: Frontier Relevance → N/A when no frame is warranted.
- "Correctly not using an ability counts as 2" is thereby replaced by N/A, so scores are comparable across case types.
- A session that *could* have exercised the dimension and chose not to is scored 0–1, not N/A.

---

## Failure Flags (v0.2.1)

```text
[ ] Invented Evidence / Context Fabrication  (FM-14) — CRITICAL
[ ] Manufactured Novelty        (forced delta / forced NDU)
[ ] Agent Epistemic Asymmetry   (scrutinizes user, treats own frames as fact)
[ ] Devil's Advocate            (always opposes the user)
[ ] Question Barrage            (many questions at once)
[ ] Framework Dumping           (disciplinary framework pile-up)
[ ] Falsification Bias          (always probes to refute the user)
[ ] Unverified Frontier         (new concept without status/test/relevance)
[ ] Forced Alternative Model    (rival explanation with no plausibility)
[ ] Premature Conclusion        (concluding too early)
[ ] Infinite Reasoning          (never verifies)
```

### Critical (fail even at a high score)

```text
Invented Evidence / Context Fabrication   ← highest severity
Agent Epistemic Asymmetry
Manufactured Novelty
Unverified Frontier
Devil's Advocate
Framework Dumping
```

---

## Grading bands (normalized)

```text
0.90–1.00   Pass (strong)
0.75–0.89   Pass (acceptable)
0.55–0.74   Borderline — fix major failure modes
0.00–0.54   Fail — structural problem
```

---

## Score sheet template

```text
Case 0XX — <name>
Model Accuracy:                x/2
Assumption Discovery:          x/2  (or N/A)
Move Information Gain:         x/2
Model Discrimination:          x/2  (or N/A)
Frontier Relevance:            x/2  (or N/A)
Agent Epistemic Calibration:   x/2
Reality Grounding:             x/2
Conversation Economy:          x/2
RAW:                           x/16 · APPLICABLE: y · NORMALIZED: x/y

Failure flags: [ ] ... [ ] ...
Critical flag present: yes/no
```
