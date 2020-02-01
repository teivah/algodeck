# Recursion

## How to handle a recursive function that need to return a list

Input:
- Result List
- Current iteration element

Output: void

```java
void f(List<String> result, String current) {
	// Do something
	result.add(...);
}
```

[#recursion](recursion.md)

## How to handle a recursive function that need to return a maximum value

Implementation: return max(f(a), f(b))

[#recursion](recursion.md)

## Loop inside of a recursive function?

Might be a code smell. The iteration is already brought by the recursion itself.

[#recursion](recursion.md)