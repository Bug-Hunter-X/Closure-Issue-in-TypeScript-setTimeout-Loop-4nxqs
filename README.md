# TypeScript Closure Issue in setTimeout Loop

This repository demonstrates a common closure-related issue in TypeScript when using `setTimeout` within a loop.  The problem arises because the `setTimeout` callback function closes over the loop variable `i`, which is not immediately evaluated, leading to unexpected results.

## Bug

The `printNumbers2` function intends to print numbers from 1 to `n` with a slight delay using `setTimeout`. However, due to the asynchronous nature of `setTimeout` and the closure, all callbacks will use the final value of `i` (which is `n+1`).

## Solution

The solution involves creating a new scope for each iteration using an immediately invoked function expression (IIFE) to capture the current value of `i`. This ensures that each callback has its own copy of `i`.