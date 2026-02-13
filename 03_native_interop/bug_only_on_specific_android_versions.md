# Bug only on specific Android versions

**Q:** A bug occurs only on specific Android versions when calling certain Java methods. How would your JNIgen setup and logging strategy help isolate and fix it?

**Key answers:**

- Add version/SDK logging, method argument logging (sanitized), and error code mapping to identify pattern by OS version.
- Create a minimal reproduction call path and run on emulators/device farm for those versions.
- If signature/overload mismatches exist, add explicit method selection and tests per API level.
