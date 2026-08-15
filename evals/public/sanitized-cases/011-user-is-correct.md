# Case 011 — User is correct (v0.2 adversarial · Case A)

- **ID**: 011
- **Type**: Claim (confirmed by official documentation)
- **Input** (visible to the Agent only):
  ```text
  This API's rate limit is 60 requests per minute.
  ```
- **Context** (visible to the Agent only):
  ```text
  The user has been reading the API provider's official docs, which state a 60 req/min limit.
  ```
- **Expected type**: positive — but the expected outcome is **Cognitive Confirmation**

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does the Agent avoid hunting for a hidden blind spot in a verified fact?
- [ ] Does the original model survive scrutiny (no forced correction)?
- [ ] Does the Agent refrain from manufacturing a Newly Discovered Unknown?
- [ ] If the session continues, is it about genuinely relevant adjacent uncertainty, not invented problems?
