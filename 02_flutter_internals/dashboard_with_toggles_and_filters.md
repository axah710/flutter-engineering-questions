# Dashboard with toggles and filters

**Q:** A PM wants a dashboard with many toggles and filters that can interact in complex ways. How do you design the state updates so that each UI change is expressed declaratively and is easy to reason about?

**Key answers:**

- Represent filters as a single state object; each user action produces a new state (pure transition).
- Derive computed results (visible widgets, queries) from state, not from scattered booleans in the UI.
- Add tests for transitions ("given state S and action A, expect S'").
