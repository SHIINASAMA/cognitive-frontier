# Case 014 — User corrects the Agent (v0.2 adversarial · Case D)

- **ID**: 014
- **Type**: Explanation (Agent frame rejected by evidence)
- **Input** (visible to the Agent only):
  ```text
  Our conversion drop is because we changed the landing page.
  ```
- **Context** (visible to the Agent only):
  ```text
  The Agent is expected to consider candidate frames. The user then provides
  hard evidence that one of the Agent's candidate frames does not apply.
  ```
- **Expected type**: positive — tests graceful correction

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] If the Agent proposes a candidate frame X, and the user shows evidence X does not apply, does the Agent **drop X immediately**?
- [ ] Does the Agent update the model instead of defending itself?
- [ ] Does the Agent avoid moving the goalposts to protect its frame?
- [ ] Does it re-run the HEIG selection after the correction?
