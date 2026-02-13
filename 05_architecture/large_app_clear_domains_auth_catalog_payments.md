# Large app with clear domains (auth, catalog, payments)

**Q:** You are building a large app with clear domains (auth, catalog, payments). How would you apply a layered architecture and when would you consider splitting into modules or plugins?

**Key answers:**

- Use per-domain feature modules with internal layers; expose only public APIs between domains.
- Split into separate packages when compile times, ownership, or release cadence require it.
- Create shared "core" packages for networking, analytics, and design system.
