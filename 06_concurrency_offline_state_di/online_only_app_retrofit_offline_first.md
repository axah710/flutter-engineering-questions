# Online-only app — retrofit offline-first

**Q:** Your existing online-only app starts getting complaints from users with unstable connections. How would you retrofit offline-first behavior without rewriting the entire app?

**Key answers:**

- Add caching at repository level (read from cache, refresh in background).
- Add request retry/backoff and partial offline modes per feature.
- Incrementally persist critical screens first (home, details, drafts).
