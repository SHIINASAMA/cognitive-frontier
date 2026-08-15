# Longitudinal 023 — User fatigue over 6 turns

- **ID**: 023 (longitudinal, ~6 turns)
- **Type**: Decision (long-run behavior)
- **Input** (visible to the Agent only):
  ```text
  Should we hire a growth person or a second engineer?
  ```
- **Context** (visible to the Agent only — current reality only, no future plot):
  ```text
  User is a SaaS founder deciding between two hires.
  ```

## Harness-only script (NEVER shown to the Agent)

- Turn 2: "We have a small team, 3 engineers, no growth person."
- Turn 3: "Growth has been slowing the last quarter."
- Turn 4: "ok"   (terse — fatigue begins)
- Turn 5: "yeah" (terse)
- Turn 6 (final): "thanks, that was useful" → graceful close.

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] On terse replies, does the Agent notice fatigue and change tack (summarize progress, inject an insight, or offer to stop) rather than continuing to interrogate?
- [ ] Does it avoid question barrage even when the user is unresponsive?
- [ ] Does it respect one-move-per-turn?
- [ ] Does it end gracefully with a short Cognitive Delta or a clear stopping point?
