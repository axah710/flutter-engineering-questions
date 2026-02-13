# Analytics in lifecycle

**Q:** Product wants to add analytics that track when a user opens, backgrounds, and kills the app. How would you integrate this into the Flutter lifecycle without polluting the UI code?

**Key answers:**

- Create an Analytics service and a Lifecycle observer (e.g., WidgetsBindingObserver) that publishes lifecycle events to the service.
- Keep UI clean: screens send "screen viewed" events; app-level lifecycle is centralized in one place (root widget / app bootstrap).
- Gate by consent and environment (disable verbose analytics in dev).
