# Reactive/declarative principles

**Q:** You join a project where developers think of Flutter as "just UI widgets" and keep adding imperative logic in callbacks. Features start breaking randomly. How would you explain and apply Flutter's reactive/declarative principles to reorganize this code?

**Key answers:**

- Explain: UI should be a pure function of state; callbacks only dispatch events that update state, then the UI rebuilds from that state.
- Move logic out of callbacks into a state layer (Notifier/BLoC/ViewModel), make state immutable (copy-with), and centralize side effects in a repository/service layer.
- Introduce predictable state transitions: events → reducer/handler → new state → render, plus tests on the transition logic.
