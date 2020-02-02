# Heap

## Binary heap (min-heap or max-heap) complexity: insert, get min (max), delete min (max)

Insert: O(log (n))

Get min (max): O(1)

Delete min: O(log n)

[#complexity](complexity.md) [#heap](heap.md)

## Binary heap (min-heap or max-heap) data structure used for the implementation

Using an array

If children at index i:
- Left children: 2 * i + 1
- Right children: 2 * i + 2
- Parent: (i - 1) / 2

[#heap](heap.md)

## Binary heap (min-heap or max-heap) definition

A binary heap is a a complete binary tree with min-heap or max-heap property ordering. Also called min heap or max heap.

Min heap: each node smaller than its children, min value element at the root.

Two operations: insert(), getMin()

Difference BST: in a BST, each smaller element is on the left and greater element on the right, here a smaller element can be found on the left or the right side.

[#heap](heap.md)

## Binary heap (min-heap or max-heap) delete min

Replace min element (root) with the last node (left-most, lowest-level node because a binary heap is a complete binary tree)

If violations, swap with the smallest child (level by level)

[#heap](heap.md)

## Binary heap (min-heap or max-heap) insert algorithm

Insert node at the end (left-most spot because a binary heap is a complete binary tree)

If violations, swap with parents until no more violation

[#heap](heap.md)

## Binary heap (min-heap or max-heap) use-cases

Priority queue

[#heap](heap.md)

## Comparator implementation to order two integers

Ordering, min-heap: (a, b) -> a - b

Reverse ordering, max-heap: (a, b) -> b - a

[#general](general.md) [#heap](heap.md)

## Convert an array into a binary heap in place

For i from 0 to n-1, swap recursively element a[i] until min/max heap violation on its node

[#heap](heap.md)

## Find the median of a stream of numbers, 2 methods insert(int) and int findMedian()

Solution: two heap technique

Keep two heaps and maintain the balance by transfering an element from one heap to another if not balanced

Return the median (difference if even or odd)

```java
// First half
PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);
// Second half
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

public void insertNum(int n) {
	// First element
	if (minHeap.isEmpty()) {
		minHeap.add(n);
		return;
	}

	// Insert into min or max heap
	Integer minSecondHalf = minHeap.peek();
	if (n >= minSecondHalf) {
		minHeap.add(n);
	} else {
		maxHeap.add(n);
	}

	// Is balanced?
	if (minHeap.size() > maxHeap.size() + 1) {
		maxHeap.add(minHeap.poll());
	} else if (maxHeap.size() > minHeap.size() + 1) {
		minHeap.add(maxHeap.poll());
	}
}

public double findMedian() {
	// Even
	if (minHeap.size() == maxHeap.size()) {
		return (double) (minHeap.peek() + maxHeap.peek()) / 2;
	}

	// Odd
	if (minHeap.size() > maxHeap.size()) {
		return minHeap.peek();
	}
	return maxHeap.peek();
}
```

[#heap](heap.md)

## Given an unsorted array of numbers, find the K largest numbers in it

Solution: using a min heap but we keep only K elements in it

```java
public static List<Integer> findKLargestNumbers(int[] nums, int k) {
	PriorityQueue<Integer> minHeap = new PriorityQueue<>();

	// Put the first K numbers
	for (int i = 0; i < k; i++) {
		minHeap.add(nums[i]);
	}

	// Iterate on the rest of the array
	// Check whether the current element is bigger than the smallest one
	for (int i = k; i < nums.length; i++) {
		if (nums[i] > minHeap.peek()) {
			minHeap.poll();
			minHeap.add(nums[i]);
		}
	}

	return toList(minHeap);
}

public static List<Integer> toList(PriorityQueue<Integer> minHeap) {
	List<Integer> list = new ArrayList<>(minHeap.size());
	while (!minHeap.isEmpty()) {
		list.add(minHeap.poll());
	}

	return list;
}
```

Space complexity: O(k)

[#heap](heap.md)

## Heapsort algorithm

- Build a max heap from the array
- For i from n-1 to 0: 
1. Swap the largest element (at index 0) with i
2. Heapify the remaining elements (0.. i -1) by putting the root element at its correct position (keep swapping element with biggest child until there is a max heap violation on a node)

[#heap](heap.md) [#sort](sort.md)

## Is binary heap stable?

Stable

[#heap](heap.md)

## Time complexity to build a binary heap

O(n)

[#complexity](complexity.md) [#heap](heap.md)

## Two heaps technique

Keep two heaps:
- A max heap for the first half
- Then a min heap for the second half

May be required to balance them to have at most a difference in terms of size of 1

[#heap](heap.md) [#technique](technique.md)

## Why binary heap over BST for priority queue?

BST needs an extra pointer to the min or max value (otherwise finding the min or max is O(log n))

Implemented using an array: faster in practice (better locality, more cache friendly)

Building a binary heap is O(n), instead of O(n log n) for a BST

[#heap](heap.md)
