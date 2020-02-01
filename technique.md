# Technique

[14 Patterns to Ace Any Coding Interview Question](https://medium.com/hackernoon/14-patterns-to-ace-any-coding-interview-question-c5bb3357f6ed#7cb6) by Fahim ul Haq

## 0/1 Knapsack brute force technique

Recursive approach: solve f(c, i) with c is the remaining capacity and i is th current item index
At each level, we branch with the item at index i (if enough capacity) and without it

```java
public int knapsack(int[] profits, int[] weights, int c) {
	return knapsack(profits, weights, c, 0, 0);
}

public int knapsack(int[] profits, int[] weights, int c, int i, int sum) {
	if (i == profits.length || c <= 0) {
		return sum;
	}

	// Not
	int sum1 = knapsack(profits, weights, c, i + 1, sum);

	// With
	int sum2 = 0;
	if (weights[i] <= c) {
		sum2 = knapsack(profits, weights, c - weights[i], i + 1, sum + profits[i]);
	}

	return Math.max(sum1, sum2);
}
```

[#technique](technique.md)

## 0/1 Knapsack memoization technique

Memoization: store a[c][i] (c is the remaining capacity, i is the current item index)

As we need to store the 0 capacity, we have to init the array this way:

int[][] a = new int[c + 1][n] // n is the number of items

Time and space complexity: O(n * c)

```java
public int knapsack(int[] profits, int[] weights, int capacity) {
	// Capacity from 1 to n
	Integer[][] a = new Integer[capacity][profits.length];
	return knapsack(profits, weights, capacity, 0, 0, a);
}

public int knapsack(int[] profits, int[] weights, int capacity, int i, int sum, Integer[][] a) {
	if (i == profits.length || capacity == 0) {
		return sum;
	}

	// If value already exists, return 
	if (a[capacity - 1][i] != null) {
		return a[capacity][i];
	}

	// With
	int sum1 = knapsack(profits, weights, capacity, i + 1, sum, a);
	// Without
	int sum2 = 0;
	if (weights[i] <= capacity) {
		sum2 = knapsack(profits, weights, capacity - weights[i], i + 1, sum + profits[i], a);
	}

	a[capacity - 1][i] = Math.max(sum1, sum2);
	return a[capacity - 1][i];
}
```

[#technique](technique.md)

## 0/1 Knapsack tabulation technique

Two dimensional array: a[n + 1][c + 1] // n the number of items and c the max capacity 

First row and first column are set to 0

a[row][col] represent the max profit with items 1..row at capacity col

remainingWeight = col - itemWeight // col: current max capacity

a[row][col] = max(a[row - 1][col], itemValue + a[row - 1][remainingWeight]) // max between item not selected and item selected + max remaining weight

If remainingWeight < 0, we can't chose the item so a[row][col] = a[row - 1][col]

Return last element of the array

```java
public int solveKnapsack(int[] profits, int[] weights, int capacity) {
	int[][] a = new int[profits.length + 1][capacity + 1];

	for (int row = 1; row < profits.length + 1; row++) {
		int value = profits[row - 1];
		int weight = weights[row - 1];
		for (int col = 1; col < capacity + 1; col++) {
			int remainingWeight = col - weight;
			if (remainingWeight < 0) {
				a[row][col] = a[row - 1][col];
			} else {
				a[row][col] = Math.max(
						a[row - 1][col],
						value + a[row - 1][remainingWeight]
				);
			}
		}
	}

	return a[profits.length][capacity];
}
```

If we need to compute a result like "determine if a subset exists" that return a boolean, the array type is boolean[][]

As we are only interested in the previous row, we can also use an int[2][n] array

[#technique](technique.md)

## Backtracking technique

Solution for solving a problem recursively

Loop:
- apply() // Apply a change
- try() // Try a solution
- reverse() // Reverse apply

[#technique](technique.md)

## Cyclic sort technique

Iterate over each number of an array and swap it to its correct position

At the end, we may iterate on the array to check which number is not at its correct position

If numbers are not within the 1 to n range, we can simply drop them

Alternative: marker technique (mark a result by setting a[i] to negative for example)

[#technique](technique.md)

## Greedy technique

Identify an optimal subproblem or substructure in the problem and determine how to reach it

Focus on what you have now (don't think about what comes next)

We may want to apply the traversal technique to have a global context for the identification part (a map of letters/positions etc.)

[#greedy](greedy.md) [#technique](technique.md)

## K-way merge technique

Given K sorted array, technique to perform a sorted traversal of all the elements of all arrays

- First, push the first element of each array in a min heap
- While min heap not empty, take min element and push the next element of the same array

We need to keep track of which structure the min element come from (tracking the array index or taking the next node if it's a linked list)

[#technique](technique.md)

## Runner technique

Iterate over the linked list with two pointers simultaneously either with:
- One ahead by a fixed amount
- One faster

This technique can also be applied on other problems where we need to find a cycle (f(slow) and f(f(fast)) may converge)

[#technique](technique.md)

## Simplification technique

Simplify the problem. If solvable, generalize to the initial problem.

Example: sort the array first

[#technique](technique.md)

## Sliding window technique

Range of elements in a specific window size

Two pointers left and right:
- Move right while condition is valid
- Move left if condition is not valid

[#technique](technique.md)

## Subsets technique

Technique to find all the possible permutations or combinations

Start with an empty set, for each element of the input, add them to all the existing subsets to create new subsets

Example:
- Given [1, 5, 3]
- => [] // Start
- => [], [1]
- => [], [1], [5], [1,5]
- => [], [1], [5], [1,5], [3], [1,3], [1,5,3]

For each level, we iterate from 0 to size // size is the fixed size of the list

```java
List<List<Integer>> findSubsets(int[] a) {
	List<List<Integer>> subsets = new ArrayList<>();
	// Add subset []
	subsets.add(new ArrayList<>());

	for (int n : a) {
		// Fix the current size
		int size = subsets.size();
		for (int i = 0; i < size; i++) {
			// Copy subset
			ArrayList<Integer> newSubset = new ArrayList<>(subsets.get(i));
			// Add element
			newSubset.add(n);
			subsets.add(newSubset);
		}
	}

	return subsets;
}
```

[#technique](technique.md)

## Technique - Dealing with cycles in a linked list or an array

Runner technique

[#technique](technique.md)

## Technique - Find all the permutations or combinations

Subsets technique or recursion + backtracking

[#technique](technique.md)

## Technique - Find an element in a sorted array or linked list

Binary search

[#technique](technique.md)

## Technique - Find or calculate something among all the contiguous subarrays of a given size

Sliding window technique

Example: 
- Given an array, find the average of all subarrays of size ‘K’ in it

[#technique](technique.md)

## Technique - Find the longest/shortest substring or subarray

Sliding window technique

Example:
- Longest substring with K distinct characters
- Longest substring without repeating characters

[#technique](technique.md)

## Technique - Find the smallest/largest/median element of a set

Two heaps technique

[#technique](technique.md)

## Technique - Finding a certain element in a linked list (e.g. middle)

Runner technique

[#technique](technique.md)

## Technique - Given a sorted array, find a set of elements that fullfill certain conditions

Two pointers technique

Example: 
- Given a sorted array and a target sum, find a pair in the array whose sum is equal to the given target
- Given an array of unsorted numbers, find all unique triplets in it that add up to zero
- Comparing strings containing backspaces

[#technique](technique.md)

## Technique - Given an array of size n containing integer from 1 to n (e.g. with one duplicate)

Cyclic sort technique

[#technique](technique.md)

## Technique - Given time intervals

Traversal technique

Iterate with two pointers, one over the starts, another one over the ends

Handle the element with the lowest value first and generate an event

Example: how many rooms for n meetings => meeting started, meeting started, meeting ended etc.

[#technique](technique.md)

## Technique - How to get the K biggest/smallest/frequent elements

Top K elements technique

[#technique](technique.md)

## Technique - Optimization problems requiring a min or max

Greedy technique

[#greedy](greedy.md) [#technique](technique.md)

## Technique - Problems featuring a list of sorted arrays (merge or find the smallest element)

K-way merge technique

[#technique](technique.md)

## Technique - Scheduling problem with n tasks where each task can have constraints to be completed before others

Topological sort technique

[#technique](technique.md)

## Technique - Situations like priority queue or scheduling

Heap data structure

Possibly two heaps technique

[#technique](technique.md)

## Top K elements technique (biggest and smallest)

Finding the K biggest elements:
- Min heap
- Add k elements
- Then iterate over the remaining elements, if current > min => remove min, add current

Finding the k smallest elements: 
- Max heap
- Add k elements
- Then iterate over the remaining elements, if current < max => remove max, add current

[#technique](technique.md)

## Topological sort technique

If there is an edge from U to V, then U <= V

Possible only if the graph is a DAG

Algo:
- Create a graph representation (adjacency list) and an in degree counter (Map<Integer, Integer>)
- Zero them for each vertex
- Fill the adjacency list and the in degree counter for each edge
- Add in a queue each vertex whose in degree count is 0 (source vertex with no parent)
- While the queue is not empty, poll a vertex from it then decrement the in degree of its children (no removal)

To check if there is a cycle, we must compare the size of the produced array to the number of vertices

```java
List<Integer> sort(int vertices, int[][] edges) {
	if (vertices == 0) {
		return Collections.EMPTY_LIST;
	}

	List<Integer> sorted = new ArrayList<>(vertices);
	// Adjacency list graph
	Map<Integer, List<Integer>> graph = new HashMap<>();
	// Count of incoming edges for each vertex
	Map<Integer, Integer> inDegree = new HashMap<>();

	for (int i = 0; i < vertices; i++) {
		inDegree.put(i, 0);
		graph.put(i, new LinkedList<>());
	}

	// Init graph and inDegree
	for (int[] edge : edges) {
		int parent = edge[0];
		int child = edge[1];

		graph.get(parent).add(child);
		inDegree.put(child, inDegree.get(child) + 1);
	}

	// Create a source queue and add each source (a vertex whose inDegree count is 0)
	Queue<Integer> sources = new LinkedList<>();
	for (Map.Entry<Integer, Integer> entry : inDegree.entrySet()) {
		if (entry.getValue() == 0) {
			sources.add(entry.getKey());
		}
	}

	while (!sources.isEmpty()) {
		int vertex = sources.poll();
		sorted.add(vertex);

		// For each vertex, we will decrease the inDegree count of its children
		List<Integer> children = graph.get(vertex);
		for (int child : children) {
			inDegree.put(child, inDegree.get(child) - 1);
			if (inDegree.get(child) == 0) {
				sources.add(child);
			}
		}
	}

	// Topological sort is not possible as the graph has a cycle
	if (sorted.size() != vertices) {
		return new ArrayList<>();
	}

	return sorted;
}
```

[#graph](graph.md) [#technique](technique.md)

## Traversal technique

Traverse the input and generate another data structure or optional events

Start the problem from this new state

[#technique](technique.md)

## Two heaps technique

Keep two heaps:
- A max heap for the first half
- Then a min heap for the second half

May be required to balance them to have at most a difference in terms of size of 1

[#heap](heap.md) [#technique](technique.md)

## Two pointers technique

Two pointers iterating through the data structure in tandem until one or both pointers hit a certain condition

Often useful when structure is sorted. If not sorted, we may want to sort it first.

Most of the times (not always): first pointer is at the start, the second pointer is at the end

The two pointers can also be on two different ds, still iterating in tandem (e.g. comparing strings containing backspaces)

Time complexity is linear

[#technique](technique.md)

## What if we need to iterate backwards on a singly linked list in constant space without mutating the input?

Reverse the liked list (or a subpart only), implement the algo then reverse it again to the initial state

[#linkedlist](linkedlist.md) [#technique](technique.md)
