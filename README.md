# Unexpected Re-renders with useCallback and Changing State Closures in React Native

This repository demonstrates a common issue in React Native when using the `useCallback` hook with functions that close over state variables.  The `useCallback` hook is meant to optimize performance by memoizing functions, but if the function's dependencies change on every render (due to a changing state value within the function), the memoization is ineffective, leading to unnecessary re-renders.

The `UnexpectedRerenders.js` file shows the buggy implementation, and `UnexpectedRerendersSolution.js` provides a corrected version.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on an emulator or device.
4. Observe the console logs – you'll see the function being called multiple times unnecessarily in the buggy example.

## Solution

The solution involves restructuring the code to avoid the closure over the changing state variable.  By passing the state value as an argument to the function and using it as a dependency for useCallback, we ensure that the function is only recreated when the state value actually changes.