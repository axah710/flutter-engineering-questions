# Two identical stateful widgets mix state

**Q:** You have two identical stateful child widgets that should keep separate states (e.g., two counters), but after some rebuilds their states get mixed. How would you redesign this using the right type of Key?

**Key answers:**

- Assign distinct keys to each instance (ValueKey('counterA'), ValueKey('counterB')).
- If identity must always be unique per rebuild, use UniqueKey (but only when you truly want state reset).
- Prefer data-driven identity keys when preserving state is the goal.
