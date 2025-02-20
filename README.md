# Stale Closures in useEffect with setInterval

This example demonstrates a common issue in React when using the `useEffect` hook with `setInterval`.  If you don't properly handle updates within the `setInterval` callback, you might encounter stale closures, leading to unexpected behavior.

The `bug.js` file shows the problematic code. The `bugSolution.js` file presents the corrected version.

**Problem:** The original code creates a closure over the `setCount` function from the initial render.  Subsequent renders will have a different `setCount` function, but the `setInterval` callback still uses the old one, resulting in incorrect state updates.

**Solution:** The solution uses a functional update with `setCount(prevCount => prevCount + 1)`. This ensures that the update uses the latest state value.