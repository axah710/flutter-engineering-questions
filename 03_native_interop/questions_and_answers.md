# Native Interop: Platform Channel, FFI, FFIgen, JNIgen

## Platform Channel

_(See also 02_flutter_internals for scan document and iOS background location Q&As.)_

---

## Dart FFI

### C library for image processing (offline, fast)

**Q:** You are given a C library for image processing that must run offline and be as fast as possible. Explain how you'd integrate it using Dart FFI and what precautions you'd take regarding safety and threading.

**Key answers:**

- Bind via dart:ffi so Dart can call native APIs directly.
- Treat memory safety as primary: validate buffer sizes, manage allocations carefully, and ensure correct struct alignment.
- Offload heavy work off the UI isolate (use isolates/message passing); isolates don't share memory and communicate by messages.

---

### Platform channel + CPU-heavy C library causes UI stutter

**Q:** A previous developer uses platform channels to call a CPU-heavy C library. The UI stutters badly. How would you propose moving this to FFI and isolates to fix the problem?

**Key answers:**

- Replace repeated channel roundtrips with direct FFI calls for high-frequency compute.
- Run compute in a worker isolate so UI isolate stays responsive; isolates have isolated memory and message passing.
- Benchmark before/after (time per frame, CPU, battery), and keep a fallback path if native lib fails to load.

---

## FFIgen

### Large C API — hundreds of functions

**Q:** Your team wants to expose a large C API (hundreds of functions) to Flutter, and manually writing bindings is error-prone. Describe how you'd set up FFIgen in this project and how you'd keep the generated code in sync with the native library over time.

**Key answers:**

- Add ffigen config (headers, output, naming), generate bindings into a dedicated generated/ folder, and never hand-edit generated files.
- Pin native library versions and regenerate bindings as part of CI (or a controlled build step).
- Add compile-time + smoke tests that call a small subset of functions to detect breaking changes early.

---

### Native library update — some Dart calls fail

**Q:** After updating the native library, some Dart calls start failing. How would you use FFIgen and versioning strategy to safely roll out such updates?

**Key answers:**

- Version the native library and bindings together (semantic versioning); publish breaking changes only on major bumps.
- Maintain a compatibility layer in Dart (adapter) so app code doesn't change everywhere at once.
- Roll out with feature flags and staged releases; add runtime checks for library version if feasible.

---

## JNIgen

### Complex Java SDK for streaming video (Android)

**Q:** You must integrate a complex Java SDK on Android that handles streaming video. Explain how you'd use JNIgen to generate bindings and how you'd design the Dart side to manage callbacks, threads, and lifecycle safely.

**Key answers:**

- Generate bindings for the minimal surface area needed; avoid exposing the whole SDK by default.
- Route callbacks into a controlled Dart event stream; ensure you manage subscription lifecycles (start/stop on route changes).
- Carefully model threading: don't do heavy work in callbacks; buffer events and process off UI isolate when needed.

---

### Bug only on specific Android versions

**Q:** A bug occurs only on specific Android versions when calling certain Java methods. How would your JNIgen setup and logging strategy help isolate and fix it?

**Key answers:**

- Add version/SDK logging, method argument logging (sanitized), and error code mapping to identify pattern by OS version.
- Create a minimal reproduction call path and run on emulators/device farm for those versions.
- If signature/overload mismatches exist, add explicit method selection and tests per API level.
