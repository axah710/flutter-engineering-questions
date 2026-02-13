# Hot reload stops picking up changes

**Q:** Hot reload stops picking up some changes and the UI behaves strangely after multiple edits. The team thinks Flutter is "buggy." How would you use your knowledge of widget/element/render trees to explain what is happening and fix the problem structure-wise?

**Key answers:**

- Explain that hot reload preserves state (element tree), so structural/stateful changes might not reset as expected.
- Fix by using proper keys, avoiding storing mutable UI state in widgets incorrectly, and doing a hot restart when changing state shape.
- Reduce "hidden state": keep state in controllers/stores, not in long-lived singletons tied to old assumptions.
