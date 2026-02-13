# Services created with new Service() in widgets — need mocks

**Q:** The app currently creates services directly inside widgets with new Service(). You now need to mock those services in tests. How would you introduce DI so that existing code can be migrated gradually?

**Key answers:**

- Start by injecting services via constructors at feature boundaries (screens/controllers), with sensible defaults temporarily.
- Introduce a DI container or provider at the app root and route dependencies from there.
- Gradually remove new Service() from widgets; add tests that use mocks/fakes.
