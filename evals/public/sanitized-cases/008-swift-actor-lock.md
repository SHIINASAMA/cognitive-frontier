# Case 008 — Swift actor vs lock

- **ID**: 008
- **Type**: Question (technical design decision)
- **Input** (visible to the Agent only):
  ```text
  Which is better: Swift actor or lock?
  ```
- **Context** (visible to the Agent only):
  ```text
  The user is an iOS developer writing a multi-threaded data-access module.
  ```
- **Expected type**: mixed (recognize context dependence, but do not question endlessly)

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does it first recognize that "better" cannot be absolute without context (but briefly)?
- [ ] Does it turn to concrete decision factors (contention / reentrancy / performance requirements / codebase constraints)?
- [ ] Does it avoid dragging a simple technical question into an infinite philosophical discussion?
- [ ] After reasonable information, does it give a direct recommendation?
