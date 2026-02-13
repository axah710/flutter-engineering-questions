# White-label / microkernel (plugin) style

**Q:** You are designing a core app that must be extended by different clients (white-label builds). How would you apply a microkernel (plug-in) style on the Flutter side?

**Key answers:**

- Define extension points (interfaces) for theming, feature toggles, and client-specific modules.
- Load client-specific implementations via DI + build-time flavors.
- Keep core stable and restrict what plugins can access.
