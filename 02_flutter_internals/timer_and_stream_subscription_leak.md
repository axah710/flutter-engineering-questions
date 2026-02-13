# Timer and stream subscription leak

**Q:** A screen creates a timer and a stream subscription, and after navigating away you see memory usage and CPU stay high. How do you use widget lifecycle knowledge to fix this leak?

**Key answers:**

- Track ownership: create in initState, cancel in dispose (timers, streams, controllers).
- Ensure async callbacks check mounted before calling setState.
- Use DevTools memory + allocation tracking to confirm the leak is gone.
