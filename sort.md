# Sort

## Bubble sort algorithm

Walk through a collection and compares 2 elements at a time

If they are out of order, swap them

Continue until the entire collection is sorted

[#sort](sort.md)

## Bubble sort complexity and stability

Time: O(n²)

Space: O(1)

Stable

[#complexity](complexity.md) [#sort](sort.md)

## Counting sort complexity, stability, use case

Time complexity: O(n + k) // n is the number of elements, k is the range (the maximum element)

Space complexity: O(k)

Stable

Use case: known and small range of possible integers

[#complexity](complexity.md) [#sort](sort.md)

## Counting sort algorithm

If range r is known

1) Create an array of size r where each a[i] represents the number of occurences of i

2) Modify the array to store the cumulative sum (if a=[1, 3, 0, 2] => [1, 4, 4, 6])

3) Right shift the array with a backward iteration (element at index 0 is 0 => [0, 1, 4, 4])
Now a[i] represents the first index of i if array was sorted

4) Create the sorted array by filling the elements from their first index

[#sort](sort.md)

## Heapsort algorithm

- Build a max heap from the array
- For i from n-1 to 0: 
1. Swap the largest element (at index 0) with i
2. Heapify the remaining elements (0.. i -1) by putting the root element at its correct position (keep swapping element with biggest child until there is a max heap violation on a node)

[#heap](heap.md) [#sort](sort.md)

## Heapsort complexity, stability, use case

Time: Theta(n log n)

Space: O(1)

Unstable

Use case: space constrained environment with O(n log n) time guarantee

Yet, not stable and not cache friendly

[#complexity](complexity.md) [#sort](sort.md)

## Insertion sort algorithm

From i to 0..n, insert a[i] to its correct position to the left (0..i)

Used by humans

[#sort](sort.md)

## Insertion sort complexity, stability, use case

Time: O(n²)

Space: O(1)

Stable

Use case: partially sorted structure

[#complexity](complexity.md) [#sort](sort.md)

## Mergesort algorithm

Splits a collection into 2 halves, sort the 2 halves (recursive call) then merge them together to form one sorted collection

```java
void mergeSort(int[] a) {
	int[] helper = new int[a.length];
	mergeSort(a, helper, 0, a.length - 1);
}

void mergeSort(int a[], int helper[], int lo, int hi) {
	if (lo < hi) {
		int mid = (lo + hi) / 2;

		mergeSort(a, helper, lo, mid);
		mergeSort(a, helper, mid + 1, hi);
		merge(a, helper, lo, mid, hi);
	}
}

private void merge(int[] a, int[] helper, int lo, int mid, int hi) {
	// Copy into helper
	for (int i = lo; i <= hi; i++) {
		helper[i] = a[i];
	}

	int p1 = lo; // Pointer on the first half
	int p2 = mid + 1; // Pointer on the second half
	int index = lo; // Index of a

	// Copy the smallest values from either the left or the right side back to the original array
	while (p1 <= mid && p2 <= hi) {
		if (helper[p1] <= helper[p2]) {
			a[index] = helper[p1];
			p1++;
		} else {
			a[index] = helper[p2];
			p2++;
		}
		index++;
	}

	// Copy the eventual rest of the left side of the array into the target array
	while (p1 <= mid) {
		a[index] = helper[p1];
		index++;
		p1++;
	}
}
```

### Further Reading

[Further reading](https://medium.com/omarelgabrys-blog/dynamic-connectivity-problem-9460f3dff2c6)