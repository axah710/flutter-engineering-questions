# Multiple themes (light/dark/custom)

**Q:** Your app must support multiple themes (light/dark/custom) and you want to keep theme creation consistent. How would you use a creational pattern to manage this?

**Key answers:**

- Use a Factory/Builder to generate ThemeData from a small config (brand colors, typography).
- Keep theme tokens in one place; avoid scattering colors across widgets.
- Provide theme variants by environment/flavor and runtime user preference.
