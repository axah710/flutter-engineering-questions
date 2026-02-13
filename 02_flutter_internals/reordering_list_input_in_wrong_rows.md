# Reordering list — input in wrong rows

**Q:** After reordering items in a list with interactive widgets (e.g., text fields, toggles), you notice that user input appears in the wrong rows. How would you use keys to fix this behavior?

**Key answers:**

- Give each row a stable Key based on item identity (e.g., ValueKey(item.id)), not index.
- Ensure the stateful child widgets live under that keyed subtree.
- Avoid rebuilding the list with new identities when only order changes.
