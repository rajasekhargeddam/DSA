# Leetcode(225) Implement Stack using Queues

This problem requires implementing a **Last-In-First-Out (LIFO) stack** using only the standard operations of a queue. The stack must support the following operations:

- `push(x)`: push element `x` onto the stack
- `pop()`: remove and return the top element
- `top()`: return the top element without removing it
- `empty()`: return `true` if the stack is empty, otherwise `false`

Important constraint:
- Only queue operations are allowed: push to back, pop from front, peek from front, check size, and check emptiness.
- In JavaScript, a queue can be simulated using an array and only standard queue behavior.

## Example

Input:
`["MyStack", "push", "push", "top", "pop", "empty"]`

Operations:
- `MyStack()`
- `push(1)`
- `push(2)`
- `top()` → returns `2`
- `pop()` → returns `2`
- `empty()` → returns `false`

## Constraints

- `1 <= x <= 9`
- At most `100` calls to `push`, `pop`, `top`, and `empty`
- All calls to `pop` and `top` are valid

## Approaches

### Approach 1: Using Two Queues

This version maintains two queues, `q1` and `q2`.

- `push(x)`: enqueue `x` into `q1`
- `pop()`: move all elements from `q1` to `q2` except the last one, then dequeue and return the last element from `q1`. Swap `q1` and `q2`.
- `top()`: move all elements from `q1` to `q2` except the last one, dequeue the last element, enqueue it back into `q2`, then swap `q1` and `q2`. Return the saved element.
- `empty()`: check whether `q1` is empty

This approach uses two queues to preserve order and isolate the topmost element for stack behavior.

### Approach 2: Using One Queue

This version uses a single queue, `q1`, and rotates elements to simulate stack behavior.

- `push(x)`: enqueue `x` into `q1`
- `pop()`: rotate the queue by dequeuing and re-enqueuing elements until only the last pushed element remains at the front, then dequeue and return it.
- `top()`: perform the same rotation as `pop()`, but after removing the last element, immediately re-enqueue it so the queue remains intact. Return the saved element.
- `empty()`: check whether `q1` is empty

This approach is more space-efficient because it uses a single queue, but it still maintains the correct LIFO order by cyclic rotation.

## Files

- `withTwoQueues.js` — implementation using two queues
- `withOneQueue.js` — implementation using a single queue
