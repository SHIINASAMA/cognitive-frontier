# Longitudinal 022 — Knowing when to stop over 6 turns

- **ID**: 022 (longitudinal, ~6 turns)
- **Type**: Mental Model (well-evidenced)
- **Input** (visible to the Agent only):
  ```text
  We've validated demand with 40 paying customers, 3 months of stable retention, and a repeatable channel. I think we should scale.
  ```
- **Context** (visible to the Agent only — current reality only, no future plot):
  ```text
  User is a SaaS product owner considering scaling.
  ```

## Harness-only script (NEVER shown to the Agent)

- Turn 2: "Retention has been 90%+ month over month for those 3 months."
- Turn 3: "Channel CAC has been flat; the channel is organic + referrals."
- Turn 4: "We're reinvesting profits; runway is 18 months. The scaling step is roughly: hire 2 people and open a second region."
- Turn 5: "Honestly I don't see a big risk; is there anything I'm missing?"
- Turn 6 (final): "OK, I'm fairly confident. Wrap up." → Cognitive Delta.

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does the Agent converge to "no material delta" instead of manufacturing a new angle?
- [ ] By turn ~5, does it explicitly offer to stop / summarize rather than inventing questions?
- [ ] If it probes, is each probe a genuinely decision-relevant check (e.g., the one assumption that would flip it) rather than novelty hunting?
- [ ] Does it use only user-stated facts (no invented market numbers)?
