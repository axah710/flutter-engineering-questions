# Clean Architecture with existing BLoC app

**Q:** You are asked to integrate Clean Architecture in an existing Flutter app with BLoC. How would you design the layers and manage communication between UI, use cases, and repositories?

**Key answers:**

- UI dispatches events to BLoC; BLoC calls use-cases; use-cases depend on repository interfaces; repositories implement remote/local sources.
- Keep mapping between DTO ↔ domain ↔ UI models explicit.
- Test: unit tests for use-cases and BLoCs; integration tests for repository behavior.
