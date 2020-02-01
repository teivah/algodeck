# Complexity

[Big-O Cheat Sheet](https://www.bigocheatsheet.com/)

## 0/1 Knapsack brute force complexity

Time complexity: O(2^n) with n the number of items

Space complexity: O(n)

[#complexity](complexity.md)

## 0/1 Knapsack memoization complexity

Time and space complexity: O(n * c) with n the number items and c the capacity

[#complexity](complexity.md)

## 0/1 Knapsack tabulation complexity

Time and space complexity: O(n * c) with n the number of items and c the capacity

Space complexity could even be improved to O(2*c) = O(c) as we need to store only the last 2 lines (using row%2):

```java
int[][] dp = new int[2][c + 1];
```

[#complexity](complexity.md)

## Amortized complexity definition

How much of a resource (time or memory) it takes to execute per operation on average

[#complexity](complexity.md)

## Array complexity: access, search, insert, delete

Access: O(1)

Search: O(n)

Insert: O(n)

Delete: O(n)

[#array](array.md) [#complexity](complexity.md)

## B-tree complexity: access, insert, delete

All: O(log n)

[#complexity](complexity.md) [#tree](tree.md)

## BFS and DFS graph traversal time and space complexity

Time: O(v + e) with v the number of vertices and e the number of edges

Space: O(v)

[#complexity](complexity.md) [#graph](graph.md)

## BFS and DFS tree traversal time and space complexity

BFS: time O(v), space O(v)

DFS: time O(v), space O(h) (height of the tree)

[#complexity](complexity.md) [#tree](tree.md)

## Big O

Upper bound

[#complexity](complexity.md)

## Big Omega

Lower bound (fastest)

[#complexity](complexity.md)

## Big Theta

Theta(n) if both O(n) and Omega(n)

[#complexity](complexity.md)

## Binary heap (min-heap or max-heap) complexity: insert, get min (max), delete min (max)

Insert: O(log (n))

Get min (max): O(1)

Delete min: O(log n)

[#complexity](complexity.md) [#heap](heap.md)

## BST complexity: access, insert, delete

If not balanced O(n)

If balanced O(log n)

[#complexity](complexity.md) [#tree](tree.md)

## BST delete algo and complexity

Find inorder successor and swap it

Average: O(log n)

Worst: O(h) if not self-balanced BST, otherwise O(log n)

[#complexity](complexity.md) [#tree](tree.md)

## Bubble sort complexity and stability

Time: O(n²)

Space: O(1)

Stable

[#complexity](complexity.md) [#sort](sort.md)

## Complexity of a function making multiple recursive subcalls

Time: O(branches^depth) with branches the number of times each recursive call branches (english: 2 power 3)

Space: O(depth) to store the call stack

[#complexity](complexity.md)

## Complexity to create a trie

Time and space: O(n * l) with n the number of words and l the longest word length

[#complexity](complexity.md)

## Complexity to insert a key in a trie

Time: O(k) with k the size of the key

Space: O(1) iterative, O(k) recursive

[#complexity](complexity.md) [#tree](tree.md)

## Complexity to search for a key in a trie

Time: O(k) with k the size of the key

Space: O(1) iterative or O(k) recursive

[#complexity](complexity.md) [#tree](tree.md)

## Counting sort complexity, stability, use case

Time complexity: O(n + k) // n is the number of elements, k is the range (the maximum element)

Space complexity: O(k)

Stable

Use case: known and small range of possible integers

[#complexity](complexity.md) [#sort](sort.md)

## Doubly linked list complexity: access, insert, delete

Access: O(n)

Insert: O(1)

Delete: O(1)

[#complexity](complexity.md) [#linkedlist](linkedlist.md)

## Hash table complexity: search, insert, delete

All: amortized O(1), worst O(n)

[#complexity](complexity.md) [#hashtable](hashtable.md)

## Heapsort complexity, stability, use case

Time: Theta(n log n)

Space: O(1)

Unstable

Use case: space constrained environment with O(n log n) time guarantee

Yet, not stable and not cache friendly

[#complexity](complexity.md) [#sort](sort.md)

## Insertion sort complexity, stability, use case

Time: O(n²)

Space: O(1)

Stable

Use case: partially sorted structure

[#complexity](complexity.md) [#sort](sort.md)

## Linked list complexity: access, insert, delete

Access: O(n)

Insert: O(1)

Delete: O(1)

[#complexity](complexity.md) [#linkedlist](linkedlist.md)

## Mergesort complexity, stability, use case

Time: Theta(n log n)

Space: O(n)

Stable

Use case: good worst case time complexity and stable, good with linked list

[#complexity](complexity.md) [#sort](sort.md)

## Quicksort complexity, stability, use case

Time: best and average O(n log n), worst O(n²) if the array is already sorted in ascending or descending order

Space: O(log n) // In-place sorting algorithm

Not stable

Use case: in practice, quicksort is often faster than merge sort due to better locality (not applicable with linked list so in this case we prefer mergesort)

[#complexity](complexity.md) [#sort](sort.md)

## Radix sort complexity, stability, use case

Time complexity: O(nk) // n is the number of elements, k is the maximum number of digits for a number

Space complexity: O(k)

Stable

Use case: if k < log(n) (for example 1M of elements from 0..1000 as 4 < log(1M)) 

[#complexity](complexity.md) [#sort](sort.md)

## Recursivity impacts on algorithm complexity

Space impact as each call is added to the call stack

Unless we use tail call recursion

[#complexity](complexity.md)

## Red-black tree complexity: access, insert, delete

All: O(log n)

[#complexity](complexity.md) [#tree](tree.md)

## Selection sort complexity

Time: Theta(n²)

Space: O(1)

[#complexity](complexity.md) [#sort](sort.md)

## Stack implementations and insert/delete complexity

- Linked list with a pointer on the head

Insert: O(1)

Delete: O(1)

- Array

Insert: O(n), amortized time O(1)

Delete: O(1)

[#complexity](complexity.md) [#stack](stack.md)

## Time complexity to build a binary heap

O(n)

[#complexity](complexity.md) [#heap](heap.md)

## Topological sort complexity

Time and space: O(v + e)

[#complexity](complexity.md) [#graph](graph.md)