# Dynamic Programming

## Dynamic programming concept

Break down a problem in smaller parts and store the results of these subproblems so that they only need to be computed once

A DP algorithm will search through all of the possible subproblems (main difference with greedy algorithms)

Based on either:
- Memoization (top-down)
- Tabulation (bottom-up)

[#dynamicprogramming](dynamicprogramming.md)

## Memoization vs tabulation

Optimization technique to cache previously computed results

Used by dynamic programming algorithms

Memoization: top-down (start with a large, complex problem and break it down into smaller sub-problems)

```
f(x) {
	if (mem[x] is undefined)
		mem[x] = f(x-1) + f(x-2)
	return mem[x]
}
```

Tabulation: bottom-up (start with the smallest solution and then build up each solution until we arrive at the solution to the initial problem)

```
tabFib(n) {
	mem[0] = 0
	mem[1] = 1
	for i = 2...n
		mem[i] = mem[i-2] + mem[i-1]
	return mem[n]
}
```

[#dynamicprogramming](dynamicprogramming.md)