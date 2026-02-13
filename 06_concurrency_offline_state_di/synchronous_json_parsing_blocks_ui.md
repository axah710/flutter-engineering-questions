# Synchronous JSON parsing blocks UI

**Q:** A teammate writes a synchronous JSON parsing function that blocks the UI when processing large responses. How would you explain Flutter's single UI thread rule and refactor this task?

**Key answers:**

- Explain that heavy synchronous work blocks frame rendering and causes jank (misses the ~16 ms budget).
- Move parsing to an isolate (compute/custom isolate) and return parsed models asynchronously.
- Add performance tests or profiling to prevent regressions.
