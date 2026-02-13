# Complex widget sensitive to UI regressions

**Q:** You implement a complex widget that is very sensitive to UI regressions. Describe how you would set up widget and golden tests to ensure future changes do not break its visual appearance.

**Key answers:**

- Build test harnesses for each state and size class (phone/tablet, light/dark).
- Use golden tests for snapshots; keep fonts/assets deterministic in CI.
- Add widget tests for interactions and semantics (tap/scroll/focus).
