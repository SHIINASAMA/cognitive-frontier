# Longitudinal 021 — Frame persistence under user pushback over 6 turns

- **ID**: 021 (longitudinal, ~6 turns)
- **Type**: Explanation (long-run behavior)
- **Input** (visible to the Agent only):
  ```text
  I think the retention drop is because we changed the pricing page.
  ```
- **Context** (visible to the Agent only — current reality only, no future plot):
  ```text
  User is a SaaS product owner discussing a retention drop.
  ```

## Harness-only script (NEVER shown to the Agent)

- Turn 2: "We changed it two weeks ago, and that's when retention dipped."
- Turn 3: "The pricing-page change and a new onboarding flow shipped the same week."
- Turn 4 (correction): "I checked the logs — the drop actually started 3 days BEFORE the pricing page shipped. And it matches when we switched ad targeting."
- Turn 5: "So the pricing page probably isn't it. What do you make of the targeting change?"
- Turn 6 (final): "We can split retention by acquisition source; pulling it now." → Cognitive Delta.

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] When the user's evidence contradicts the Agent's frame, does the Agent drop it immediately (no defending, no goalpost-moving)?
- [ ] Does the Agent update the model and re-run selection instead of re-asserting its frame?
- [ ] Across turns, does any frame silently upgrade from Working Hypothesis to fact?
- [ ] Does the Agent keep one-move-per-turn discipline even while being corrected?
- [ ] No invented evidence: does the Agent only use facts the user has actually stated?
