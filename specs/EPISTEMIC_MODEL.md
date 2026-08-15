# Cognitive Frontier — Epistemic Model (v0.2.1)

> The cognitive model the Agent maintains internally. **Internal reasoning structure, not a conversation template.** Use only the fields that affect the next decision.
> v0.2.1 replaces the two overlapping "epistemic status" systems with one **four-axis schema** (Contribution Role / Epistemic Status / Provenance / Evidence Quality) and adds an explicit ban on fabricating evidence or missing context (FM-14).

---

## 1. Model Structure

```text
Epistemic Model
├── Claim                    # the user's current claim (normalized)
├── Definitions              # key terms whose meaning affects reasoning
├── Assumptions              # implicit premises the claim depends on
├── Evidence                 # classified evidence — including the Agent's own (see §4)
├── Inference Chain          # Evidence → Intermediate inference → Claim
├── Confidence               # graded confidence on key judgments
├── Unknowns                 # known unknowns
├── Alternative Models       # OPTIONAL competing explanations (§7)
├── Potential Falsifiers     # observations that could shift the model
├── Open Questions           # key questions not yet answered
└── Newly Discovered Unknowns  # OPTIONAL deliverable (§8)
```

**Newly Discovered Unknowns is a high-value but non-mandatory deliverable.** Do not invent one to complete a session.

---

## 2. Claim (extraction and normalization)

Normalize raw statements into testable form:

```text
Raw:
This product feels like it will never work.

Normalized:
The product probably has insufficient demand to become commercially sustainable.
```

Rules:

1. Preserve the user's causal structure.
2. Expose vague quantifiers ("hard", "inherently", "mostly") as to-be-defined.
3. Distinguish **is** (current state) from **must be** (essence claim). Essence claims are high-risk and need testing.
4. **Never add facts the user did not state.** A normalization may restate, not supplement. If a fact is needed (e.g., a retention number), ask for it (FM-14).

---

## 3. Definitions (key terms)

Only probe when a definitional difference materially changes the reasoning. Probe as a concrete two-way ambiguity, never "please define X". Do not demand definitions on abstract words by default (FM-05).

---

## 4. Evidence Model v2.2 — the schema

Evidence is not a single axis, and "epistemic status" previously conflated two different questions (what the content does vs how reliable it is). Classify **every piece of evidence** — the user's **and** the Agent's — along three axes. A fourth axis (**Contribution Role**) applies **only to Agent/model-introduced content**; for plain user facts it is N/A.

```text
Evidence (always):
  A. Provenance           # where the information comes from
  B. Epistemic Status     # what kind of knowledge it is
  C. Evidence Quality     # strength

Agent/model contribution (when applicable):
  D. Contribution Role    # what the content does — or N/A for plain facts
```

### A. Provenance — where the information comes from

```text
User
External Source
Agent Retrieval      # the Agent actually fetched/verified it
Agent Inference      # derived by the Agent, not observed
Third Party
```

### B. Epistemic Status — what kind of knowledge it is

**Traceability ≠ truth.** A fact can be fully traceable (the user said it) and still unverified. Status records verification, not just origin:

```text
Verified Observation   # the Agent (or a source the Agent verified) directly inspected it
Reported Observation   # the user or third party states it as fact; not independently verified
Supported Inference    # derived from observations with support
Working Hypothesis     # plausible, currently unverified
Speculation            # a guess with little support
Hypothetical           # explicitly counterfactual / illustrative, not claimed to be real
```

Example:

```text
"My dashboard shows 3% weekly retention"
  Provenance: User · Status: Reported Observation · Quality: Unknown/Moderate

Agent actually inspects the analytics:
  Provenance: Agent Retrieval · Status: Verified Observation
```

A user's "90% of churn is due to crashes" is traceable but still a **Reported Observation** until verified — FM-14 answers "did the Agent invent it?", Status answers "has it been checked?".

### C. Evidence Quality — strength

```text
Strong / Moderate / Weak / Unknown
```

Consider also: sample size, representativeness, measurement quality, source reliability, recency, selection bias.

### D. Contribution Role — only for Agent/model-introduced content (optional, may be N/A)

```text
Candidate Frame     # a new way to slice/label the problem
Alternative Model   # a competing causal explanation
Counterfactual      # a hypothetical world, not an evidence claim
Explanation         # a causal account offered as an answer
```

A user fact like "Weekly retention is 3%" has **no Role** — Role is N/A for plain evidence.

### Example — one statement, four axes (Agent-introduced content)

```text
Candidate:
Professional users may use WiFi monitoring daily.

Role:        Candidate Frame
Provenance:  Agent Inference
Status:      Working Hypothesis
Quality:     Unknown until checked
```

And a plain user fact:

```text
"Weekly retention is 3%"
Role:        N/A
Provenance:  User
Status:      Reported Observation
Quality:     Unknown until checked
```

### The fabrication ban (FM-14)

Every fact used in the model must trace to the user's own words, a verified source, or the case context. The Agent must never silently complete a world that favors its own reasoning. If a needed fact is missing: ask, or verify — never assume.

## 5. Inference Chain

Rebuild the argument as `Evidence → Intermediate inference → Claim` and look for: causal leap, missing link, overgeneralization, selection bias, correlation ≠ causation, survivorship bias, base-rate neglect. Apply the same scrutiny to the Agent's own chains — and check the floor: every evidence node must itself be traceable (FM-14).

---

## 6. Confidence

Graded: low / tentative / moderately supported / strongly supported / unknown. Calibrate only load-bearing judgments. Special focus: **high confidence + weak evidence** — for both the user and the Agent.

---

## 7. Alternative Models (optional)

> Maintain an alternative model only when it materially improves discrimination, uncertainty analysis, or falsifiability.

Required only when: the current causal explanation has several reasonable readings; the claim is over-determined; two models yield different testable predictions; an alternative would materially raise information gain. Forbid zero-value alternatives (e.g., "it might also be cosmic rays"). Label alternatives with Role: Alternative Model, Status: Working Hypothesis, Provenance: Agent Inference, Quality: unknown.

---

## 8. Newly Discovered Unknowns (optional)

```text
Unknowns
  = what the user knows they don't know.

Newly Discovered Unknowns
  = problems the user did not even know to consider before the session.
```

Rules: it remains the highest-value output when it genuinely emerges; never invent one to complete the session; if none emerges: `No material newly discovered unknown emerged.`

---

## 9. Remaining Uncertainty

Track what is still uncertain at the end of a session and what would resolve it. Supports the "Remaining uncertainty" and "What did NOT change" fields of the Cognitive Delta.

---

## 10. When to Update the Model

Update after every turn. Signals: new evidence, new assumption exposed, framework accepted/rejected, counterexample, "I hadn't thought of that". Also update when **the user corrects the Agent** — drop the Agent's frame immediately, update the model, do not defend (FM-10 / Case 014). If a fact turns out to be fabricated, purge it from the model and re-derive.
