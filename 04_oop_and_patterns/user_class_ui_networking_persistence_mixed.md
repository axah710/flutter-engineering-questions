# User class with UI, networking, persistence mixed

**Q:** In your project, a "User" class has fields and methods related to UI, networking, and persistence all together. Explain how you'd analyze this design and refactor it using OOP concepts to separate responsibilities.

**Key answers:**

- Split by responsibility: User (domain entity), UserDto (API mapping), UserRepository (data access), UserViewModel (UI state).
- Apply encapsulation: keep invariants in the domain entity; keep serialization/parsing outside.
- Reduce coupling by introducing interfaces for repositories/services and injecting them.
