# Complex Java SDK for streaming video (Android)

**Q:** You must integrate a complex Java SDK on Android that handles streaming video. Explain how you'd use JNIgen to generate bindings and how you'd design the Dart side to manage callbacks, threads, and lifecycle safely.

**Key answers:**

- Generate bindings for the minimal surface area needed; avoid exposing the whole SDK by default.
- Route callbacks into a controlled Dart event stream; ensure you manage subscription lifecycles (start/stop on route changes).
- Carefully model threading: don't do heavy work in callbacks; buffer events and process off UI isolate when needed.
