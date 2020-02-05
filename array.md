# Array

## Algorithm to reverse an array

```java
int i = 0;
int j = a.length - 1;
while (i < j) {
	swap(a, i++, j--);
}
```

[#array](array.md)

## Array complexity: access, search, insert, delete

Access: O(1)

Search: O(n)

Insert: O(n)

Delete: O(n)

[#array](array.md) [#complexity](complexity.md)

## Binary search in a sorted array algorithm

```java
int lo = 0, hi = a.length - 1;

while (lo <= hi) {
	int mid = lo + ((hi - lo) / 2);
	if (a[mid] == key) {
		return mid;
	}
	if (a[mid] < key) {
		lo = mid + 1;
	} else {
		hi = mid - 1;
	}
}
```

### Further Reading

- [Nearly All Binary Searches and Mergesorts are Broken](https://ai.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html) by the Google AI Blog

[#array](array.md)

## Find an element in a rotated sorted array

Solution: binary search

Check first if the array is rotated. If not, apply normal binary search

If rotated, find pivot (smallest element, only element whose previous is bigger)

Then, check if the element is in 0..pivot-1 or pivot..len-1

```java
int findElementRotatedArray(int[] a, int val) {
	// If array not rotated
	if (a[0] < a[a.length - 1]) {
		// We apply the normal binary search
		return binarySearch(a, val, 0, a.length - 1);
	}

	int pivot = findPivot(a);

	if (val >= a[0] && val <= a[pivot - 1]) {
		// Element is before the pivot
		return binarySearch(a, val, 0, pivot - 1);
	} else if (val >= a[pivot] && val < a.length - 1) {
		// Element is after the pivot
		return binarySearch(a, val, pivot, a.length - 1);
	}
	return -1;
}
```

[#array](array.md)

## Given an array, move all the 0 to the left while maintaining the order of the other elements
   
Example: 1, 0, 2, 0, 3, 0 => 0, 0, 0, 1, 2, 3

Two pointers technique: read and write starting at the end of the array

If read is on a 0, decrement read. Otherwise swap, decrement both

```java
public void move(int[] a) {
	int w = a.length - 1, r = a.length - 1;
	while (r >= 0) {
		if (a[r] == 0) {
			r--;
		} else {
			swap(a, r--, w--);
		}
	}
}
```

Time complexity: O(n)

Space complexity: O(1)

[#array](array.md)

## How to detect if an element is a pivot in a rotated sorted array

Only element whose previous is bigger (also the pivot is the smallest element)

[#array](array.md)

## How to find a pivot element in a rotated array

Check first if the array is rotated

Then, apply binary search (comparison with a[right] to know if we go left or right)

```java
int findPivot(int[] a) {
	int left = 0, right = a.length - 1;

	// Array is not rotated
	if (a[left] < a[right]) {
		return -1;
	}

	while (left <= right) {
		int mid = left + ((right - left) / 2);
		if (mid > 0 && a[mid] < a[mid - 1]) {
			return a[mid];
		}

		if (a[mid] < a[right]) {
			// Pivot is on the left
			right = mid - 1;
		} else {
			// Pivot is on the right
			left = mid + 1;
		}
	}

	return -1;
}
```

[#array](array.md)

## How to find the duplicates in an array

- Hashtable
- Sorting the array then iterating over each element and check if previous = current

[#array](array.md)

## How to manage a dynamic array

When full, create a new array of twice the size, copy items (System.arraycopy is optimized for that)

Shrink: 
- Not when one-half full (otherwise worst case is too expensive: double-shrink-double-shrink etc.)
- Solution: one-quarter full

[#array](array.md)

## How to test if the array is sorted in ascending or descending order

Test first and last element (no iteration)

[#array](array.md)

## Rotate an array by n elements (n can be negative)
   
Example: 1, 2, 3, 4, 5 with n = 3 => 3, 4, 5, 1, 2

- Reverse the initial array
- Reverse from 0 to n-1
- Reverse from n to len - 1

```java
void rotateArray(List<Integer> a, int n) {
	if (n < 0) {
		n = a.size() + n;
	}

	reverse(a, 0, a.size() - 1);
	reverse(a, 0, n - 1);
	reverse(a, n, a.size() - 1);
}
```

Time complexity: O(n)

Memory complexity: O(1)

[#array](array.md)
