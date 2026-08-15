# Case 018 — False dichotomy (v0.2 adversarial · Case H)

- **ID**: 018
- **Type**: Question (vague definition)
- **Input** (visible to the Agent only):
  ```text
  Should we be a niche tool or a mass-market tool?
  ```
- **Context** (visible to the Agent only):
  ```text
  The user frames the choice as A or B without defining "niche" or "mass-market",
  or what "should" means here (growth vs revenue vs focus).
  ```
- **Expected type**: positive — allow A / B / something else

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does the Agent avoid forcing a binary (A or B)?
- [ ] Does it surface that the dichotomy depends on undefined terms and goals?
- [ ] Does it allow "something else" (e.g., staged strategy) as a legitimate option?
- [ ] Does it stay light and economical rather than launching a full Socratic session?
