# App lifecycle and resume crashes

**Q:** A newly released app crashes when users resume it after being in the background for a while. You suspect improper lifecycle handling. Walk through how you would investigate and adjust the app's code from planning to deployment to properly handle app and widget lifecycle.

**Key answers:**

- Reproduce in profile/release mode; inspect crash logs (Firebase Crashlytics / Play Console / Xcode devices).
- Audit lifecycle hooks: initState, dispose, didChangeAppLifecycleState, navigation callbacks; ensure timers/streams/controllers are paused/resumed/disposed safely.
- Add lifecycle-focused tests and logging around "resume" paths; ship a hotfix with defensive checks (nullability, mounted checks, retry logic) and monitor.
