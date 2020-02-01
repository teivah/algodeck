# General

## Before finding a solution

1) Make sure to understand the problem by listing:
- Inputs
- Outputs (what do we search)
- Constraints

2) Draw examples

[#general](general.md)

## Comparator implementation to order two integers

Ordering, min-heap: (a, b) -> a - b

Reverse ordering, max-heap: (a, b) -> b - a

[#general](general.md) [#heap](heap.md)

## Different ways for two intervals to relate to each other

7 ways:
1. a and b do not overlap
2. a and b overlap, b ends after a
3. a completely overlaps b
4. a and b overlap, a ends after b
5. b completely overlaps a
6. a and b do no overlap
7. a and b are equals

[#general](general.md)

## Different ways for two intervals to relate to each other if ordered by start then end

2 different ways:
- No overlap
- Overlap // Merge intervals (start of the first interval, max of the two ends)

[#general](general.md)

## Divide and conquer algorithm paradigm

1. Divide: break a given problem into subproblems of same type
2. Conquer: recursively solve these subproblems
3. Combine: combine the answers to solve the initial problem

Example with merge sort:
1. Split the array into two halves
2. Sort them (recursive call)
3. Merge the two halves

[#general](general.md)

## How to name a matrix indexes

Use m[row][col] instead of m[y][x]

[#general](general.md)

## If stucked on a problem

- Start with the smallest and easiest problem (e.g. 2 elements) and build a solution for that. Then, add elements and see if we can find a common pattern
- Greedy method
- Traversal technique

[#general](general.md)

## In place definition

Mutates an input

[#general](general.md)

## P vs NP problems

P (polynomial): set of problems that can be solved reasonably fast (example: multiplication, sorting, etc.)

Complexity is not exponential

NP (non-deterministic polynomial): set of problems where given a solution, we can test is it is a correct one in a reasonable amount of time but finding the solution is not fast (example: a 1M*1M sudoku grid, traveling salesman problem, etc)

NP-complete: hardest problems in the NP set

There are other sets of problems that are not P nor NP as an answer is really hard to prove (example: best move in a chess game)

P = NP means does being able to quickly recognize correct answers means there's also a quick way to find them?

[#general](general.md)

## Solving optimization problems

- Greedy method
- Dynamic programming (memoization or tabulation)
- Branch and bound (minimization problem only)

[#general](general.md)

## Stable property

Preserve the original order of elements with equal key

[#general](general.md)

## What do to after having designed a solution

Testing on nominal cases then edge cases

Time and space complexity

[#general](general.md)