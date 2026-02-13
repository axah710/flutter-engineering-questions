# Simple layered → Clean Architecture or feature modules?

**Q:** Your current app is a simple layered architecture (UI → logic → data), but you are starting to hit limitations with growing features. How would you decide whether to move to Clean Architecture, add feature modules, or keep the existing structure?

**Key answers:**

- Decide based on symptoms: duplication, unclear boundaries, test pain, feature coupling, build times.
- If features are independent domains, modularize by feature first; add Clean Architecture strictness only where complexity demands it.
- Run a pilot migration on one feature and measure outcome (velocity, defects).
