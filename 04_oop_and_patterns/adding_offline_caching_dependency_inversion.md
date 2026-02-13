# Adding offline caching (Dependency Inversion)

**Q:** You need to add offline caching to an existing data layer. How would you apply the Dependency Inversion Principle so that the UI is not directly dependent on details of local or remote storage?

**Key answers:**

- Define repository interfaces used by UI/use-cases; implement with RemoteDataSource + LocalCacheDataSource.
- Choose caching strategy (cache-aside, write-through) inside repository, not UI.
- Make storage swappable via DI (mock/in-memory for tests, SQLite/Isar for prod).
