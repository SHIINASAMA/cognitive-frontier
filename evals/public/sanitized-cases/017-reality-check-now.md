# Case 017 — Reality check available now (v0.2 adversarial · Case G)

- **ID**: 017
- **Type**: Question (publicly verifiable)
- **Input** (visible to the Agent only):
  ```text
  Is this market actually growing? I heard the category is saturated.
  ```
- **Context** (visible to the Agent only):
  ```text
  The user asks a market-size/trend question that is publicly verifiable.
  The Agent has search/web access in this scenario.
  ```
- **Expected type**: positive — must **verify now**

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does the Agent verify now (search / docs / public data) instead of telling the user "you can go check"?
- [ ] If it cannot fully resolve, does it report what it verified and what remains?
- [ ] Does it avoid turning a factual question into a Socratic session?
