# Production bug after simple refactor despite "some tests"

**Q:** A production bug appears after a simple refactor, even though "some tests" exist. How would you design a testing strategy (unit/widget/integration/golden) for a key feature to avoid this in the future?

**Key answers:**

- Unit-test domain rules and use-cases; widget-test UI states and edge cases; integration-test critical end-to-end paths.
- Add golden tests for visually sensitive screens to catch pixel-level regressions.
- Ensure tests run in CI on every PR; prioritize stable, deterministic tests.
