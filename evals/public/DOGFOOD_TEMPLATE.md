# Dogfood Template (v0.2)

> Target: **15–20 real sessions**. This is the calibration loop for v0.2 — the goal is not "did the Agent find something new" but whether the session improved the user's epistemic position at acceptable cost.
> Session records go to `evals/private/runs/dogfood/` (ignored by git — may contain personal context).

## Per-session log

```text
Date / context:           #
Trigger (explicit/high-value):   #

Initial belief:            #

Questions:
- Did the Agent change my mind?           yes / no / partially
- Should it have changed my mind?         yes / no / unsure
- Did it introduce something unsupported?  (quote it if so)
- Did it make me notice uncertainty?      yes / no
- Did it waste my time?                   yes / no  (how much?)
- Did it know when to stop?               yes / no
- Did my original view survive?           yes / no / partially

Most useful move:          #
Newly discovered unknown?  (if any)      #
Epistemic status labels were honest?     yes / no
```

## Positive signals (all three count equally)

- **A** — "I genuinely hadn't thought of that angle."
- **B** — "My judgment actually holds up better than I thought."
- **C** — "Now I know exactly what evidence is missing."

## Negative signals (most important tuning data)

- "What's the point of this question?"
- "Are you arguing with me again?"
- "What's the use of all these questions?"
- The Agent introduced an unlabeled frame that turned out wrong.
- The Agent kept probing after information gain had clearly dropped.

## Review cadence

After every 5 sessions: score each against `RUBRIC.md`, tally failure flags, and note recurring mechanical patterns before deciding any v0.3 feature work (persistent cognitive map / recurring blindspot detection / reality loop are candidates only after dogfood shows the base skill is stable).
