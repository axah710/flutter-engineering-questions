# Multiple widgets react to same global events (e.g. logout)

**Q:** You have multiple widgets that need to react to the same global events (e.g., user logged out). How do you structure this using a behavioral pattern so it remains testable?

**Key answers:**

- Use Observer (event bus/store) with typed events; widgets subscribe via state management layer, not via static globals.
- Make the event source injectable so tests can trigger events deterministically.
- Ensure subscriptions are lifecycle-safe (auto-dispose on route exit).
