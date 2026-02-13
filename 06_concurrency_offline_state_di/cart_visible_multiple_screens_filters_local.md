# Cart visible on multiple screens; filters local to one

**Q:** In a shopping app, the cart must be visible and up to date on multiple screens, while some filters are local to one screen. How would you scope local vs global state and which tools would you pick?

**Key answers:**

- Cart: global state (app-level store/repository) with persistence; filters: local state in the screen/store scoped to that feature.
- Choose a tool consistent with team: Provider/Riverpod for simpler reactive state, BLoC for event/state rigor.
- Keep derived state (totals, availability) computed from cart state, not duplicated.
