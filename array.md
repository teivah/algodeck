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
	int mid = (low + high) / 2;
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

[#array](array.md)

## Find an element in a rotated sorted array

Solution: binary search

Check first if the array is rotated. If not, apply normal binary search

If rotated, **find pivot** (smallest element, only element whose previous is bigger)

Then, check if the element is in **0..pivot-1 or pivot..len-1**