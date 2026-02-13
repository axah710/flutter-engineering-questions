# Dev, staging, production backends — flavors and config

**Q:** Your app must connect to dev, staging, and production backends with different keys and endpoints. How would you set up flavors and configuration management so switching environments is trivial for both developers and CI?

**Key answers:**

- Create dev/stage/prod flavors using Flutter flavor setup guides.
- Load endpoints/keys from build-time configuration (CI injects secrets; local uses non-secret defaults).
- Keep a single config interface in Dart so code doesn't branch everywhere.
