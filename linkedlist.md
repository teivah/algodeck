# Linked List

## Algorithm to reverse a linked list

```java
public ListNode reverse(ListNode head) {
	ListNode previous = null;
	ListNode current = head;

	while (current != null) {
		// Keep temporary next node
		ListNode next = current.next;
		// Change link
		current.next = previous;
		// Move previous and current
		previous = current;
		current = next;
	}

	return previous;
}
```

[#linkedlist](linkedlist.md)

## Doubly linked list

Each node contains a pointer to the previous and the next node

[#linkedlist](linkedlist.md)

## Doubly linked list complexity: access, insert, delete

Access: O(n)

Insert: O(1)

Delete: O(1)

[#complexity](complexity.md) [#linkedlist](linkedlist.md)

## Get the middle of a linked list

Using the runner technique

[#linkedlist](linkedlist.md)

## Iterate over two linked lists

```java
while (l1 != null || l2 != null) {
	
}
```

[#linkedlist](linkedlist.md)

## Linked list complexity: access, insert, delete

Access: O(n)

Insert: O(1)

Delete: O(1)

[#complexity](complexity.md) [#linkedlist](linkedlist.md)

## Linked list questions prerequisite

Single or doubly linked list?

[#linkedlist](linkedlist.md)

## Queue implementations and insert/delete complexity

1. Linked list with pointers on head and tail

Insert: O(1)

Delete: O(1)

2. Circular buffer if queue has a fixed size using a read and write pointer

Insert: O(1)

Delete: O(1)

[#linkedlist](linkedlist.md) [#queue](queue.md)

## Ring buffer (or circular buffer) structure

Data structure using a single, fixed-sized buffer as if it were connected end-to-end

[#linkedlist](linkedlist.md)

## What if we need to iterate backwards on a singly linked list in constant space without mutating the input?

Reverse the liked list (or a subpart only), implement the algo then reverse it again to the initial state

[#linkedlist](linkedlist.md) [#technique](technique.md)