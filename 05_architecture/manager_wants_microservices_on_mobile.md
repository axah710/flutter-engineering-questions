# Manager wants "microservices" on mobile

**Q:** A manager wants to "adopt microservices" and asks you to change the mobile architecture to match. How do you respond and what architecture would you propose for the Flutter client?

**Key answers:**

- Explain that microservices are backend deployment; the mobile client should optimize for UX, offline, and maintainability.
- Propose a client architecture with repositories/use-cases and a cohesive local domain model (don't mirror backend service boundaries blindly).
- Use API gateway/BFF patterns server-side if needed to simplify mobile.
