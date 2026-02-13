# Custom plugin crashes when switching screens

**Q:** You are building a custom plugin and the app sometimes crashes when switching between screens using that plugin. How would knowledge of engine/framework/embedder layers influence your debugging strategy?

**Key answers:**

- Identify where the crash lives: Dart framework code vs platform channel vs native code (Android/iOS) vs engine-level rendering.
- Add structured logging around plugin calls, lifecycle attach/detach, and resource cleanup when routes change.
- Validate thread rules and object lifetimes on native side (e.g., release camera/location handles on onPause/onStop and plugin detach).
