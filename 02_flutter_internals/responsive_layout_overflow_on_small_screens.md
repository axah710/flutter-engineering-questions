# Responsive layout overflow on small screens

**Q:** Designers give you a responsive layout that must look good from small phones to tablets. Your first implementation produces overflow errors on small screens. How do you reason about and redesign it using constraints so it behaves correctly everywhere?

**Key answers:**

- Start from constraints: remove fixed heights/widths where content can grow (text, lists).
- Use Flexible/Expanded, wrap vertical content with scrolling, and introduce breakpoints for tablet layouts.
- Validate with extreme cases: smallest device, largest text scale, split-screen.
