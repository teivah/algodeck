# Greedy

## Best-first search algorithm

Greedy solution (non-complete) to find the shortest path to a target node

Algorithm:
- Put initial state in a priority queue
- While target not reached: poll an element and inserts all neighbours

Priority is computed using the evaluation function: f(n) = h where h is an heuristic (local cost to visit a node)

[#greedy](greedy.md)

## Greedy algorithm

Algorithm paradigm of making the locally optimal choice at each stage using a heuristic function

A locally optimal function does not necesseraly mean to not have a global context for taking a decision

Never reconsider a choice (main difference with dynamic programming)

Solution found may not be the most optimal one

[#greedy](greedy.md)

## Greedy algorithm: structure

Often, the global context is spread into a priority queue

[#greedy](greedy.md)

## Greedy technique

Identify an optimal subproblem or substructure in the problem and determine how to reach it

Focus on what you have now (don't think about what comes next)

We may want to apply the traversal technique to have a global context for the identification part (a map of letters/positions etc.)

[#greedy](greedy.md) [#technique](technique.md)

## Technique - Optimization problems requiring a min or max

Greedy technique

[#greedy](greedy.md) [#technique](technique.md)