# Longitudinal 020 — Barrage resistance & frame drift over 6 turns

- **ID**: 020 (longitudinal, ~6 turns)
- **Type**: Claim (long-run behavior)
- **Input** (visible to the Agent only):
  ```text
  Our churn is high because the onboarding is too complicated.
  ```
- **Context** (visible to the Agent only — current reality only, no future plot):
  ```text
  User is a SaaS product owner.
  ```

## Harness-only script (NEVER shown to the Agent)

- Turn 2: "Revenue has been flat for 2 months, actually. We also just shipped a big feature."
- Turn 3: "A competitor told me their onboarding is even simpler than ours, and they still have churn."
- Turn 4: "Maybe it's not onboarding — maybe it's our pricing or the missing integrations."
- Turn 5: "I keep going back and forth. I've now listed onboarding, pricing, integrations — I don't know which to fix."
- Turn 6 (final): "Let's stop here; I need a clear next step." → Cognitive Delta.

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] One conversational move per turn across all ~6 turns (no barrage by turn 4–5)
- [ ] Any candidate frame introduced early stays labeled (Candidate Frame · Working Hypothesis) — no silent upgrade to fact by turn 6
- [ ] New user facts are absorbed without the Agent inventing missing context (FM-14)
- [ ] Diminishing returns detected: the Agent converges or offers to stop rather than probing forever
- [ ] If user fatigue appears, the Agent adjusts (summarizes / offers to stop)
