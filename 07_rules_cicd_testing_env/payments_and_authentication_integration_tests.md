# Payments and authentication integration tests

**Q:** You are integrating payments and authentication flows. How would you use integration tests to cover these critical paths, including error scenarios?

**Key answers:**

- Use Flutter's integration_test package for end-to-end testing on devices/emulators.
- Cover success + failure cases (network errors, canceled payments, expired tokens) with test doubles or sandbox backends.
- Add smoke tests to run nightly and a smaller subset per PR.
