# Widget adapts to changing parent constraints

**Q:** A widget must adapt to parent constraints that can change at runtime (e.g., split screen). Your current approach hardcodes sizes. Describe how you'd rework it so it reacts correctly to those changing constraints.

**Key answers:**

- Use LayoutBuilder to compute sizes from incoming constraints each build.
- Prefer relative sizing (fractions/aspect ratios) over absolute pixels.
- Keep expensive calculations memoized but invalidated when constraints change.
