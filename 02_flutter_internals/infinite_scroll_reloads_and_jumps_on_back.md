# Infinite scroll reloads and jumps on back

**Q:** You implement an infinite scroll list, but when navigating back to the list from another screen, it reloads all items and jumps to the top. How would you adjust lifecycle and state handling to preserve position and data?

**Key answers:**

- Keep list state above the route (store/repository) so the screen can rebuild without refetching.
- Preserve scroll position with PageStorageKey (or keep controller in a longer-lived state holder).
- Implement caching/pagination properly (don't clear items on every initState).
