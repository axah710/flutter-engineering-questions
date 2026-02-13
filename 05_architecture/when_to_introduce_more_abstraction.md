# When to introduce more abstraction

**Q:** In a critical feature with complex business rules, going too simple makes the code unreadable. How do you decide when it is worth introducing more abstraction?

**Key answers:**

- Introduce abstraction when it reduces duplication and clarifies intent (use-cases, rule objects, policies).
- Prefer explicit domain modeling over generic helpers.
- Add tests first; complexity without tests becomes unmaintainable.
