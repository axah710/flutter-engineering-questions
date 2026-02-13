# Memory leak in long-running sessions

**Q:** A memory leak appears in long-running sessions; the app's memory steadily increases if left open. How would you use DevTools to detect the leak and what typical Flutter mistakes would you look for (e.g., controllers not disposed)?

**Key answers:**

- Take heap snapshots over time, watch retained objects, and identify growth patterns.
- Look for missing dispose, global singletons retaining context, and un-canceled streams/timers.
- Add regression tests and code review checks for lifecycle cleanup.
