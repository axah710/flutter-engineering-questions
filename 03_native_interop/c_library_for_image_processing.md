# C library for image processing (offline, fast)

**Q:** You are given a C library for image processing that must run offline and be as fast as possible. Explain how you'd integrate it using Dart FFI and what precautions you'd take regarding safety and threading.

**Key answers:**

- Bind via dart:ffi so Dart can call native APIs directly.
- Treat memory safety as primary: validate buffer sizes, manage allocations carefully, and ensure correct struct alignment.
- Offload heavy work off the UI isolate (use isolates/message passing); isolates don't share memory and communicate by messages.
