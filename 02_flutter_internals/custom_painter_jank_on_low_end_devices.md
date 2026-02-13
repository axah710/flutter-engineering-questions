# CustomPainter jank on low-end devices

**Q:** You are building a custom chart using CustomPainter, and on low-end devices scrolling becomes noticeably janky. How would you analyze and adjust rendering to improve performance without removing key visuals?

**Key answers:**

- Identify if jank is on UI vs raster side using DevTools; slow frames over ~16 ms indicate jank.
- Cache precomputed paths/labels, minimize allocations in paint, and make shouldRepaint strict.
- Use RepaintBoundary, reduce overdraw, and consider pre-rendering static parts (only animate the minimal changing layer).
