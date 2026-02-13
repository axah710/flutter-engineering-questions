# Security, Privacy, Accessibility, Performance & App Size

## Security

### Banking feature — view transactions offline, sensitive ops online

**Q:** You are building a banking feature where users can view transactions offline but sensitive operations require connectivity. How would you apply security principles and OWASP guidance to design storage, encryption, and session handling?

**Key answers:**

- Store tokens securely and handle expiration; require re-auth for sensitive operations (OWASP mobile guidance).
- Encrypt sensitive offline data with authenticated encryption (GCM/CCM recommended).
- Separate "view-only offline" from "online-required actions" with server-side authorization and short session lifetimes.

---

### Sensitive tokens logged in debug builds

**Q:** After a security review, you learn that sensitive tokens are being logged in debug builds. Describe how you would clean this up and prevent similar issues in the future.

**Key answers:**

- Remove sensitive logs immediately and add automated log redaction in the logging layer.
- Add lint/code review rules: never log secrets; gate release builds with checks.
- Verify crash reporting scrubs PII and tokens.

---

### Jailbroken/rooted device detection

**Q:** You are asked to add jailbroken/rooted device detection. How would you implement it in Flutter and what would the app do when such a device is detected?

**Key answers:**

- Use a platform plugin/service that performs detection with best-effort signals (never 100% reliable).
- Respond with risk-based controls: block sensitive operations, require step-up auth, and show a clear warning.
- Log only non-sensitive security events for monitoring.

---

## Crypto Concepts

### User preferences — tamper detection

**Q:** You need to store user preferences locally and verify they have not been tampered with. Explain how you would combine hashing and/or digital signatures to achieve this.

**Key answers:**

- For tamper detection, store (data + HMAC) using a secret key stored in secure storage; verify on read.
- If you need non-repudiation or server-verifiable integrity, use digital signatures (private key signs, public key verifies).
- Use authenticated encryption modes (e.g., GCM) when confidentiality + integrity are both required.

---

### Backend wants E2E encryption — symmetric vs asymmetric

**Q:** The backend team wants the app to encrypt certain payloads end-to-end. How would you choose between symmetric and asymmetric encryption in this scenario?

**Key answers:**

- Use asymmetric crypto for key exchange/identity, symmetric crypto for bulk payloads (performance).
- Manage keys with a well-defined rotation and revocation strategy.
- Prefer standard, audited protocols over custom designs.

---

## Privacy

### Analytics tracks too much — privacy-by-design

**Q:** Your analytics implementation currently tracks too much data and possibly violates some privacy regulations. How would you redesign it to follow privacy-by-design and give users control over their data?

**Key answers:**

- Data minimization: collect only what you need, with short retention and clear purpose.
- Add consent controls and a privacy settings screen (opt-in where required).
- Anonymize/pseudonymize identifiers and avoid collecting sensitive attributes.

---

### EU and US markets — GDPR/CCPA

**Q:** The app will be used in both EU and US markets. How would you handle consent, data access, and deletion features to comply with GDPR/CCPA in the Flutter app?

**Key answers:**

- Implement consent flows, "download my data," and "delete my account/data" requests backed by server support.
- Provide region-aware prompts and keep audit logs server-side.
- Ensure third-party SDKs respect consent signals.

---

## Accessibility

### Unusable with screen readers

**Q:** QA reports that the app is almost unusable with screen readers. How would you go through a key screen and improve semantics, focus order, and labels using Flutter tools?

**Key answers:**

- Add semantic labels/roles for tappable elements, merge semantics where appropriate, and ensure logical traversal order.
- Fix focus management for dialogs/sheets and ensure keyboard navigation works.
- Add accessibility tests/checklists to PR reviews.

---

### Error messages hard to distinguish (color-blind)

**Q:** A color-blind user reports that error messages are difficult to distinguish from normal text. How would you adjust your design and implementation to fix this?

**Key answers:**

