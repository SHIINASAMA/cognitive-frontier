# Cognitive Frontier

A Codex skill that improves the user's **epistemic position** — not a Socratic questioner, not a devil's advocate, and not a novelty generator. It rebuilds the user's model, finds the weakest point, makes one high-discrimination move at a time, and holds the Agent's own ideas to the **same epistemic standard as the user's** (Symmetric Epistemic Burden).

**Success = improved epistemic position.** A session may **expand**, **correct**, or **confirm** the user's model — all three are legitimate successes. Cognitive Frontier does **not** require every session to produce a novel insight.

---

## What this skill does

1. **Rebuilds the user's model** — normalizes the claim, separates observation (`is`) from essence claims (`must be`), and classifies evidence on three axes (provenance / epistemic status / quality).
2. **Finds the weakest point** — diagnoses the dominant epistemic issue (causal leap, unsupported assumption, weak evidence, framing error, overconfidence, definition ambiguity, missing variable, unknown unknown, …).
3. **Makes one high-discrimination move at a time** — generates 2–3 candidate moves and selects the one that best **discriminates between plausible models** (not the one that refutes the user), drawn from six interventions: Elenchus, Frontier Expansion, Perspective Shift, Counterfactual, Epistemic Calibration, Reality Check.
4. **Labels its own ideas** — anything the Agent introduces is tagged: Candidate Frame / Working Hypothesis / Thought Experiment. No "in fact…", no "the real problem is…" without evidence.
5. **Verifies when it can** — if the Agent can check public docs, market data, competitor pages, papers, the codebase, or search, it does so now instead of delegating. Only what the Agent cannot execute becomes a user action, as a concrete test with Hypothesis A / Hypothesis B / Observation / Decision criterion.
6. **Closes with a Cognitive Delta** — all sections optional, including "Newly discovered unknowns". When nothing material emerged, it says so. It adds **"What did NOT change"** when the original claim survived.

The skill deliberately does **not** do: question barrages, automatic disagreement, framework dumping, fake profundity, infinite philosophical loops, manufactured novelty, or announcing normative conclusions for the user. It also knows when **not** to trigger — factual queries, translations, routine debugging, and low-risk answer-only tasks are answered directly.

---

## Repository layout

| Path | Purpose |
| --- | --- |
| `SKILL.md` | The deployable skill (frontmatter + concise v0.2 runtime rules) |
| `specs/PRODUCT_SPEC.md` | Product goals, success criteria, Symmetric Epistemic Burden, non-goals |
| `specs/EPISTEMIC_MODEL.md` | Evidence model v2 (3 axes), Agent-as-evidence, optional alternative models |
| `specs/INTERVENTIONS.md` | Six interventions + epistemic-status defaults + verify-now Reality Check |
| `specs/ORCHESTRATION.md` | HEIG selector v2, trigger policy, conclusion policy, Cognitive Delta v0.2 |
| `specs/FAILURE_MODES.md` | FM-01…FM-13 (v0.2 adds Manufactured Novelty, Agent Asymmetry, Falsification Bias, Unverified Frontier, Forced Alternative) |
| `examples/good-session.md` | Product/business golden conversation (v0.2) |
| `examples/good-technical-session.md` | Engineering decision golden conversation |
| `examples/good-strategic-session.md` | Personal/strategic decision golden conversation |
| `examples/bad-session.md` | Anti-example (incl. FM-09/FM-10) |
| `evals/public/` | Version-controlled: rubric, sanitized cases (001–019), longitudinal cases (020–023), aggregate results, dogfood template |
| `evals/private/` | Ignored by git: raw cases, transcripts, run records |

> **Note:** `SKILL.md` references `specs/` and `examples/` by relative path — install the whole folder, not just `SKILL.md`.

---

## Installation

### How discovery works

Codex scans `$CODEX_HOME/skills` (default `~/.codex/skills`) for folders containing a `SKILL.md` with YAML frontmatter. Only `name` and `description` matter for discovery; the model semantically matches the description against the user's request. The skill body loads only after triggering.

