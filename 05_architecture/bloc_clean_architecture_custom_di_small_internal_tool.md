# BLoC + Clean Architecture + custom DI for small internal tool

**Q:** A teammate proposes a very complex BLoC + Clean Architecture + custom DI setup for a small internal tool app. How would you evaluate this proposal and suggest a simpler alternative if appropriate?

**Key answers:**

- Evaluate by expected lifetime, team size, change rate, and risk.
- Suggest a simpler stack (e.g., Provider/Riverpod + repositories) with good testing, without heavy ceremony.
- Keep an "upgrade path" documented if the tool grows.
