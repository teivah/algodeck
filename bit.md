# Bit

## & operator

AND bit by bit

[#bit](bit.md)

## << operator

Shift on the left

n * 2 <=> left shift by 1

n * 4 <=> left shift by 2

[#bit](bit.md)

## >> operator

Shift on the right

[#bit](bit.md)

## >>> operator

Logical shift (shift the sign bit as well)

[#bit](bit.md)

## ^ operator

XOR bit by bit

[#bit](bit.md)

## Bit vector structure

Vector (linear sequence of numeric values stored contiguously in memory) in which each element is a bit (so either 0 or 1)

[#bit](bit.md)

## Check exactly one bit is set

```java
boolean checkExactlyOneBitSet(int num) {
	return num != 0 && (num & (num - 1)) == 0;
}
```

[#bit](bit.md)

## Clear bits from i to 0

```java
int clearBitsFromITo0(int num, int i) {
	int mask = (-1 << (i + 1));
	return num & mask;
}
```

[#bit](bit.md)

## Clear bits from most significant one to i

```java
int clearBitsFromMsbToI(int num, int i) {
	int mask = (1 << i) - 1;
	return num & mask;
}
```

[#bit](bit.md)

## Clear ith bit

```java
int clearBit(final int num, final int i) {
	final int mask = ~(1 << i);
	return num & mask;
}
```

[#bit](bit.md)

## Flip ith bit

```java
int flipBit(final int num, final int i) {
	return num ^ (1 << i);
}
```

[#bit](bit.md)

## Get ith bit

```java
boolean getBit(final int num, final int i) {
	return ((num & (1 << i)) != 0);
}
```

[#bit](bit.md)

## How to flip one bit

b ^ 1

[#bit](bit.md)

## How to represent signed integers

Use the most significative bit to represent the sign. Yet, it is not enough (problem with this technique: 5 + (-5) != 0)

Two's complement technique: take the one complement and add one

-3: 1101

-2: 1110

-1: 1111

0:  0000

1:  0001

2:  0010

3:  0011

The most significant bit still represents the sign

Max integer value: 1...1 (31 bits)

-1: 1...1 (32 bits)

[#bit](bit.md)

## Set ith bit

```java
int setBit(final int num, final int i) {
	return num | (1 << i);
}
```

[#bit](bit.md)

## Update a bit from a given value

- Clear this bit
- Apply OR on the result with a 0 or 1 left shifted to its index

```java
int updateBit(int num, int i, boolean bit) {
	int value = bit ? 1 : 0;
	int mask = ~(1 << i);
	return (num & mask) | (value << i);
}
```

[#bit](bit.md)

## x & 0s

0

[#bit](bit.md)

## x & 1s

x

[#bit](bit.md)

## x & x

x

[#bit](bit.md)

## x ^ 0s

x

[#bit](bit.md)

## x ^ 1s

~x

[#bit](bit.md)

## x ^ x

0

[#bit](bit.md)

## x | 0s

x

[#bit](bit.md)

## x | 1s

1s

[#bit](bit.md)

## x | x

x

[#bit](bit.md)

## XOR operations

0 ^ 0 = 0

1 ^ 0 = 1

0 ^ 1 = 1

1 ^ 1 = 0

n XOR 0 => keep

n XOR 1 => flip

[#bit](bit.md)

## | operator

OR bit by bit

[#bit](bit.md)

## ~ operator

Complement bit by bit

[#bit](bit.md)