- Don't rely on color alone: add icons, text, and spacing; ensure sufficient contrast.
- Use theme tokens for error styling consistently across the app.
- Validate with color-blind simulators and contrast tools.

---

## Performance

### Home screen below 60 fps on mid-range devices

**Q:** After adding some animations and a complex list, your home screen drops below 60 fps on mid-range devices. How would you use Flutter DevTools to diagnose the cause and what changes might you make?

**Key answers:**

- Use DevTools Performance view: jank appears when frames exceed ~16 ms, which is the 60 FPS budget.
- Determine if it's build/layout (UI) or shader/paint (raster), then optimize accordingly (reduce rebuilds, cache, simplify effects).
- Apply targeted fixes: const widgets, smaller rebuild scopes, lazy loading, isolate heavy compute.

---

### Search flow consumes CPU and battery

**Q:** You see that a specific flow (e.g., searching large datasets) consumes a lot of CPU and battery. How would you optimize both the algorithm and the Flutter implementation?

**Key answers:**

- Optimize algorithm first (indexes, better search strategy, incremental results).
- Move heavy compute off UI isolate; isolates use message passing and don't share state.
- Cache results and avoid redundant work on every keystroke (debounce + incremental updates).

---

### Product detail page — many images, laggy scroll, memory growth

**Q:** On a product detail page with many images, scrolling becomes laggy and memory usage grows over time. How would you optimize rendering, use const widgets, and manage image caching to fix this?

**Key answers:**

- Reduce rebuilds (const where possible), use efficient list widgets, and limit expensive effects.
- Use appropriate image sizes/formats and cache policy; avoid decoding huge images for small thumbnails.
- Track memory in DevTools and fix leaks (controllers/subscriptions not disposed).

---

### Memory leak in long-running sessions

**Q:** A memory leak appears in long-running sessions; the app's memory steadily increases if left open. How would you use DevTools to detect the leak and what typical Flutter mistakes would you look for (e.g., controllers not disposed)?

**Key answers:**

- Take heap snapshots over time, watch retained objects, and identify growth patterns.
- Look for missing dispose, global singletons retaining context, and un-canceled streams/timers.
- Add regression tests and code review checks for lifecycle cleanup.

---

### Complex animation repaints entire screen

**Q:** You notice that a complex animation causes the entire screen to repaint, not just the changing part. How would you apply RepaintBoundary and other tricks to optimize this?

**Key answers:**

- Wrap the animated region with RepaintBoundary to isolate repaints.
- Reduce the animated subtree size and avoid triggering layout changes during animation.
- Prefer transform/opacity animations over re-layout heavy changes.

---

## Network & App Size

### Large images — data usage and slow loading

**Q:** Your app loads large images over mobile networks and users complain about data usage and slow loading. How would you optimize image formats, caching, and loading strategies to improve UX and reduce data usage?

**Key answers:**

- Serve responsive images (multiple sizes), modern formats, and enable CDN caching.
- Use placeholders and progressive loading; prefetch only when it improves UX.
- Cache with eviction and respect user settings (data saver).

---

### APK/IPA size grown due to dependencies

**Q:** The APK/IPA size has grown significantly due to added dependencies. How would you analyze the app size and then decide what to remove, split, or tree-shake to reduce it?

**Key answers:**

- Audit dependencies, remove unused ones, and replace heavy packages with lighter alternatives where feasible.
- Split features into modules/packages and avoid bundling unused assets.
- Verify tree-shaking works (avoid reflective/dynamic patterns that block it).

---

### Feature modules rarely used — size and startup time

**Q:** Feature modules are rarely used but contribute heavily to size and startup time. How would you apply deferred loading or code splitting in Flutter to load them only when needed?

**Key answers:**

- Put rarely used features behind deferred imports and load on demand.
- Keep boundaries clean so deferred modules don't leak types everywhere.
- Add analytics to confirm modules are truly rarely used before optimizing.
