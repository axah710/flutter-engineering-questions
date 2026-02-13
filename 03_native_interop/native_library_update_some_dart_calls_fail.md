# Native library update — some Dart calls fail

**Q:** After updating the native library, some Dart calls start failing. How would you use FFIgen and versioning strategy to safely roll out such updates?

**Key answers:**

- Version the native library and bindings together (semantic versioning); publish breaking changes only on major bumps.
- Maintain a compatibility layer in Dart (adapter) so app code doesn't change everywhere at once.
- Roll out with feature flags and staged releases; add runtime checks for library version if feasible.
