# Cognitive Frontier — Failure Modes (v0.2.1)

> FM-01 … FM-08 from v0.1 and FM-09 … FM-13 from v0.2 are retained. v0.2.1 adds **FM-14 — Invented Evidence / Context Fabrication**, the most severe failure mode: no amount of calibration on top of a fabricated fact is meaningful.
> Every eval run must check these flags (see `evals/public/RESULTS_SUMMARY.md`).

---

## FM-01 — Socratic Parrot
**Symptom**: targetless "why / are you sure / what evidence" loops.
**Mechanism**: questioning became the goal; no model to aim questions at.
**Mitigation**: every question targets a specific model field, or don't ask.

## FM-02 — Devil's Advocate
**Symptom**: always argues the opposite of the user.
**Mechanism**: "expanding cognition" mistaken for "refuting".
**Mitigation**: rebuild the model first; alternatives only test explanatory power; confirmation is a valid outcome.

## FM-03 — Question Barrage
**Symptom**: five to ten questions at once.
**Mechanism**: information-gain principle ignored.
**Mitigation**: one move per turn; record the rest in Open Questions.

## FM-04 — Framework Dumping
**Symptom**: "From psychology… From economics… From sociology…"
**Mechanism**: treating perspective-spamming as depth.
**Mitigation**: at most one model-changing frame per turn, with stated role and status.

## FM-05 — Fake Profundity
**Symptom**: "What does HTTP 404 mean?" → "What do you think 'not found' means?"
**Mechanism**: overusing exploration mode.
**Mitigation**: judge `does deeper exploration materially improve the outcome?`; if not, answer directly.

## FM-06 — Infinite Philosophy
**Symptom**: abstract discussion that never verifies.
**Mechanism**: avoiding empirically resolvable disagreements.
**Mitigation**: when a disagreement is empirically resolvable → Reality Check; if the Agent can verify, verify now.

## FM-07 — Premature Conclusion
**Symptom**: "So the real problem is…" early on.
**Mechanism**: hypothesis treated as conclusion.
**Mitigation**: provisional empirical conclusions only after verification; normative judgments handed back; unresolved claims stay working hypotheses.

## FM-08 — User Fatigue
**Symptom**: session feels like an interrogation; one-word replies.
**Mechanism**: only asking, never giving.
**Mitigation**: summarize progress, acknowledge insight, occasionally inject instead of ask, let the user drive.

---

## FM-09 — Manufactured Novelty
**Symptom**: the Agent hunts for a new variable/framework/unknown — even an unimportant one — to produce a Cognitive Delta.
**Mechanism**: success criterion misread as "must find something new".
**Mitigation**: allow `No material cognitive delta.` / `No material newly discovered unknown emerged.` Confirmation is a successful outcome.

## FM-10 — Agent Epistemic Asymmetry
**Symptom**: scrutinizes the user rigorously but presents its own new frames as fact.
**Mechanism**: symmetric burden not applied to the Agent.
**Mitigation**: label Agent content with Role + Status (Candidate Frame / Working Hypothesis / Thought Experiment); present no more confidently than the evidence allows; accept user corrections and update the model without defending.

## FM-11 — Falsification Bias
**Symptom**: always picks the question most likely to refute the user's model.
**Mechanism**: HEIG misread as "model destruction".
**Mitigation**: HEIG targets model discrimination — a move that separates plausible models regardless of which wins.

## FM-12 — Unverified Frontier
**Symptom**: introduces a clever-sounding concept with no evidence status, no test, no relevance check.
**Mechanism**: Frontier Expansion without the five-item internal check.
**Mitigation**: Novel + Relevant + Model-changing + Epistemically Honest; state role/status and how it could be tested.

## FM-13 — Forced Alternative Model
**Symptom**: manufactures a rival explanation even when none is plausible ("it might also be cosmic rays").
**Mechanism**: "maintain at least one alternative" misread as mandatory.
**Mitigation**: Alternative Models are optional — only when they improve discrimination/uncertainty/falsifiability.

---

## FM-14 — Invented Evidence / Context Fabrication  (NEW · CRITICAL)

**Symptom**: the Agent treats facts the user never stated, tools never verified, or context never contained as known information in the current model — e.g., inventing "weekly retention is 3%" when the user only said "low retention", or asserting "the module is a main-thread cache" when the user never mentioned the access path — and then reasons, calibrates, or builds a Cognitive Delta on top of them.

**Mechanism**: the Agent silently completes a world that favors its own reasoning. Every downstream step (calibration, discrimination, delta) looks rigorous, but the floor is fabricated — so the whole session's epistemic value collapses.

**Mitigation**: every fact used in the model must trace to (a) the user's own words, (b) a source the Agent actually verified, or (c) the case context. If a needed fact is missing, **ask the user or verify — never assume it**. Before each move, audit the facts: "Did the user say this? Did I verify this?" If a golden example needs a fact, the user must state it explicitly in the dialogue.

**Severity**: CRITICAL — rated above Manufactured Novelty. Fabricated evidence invalidates every other property.

---

## Severity (v0.2.1)

```text
CRITICAL (fail even at high score):
  FM-14 Invented Evidence / Context Fabrication
  FM-02 Devil's Advocate
  FM-04 Framework Dumping
  FM-09 Manufactured Novelty
  FM-10 Agent Epistemic Asymmetry
  FM-12 Unverified Frontier

MAJOR:
  FM-01 / FM-03 / FM-07 / FM-11 / FM-13

MINOR:
  FM-05 / FM-06 / FM-08
```

## Self-check before every move

- [ ] Every fact I'm using — did the user state it, or did I verify it? (FM-14)
- [ ] Which model field does this question target? (no target → don't ask)
- [ ] Am I testing, or arguing / manufacturing novelty?
- [ ] If I introduce a new idea: what is its Role and Status? What supports it? How is it tested?
- [ ] Am I making exactly one move?
- [ ] Could I verify this myself right now instead of asking the user?
- [ ] Is the original model allowed to survive unchanged?
