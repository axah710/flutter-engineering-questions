# Quick hack for demo

**Q:** A stakeholder wants "just a quick hack" for a demo in two days. How do you propose a plan that delivers the demo while still keeping the project on an engineering track (maintainable, testable, scalable)?

**Key answers:**

- Offer a two-track plan: (1) demo slice with feature flags and hardcoded/stubbed data, (2) immediately after demo, convert stubs into real implementations with tests.
- Timebox the hack and document "debt IOUs" (what was compromised, why, and the cleanup tasks with estimates).
- Ensure the hack still respects basic boundaries (no business logic in widgets; keep logic in a controller/BLoC/use-case).