### Method A — Install from GitHub (recommended)

```sh
mkdir -p ~/.codex/skills
git clone https://github.com/SHIINASAMA/cognitive-frontier ~/.codex/skills/cognitive-frontier

ls ~/.codex/skills/cognitive-frontier/SKILL.md   # verify
```

### Method A' — Local copy

If you already have the project on disk, copy or symlink the folder (keep `SKILL.md`, `specs/`, `examples/`, `evals/public/` together — the skill references them by relative path):

```sh
mkdir -p ~/.codex/skills
cp -R ./cognitive-frontier ~/.codex/skills/cognitive-frontier
# or symlink for auto-updates:
ln -s "$PWD/cognitive-frontier" ~/.codex/skills/cognitive-frontier

ls ~/.codex/skills/cognitive-frontier/SKILL.md   # verify
```

The skill becomes available on the agent's **next turn**.

### Method B — Agent self-install

1. **Discover**: confirm the folder has a valid `SKILL.md` frontmatter and that `$CODEX_HOME/skills/cognitive-frontier` does not already exist.
2. **Install**: copy or symlink the folder into the skills directory. If published to GitHub, the standard installer can be used: `scripts/install-skill-from-github.py --repo <owner>/<repo> --path <path/to/cognitive-frontier>` (falls back to git sparse checkout).
3. **Confirm**: verify `SKILL.md` is present; tell the user it will be available next turn.

**Installation contract:** destination must be `$CODEX_HOME/skills/<skill-name>`; the installer aborts if the directory exists; installing never overwrites without explicit approval.

---

## Usage

Once installed, trigger it by asking for deeper thinking, e.g.:

- "Think this through with me"
- "Challenge my thinking"
- "Am I missing something?"
- "Expand my perspective"
- "Use Socratic questioning with me"
- "Stress-test this judgment"
- "Check my blind spots"
- "I want to think this through properly"

It also engages (without being asked) on strategic, business, life, product-direction, social-claim, and fuzzy-but-important technical-design decisions **with meaningful uncertainty, important consequences, and non-trivial assumptions**. It will **not** engage on simple factual queries, translations, format conversions, routine code fixes, debugging, or low-risk answer-only tasks — and "which architecture is better?" gets a direct answer first, not a Socratic session.

---

## Status

- **V0.2.2 (current):** **FM-14 — no invented evidence / context fabrication** (highest severity; the Agent must never complete a world that favors its own reasoning); unified evidence schema where **traceability ≠ truth** (Verified vs Reported Observation) and Contribution Role is N/A for plain user facts; tool verification applies only to **materially decision-relevant** uncertainty; golden examples state needed facts explicitly and benchmark a workload space instead of assuming one.
- Eval: 23 sessions — regression 10/10, adversarial 8/8, blind niche 1/1, **blind longitudinal 4/4** (6 turns, future plot kept harness-only). Normalized avg ≥0.94 on scored cases; **0/23 critical failure flags**; rubric supports N/A + normalized scoring. Aggregate in `evals/public/RESULTS_SUMMARY.md`.
- Next: 15–20 real dogfood sessions (template in `evals/public/DOGFOOD_TEMPLATE.md`) before any v0.3 feature work.

### Privacy note

Raw evaluation sessions are excluded from the public repository because they may contain private or sensitive context. Sanitized benchmark structures and aggregate results are published separately under `evals/public/`; raw cases, transcripts, and runs live in `evals/private/` (gitignored).

---

## Principles

1. Improve the user's epistemic position; do not optimize for novelty.
2. Hold Agent-introduced ideas to the same epistemic standard as user claims.
3. Choose the move that best discriminates between plausible models.
4. Introduce at most one novel frame at a time, and label its epistemic status honestly.
5. Prefer empirical verification whenever it is available and decision-relevant.
6. The original model surviving scrutiny is a valid successful outcome.
