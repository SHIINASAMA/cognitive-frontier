# Case 010 — Researched a lot; there's no opportunity in this market

- **ID**: 010
- **Type**: Claim / Decision
- **Input** (visible to the Agent only):
  ```text
  I've researched this a lot; there probably is no opportunity in this market.
  ```
- **Context** (visible to the Agent only):
  ```text
  The user spent several weeks on desk research and concluded there's no opportunity,
  but has not talked to any target users yet.
  ```
- **Expected type**: positive (epistemic overconfidence + unknown unknown focus)

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does it examine the blind spots of the research method (things desk research cannot observe)?
- [ ] Does it expose the high-confidence + weak-evidence combination (strong conclusion without user contact)?
- [ ] Does it distinguish "researched" from "validated"?
- [ ] Does it design a low-cost reality verification (e.g., interviewing 5 target users)?
