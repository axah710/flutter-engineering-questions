# Poll API, transform, update UI in real time

**Q:** You need to poll an API, transform results, and update the UI in real time. How would you combine Futures, Streams, and cancellations to implement this robustly?

**Key answers:**

- Use a Stream pipeline: timer/trigger → async fetch → transform → emit state.
- Support cancellation (dispose cancels subscription) and debounce/backoff on failures.
- Keep state updates atomic so UI always reflects a consistent snapshot.
