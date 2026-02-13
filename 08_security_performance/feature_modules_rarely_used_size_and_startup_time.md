# Feature modules rarely used — size and startup time

**Q:** Feature modules are rarely used but contribute heavily to size and startup time. How would you apply deferred loading or code splitting in Flutter to load them only when needed?

**Key answers:**

- Put rarely used features behind deferred imports and load on demand.
- Keep boundaries clean so deferred modules don't leak types everywhere.
- Add analytics to confirm modules are truly rarely used before optimizing.
