# String

## First check to test if two strings are a permutation or a rotation of each other

Same length

[#string](string.md)

## How to print all the possible permutations of a string

Recursion with backtracking

```java
void permute(String s) {
	permute(s, 0);
}

void permute(String s, int index) {
	if (index == s.length() - 1) {
		System.out.println(s);
		return;
	}

	for (int i = index; i < s.length(); i++) {
		s = swap(s, index, i);
		permute(s, index + 1);
		s = swap(s, index, i);
	}
}
```

[#string](string.md)

## Rabin-Karp substring search

Searching a substring s in a string b takes O(s(b-s)) time

Trick: compute the hash of each substring s

Sliding window of size s

Time complexity: O(b)

If hash matches, check if the string are equals (as two different strings can have the same hash)

[#string](string.md)

## String permutation vs rotation

Permutation: contains the same characters in an order that can be different (abdc and dabc)

Rotation: rotates according to a pivot

[#string](string.md)

## String questions prerequisite

Case sensitive?

Encoding?

[#string](string.md)