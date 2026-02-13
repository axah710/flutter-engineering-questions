# List laggy with real data

**Q:** A list screen becomes laggy once real production data is loaded, but works fine with mock data. The team only tweaks UI code and gets nowhere. How would your understanding of Flutter internals guide you to identify the real bottleneck?

**Key answers:**

- Profile with DevTools and separate "UI thread" vs "raster thread" slowness; frames over ~16 ms are considered janky, and 60 FPS requires ~16 ms per frame.
- Check data-side bottlenecks: JSON parsing, sorting, image decoding, and synchronous work on the UI isolate.
- Fix by reducing rebuild scope, virtualizing work (pagination), caching computations, and moving heavy transforms off the UI isolate.
