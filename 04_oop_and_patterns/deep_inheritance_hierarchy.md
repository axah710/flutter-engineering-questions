# Deep inheritance hierarchy

**Q:** You see a deep inheritance hierarchy (BaseWidget → AppWidget → SpecialWidget → SpecialWidgetWithLogging). How would you restructure this using composition to make it easier to maintain?

**Key answers:**

- Replace inheritance with composable widgets and decorators (e.g., wrap a widget with a logging wrapper).
- Extract cross-cutting concerns (logging, analytics, theming) into wrappers/mixins only when truly necessary.
- Prefer small widgets + shared utilities over "god base classes."
