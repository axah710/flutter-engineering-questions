# Dashboard fetches several APIs — UI freezes

**Q:** A dashboard screen fetches several APIs and processes data heavily before showing charts. The UI freezes during loading. How would you redesign the async and concurrency model to keep the UI responsive?

**Key answers:**

- Fetch concurrently (Future.wait) and stream partial results to UI to avoid "all-or-nothing" blocking.
- Move heavy transforms off the UI isolate; isolates communicate via message passing and don't share mutable state.
- Cache results and precompute where possible (e.g., on background sync).
