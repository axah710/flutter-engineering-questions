# Home screen below 60 fps on mid-range devices

**Q:** After adding some animations and a complex list, your home screen drops below 60 fps on mid-range devices. How would you use Flutter DevTools to diagnose the cause and what changes might you make?

**Key answers:**

- Use DevTools Performance view: jank appears when frames exceed ~16 ms, which is the 60 FPS budget.
- Determine if it's build/layout (UI) or shader/paint (raster), then optimize accordingly (reduce rebuilds, cache, simplify effects).
- Apply targeted fixes: const widgets, smaller rebuild scopes, lazy loading, isolate heavy compute.
