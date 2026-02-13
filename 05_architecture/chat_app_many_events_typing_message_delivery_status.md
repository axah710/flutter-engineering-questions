# Chat app — many events (typing, message, delivery status)

**Q:** A chat application requires reacting to many events (typing, message received, delivery status). How would you leverage an event-driven style in your Flutter architecture to handle this?

**Key answers:**

- Model events as a stream and reduce them into state (event → reducer → new state).
- Use a single event pipeline per feature to avoid scattered subscriptions.
- Keep side effects (websocket, persistence) behind services/repositories.
