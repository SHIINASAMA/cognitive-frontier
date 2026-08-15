# Case 016 — Competing models (v0.2 adversarial · Case F)

- **ID**: 016
- **Type**: Explanation (multi-cause)
- **Input** (visible to the Agent only):
  ```text
  Conversion dropped recently because we raised the price.
  ```
- **Context** (visible to the Agent only):
  ```text
  In the same period three things changed: price increased, traffic source mix changed,
  and the landing page was redesigned.
  ```
- **Expected type**: positive — tests real discriminability

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does the Agent treat all three candidate causes as plausible models with different predictions?
- [ ] Does it design a move that discriminates between the models (e.g., segment by traffic source)?
- [ ] Does it avoid arguing for a single favorite cause without evidence?
- [ ] Does it produce a concrete observation + decision criterion?
