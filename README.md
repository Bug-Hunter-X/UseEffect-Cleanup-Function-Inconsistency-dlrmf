# React useEffect Cleanup Function Issue

This repository demonstrates a subtle issue related to the cleanup function in React's `useEffect` hook.  The example shows a counter component where the effect's cleanup function should log a message.  Under certain conditions, this cleanup function may not be called consistently, potentially leading to unexpected behavior or resource leaks.

The `bug.js` file contains the problematic code.  The `bugSolution.js` file provides a corrected version.

## Problem:

The cleanup function in the `useEffect` hook is intended to run before the next effect execution, allowing for cleanup of resources such as timers, event listeners, or subscriptions. In this example, the cleanup function logs a message to the console. However, under certain conditions, this message may not appear, which indicates the cleanup function is not always being called. 

## Solution:

The solution involves ensuring that the effect's dependencies array accurately reflects all values used within the effect. By adding `count` to the dependency array, the effect re-runs whenever `count` changes, properly triggering the cleanup function before each subsequent execution.