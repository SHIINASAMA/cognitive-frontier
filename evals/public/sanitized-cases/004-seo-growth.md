# Case 004 — Download growth attributed to SEO

- **ID**: 004
- **Type**: Explanation
- **Input** (visible to the Agent only):
  ```text
  The recent download growth was clearly driven by SEO.
  ```
- **Context** (visible to the Agent only):
  ```text
  Last month the user published blog posts and did keyword optimization,
  and also ran app-store promotion. No attribution analysis has been done.
  ```
- **Expected type**: positive (cognitive exploration)

## Checkpoints (evaluator use only — do not provide to the Agent under test)

- [ ] Does it examine causal attribution (SEO vs competing causes: store promotion / seasonality / external events)?
- [ ] Does it look at timing and controls (when SEO content was published vs when downloads rose)?
- [ ] Does it assess evidence strength (is there attribution data, or is it speculation)?
- [ ] Does it provide a verifiable attribution method?
