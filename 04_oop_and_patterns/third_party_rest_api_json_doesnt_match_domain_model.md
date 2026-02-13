# Third-party REST API JSON doesn't match domain model

**Q:** You integrate a third-party REST API whose JSON does not match your app's domain model. How would you use a structural pattern to shield your code from this mismatch?

**Key answers:**

- Use Adapter + Mapper: convert API DTOs to domain entities in a dedicated layer.
- Keep third-party schema changes contained to DTO/mappers.
- Add contract tests for mapping.
