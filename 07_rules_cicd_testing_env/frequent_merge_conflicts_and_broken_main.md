# Frequent merge conflicts and broken main

**Q:** Your team has frequent merge conflicts and broken main branch builds. How would you set up a Git workflow and CI for a Flutter app to minimize these issues?

**Key answers:**

- Use trunk-based or short-lived branches with PRs, required reviews, and required CI checks before merge.
- Run CI on PR: analyze, unit/widget tests, and at least one integration smoke test.
- Enforce small PRs and frequent rebases to reduce conflicts.
