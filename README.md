# Firebase Authentication Listener Memory Leak
This repository demonstrates a common issue with Firebase's `onAuthStateChanged` listener: memory leaks caused by forgetting to unsubscribe.

The `authListenerBug.js` file shows the problematic code.  The solution is provided in `authListenerSolution.js`.

## Problem
The `onAuthStateChanged` listener is attached but never detached. This leads to a persistent listener even after the component or function using it unmounts or finishes execution, resulting in a memory leak and potential performance issues.

## Solution
The solution involves storing the return value of `onAuthStateChanged` in a variable and calling the `unsubscribe()` function when the listener is no longer needed.