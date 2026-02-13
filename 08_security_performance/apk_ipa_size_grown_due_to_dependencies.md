# APK/IPA size grown due to dependencies

**Q:** The APK/IPA size has grown significantly due to added dependencies. How would you analyze the app size and then decide what to remove, split, or tree-shake to reduce it?

**Key answers:**

- Audit dependencies, remove unused ones, and replace heavy packages with lighter alternatives where feasible.
- Split features into modules/packages and avoid bundling unused assets.
- Verify tree-shaking works (avoid reflective/dynamic patterns that block it).
