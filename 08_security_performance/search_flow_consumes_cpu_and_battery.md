# Search flow consumes CPU and battery

**Q:** You see that a specific flow (e.g., searching large datasets) consumes a lot of CPU and battery. How would you optimize both the algorithm and the Flutter implementation?

**Key answers:**

- Optimize algorithm first (indexes, better search strategy, incremental results).
- Move heavy compute off UI isolate; isolates use message passing and don't share state.
- Cache results and avoid redundant work on every keystroke (debounce + incremental updates).
