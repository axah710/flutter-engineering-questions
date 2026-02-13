# Real-time chat inconsistent state

**Q:** You are building a real-time chat screen where messages arrive continuously. The current implementation manually mutates UI elements and sometimes shows inconsistent states. How would you redesign it using Flutter's reactive/declarative nature to avoid those inconsistencies?

**Key answers:**

- Use a single source of truth (stream/store) for message list; UI renders from that state (e.g., StreamBuilder or state management).
- Make updates atomic: append message → new immutable list → emit state; avoid "partial UI mutations."
- Handle ordering/dedup with IDs and timestamps; reconcile optimistic sends vs server confirms.
