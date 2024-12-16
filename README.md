# React: Infinite Loading State Bug

This repository demonstrates a common bug in React components that fetch data: an infinite loading state.  The `MyComponent` fetches data from an API. If the fetch operation fails without throwing an explicit error (e.g., network timeout), the `loading` state remains `true` indefinitely, preventing the error state from being displayed.

## Bug Description

The provided code uses `useEffect` and `async/await` to fetch data. While it handles errors gracefully using a `try...catch` block, it fails to address scenarios where the `fetch` operation hangs indefinitely without resolving or rejecting. This leads to the UI stuck in the loading state.

## Solution

The solution utilizes a timeout mechanism in combination with the existing error handling to address the silent failure scenarios. If the fetch operation takes longer than a specified time, the timeout will trigger an error, thus updating the UI correctly.