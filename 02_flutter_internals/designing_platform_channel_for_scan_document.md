# Designing platform channel for "scan document"

**Q:** You need to use a native Android/iOS SDK that has no existing Flutter plugin. Describe how you would design a platform channel API for a "scan document" feature, handle errors, and keep the Dart side clean and testable.

**Key answers:**

- Design a small Dart-facing interface (DocumentScanner.scan() returning a typed result), with a clear method name + structured arguments.
- Normalize errors into domain errors (permission denied, canceled, unavailable, unknown) and map platform exceptions accordingly.
- Keep testability by injecting a channel adapter (mock in tests) and keeping UI unaware of platform details.
