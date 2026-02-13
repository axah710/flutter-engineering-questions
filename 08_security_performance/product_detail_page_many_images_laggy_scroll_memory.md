# Product detail page — many images, laggy scroll, memory growth

**Q:** On a product detail page with many images, scrolling becomes laggy and memory usage grows over time. How would you optimize rendering, use const widgets, and manage image caching to fix this?

**Key answers:**

- Reduce rebuilds (const where possible), use efficient list widgets, and limit expensive effects.
- Use appropriate image sizes/formats and cache policy; avoid decoding huge images for small thumbnails.
- Track memory in DevTools and fix leaks (controllers/subscriptions not disposed).
