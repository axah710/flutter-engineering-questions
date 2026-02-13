# Service does API + JSON parsing into UI models

**Q:** A service class in your Flutter app both calls APIs and parses JSON into UI models. Bugs appear often after small changes. How would you apply SOLID principles to split and reorganize this code?

**Key answers:**

- Single Responsibility: separate API client, DTO parser/mapper, repository, and UI model mapping.
- Open/Closed: add new endpoints by adding new DTO + mapper, not by modifying existing unrelated code.
- Dependency Inversion: depend on interfaces (e.g., UserDataSource) rather than concrete HTTP clients.
