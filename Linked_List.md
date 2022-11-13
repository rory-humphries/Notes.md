---
title: Linked List
---

# Definition

A **(singly) linked list** is a linear collection of objects or nodes, which together represent a sequence. In its most basic form, each node contains: data, and a reference (in other words, a link) to the next node in the sequence. 

| 2 | ---> | 5 | ---> | 33 | ---> | -4 | ---> | null |

A linked list data structure usually only holds a reference to the first node in the list. The last node of the list is usually indicated by its refernce to the next node being null.

of the list is often given by some sort of null value. A simple implementation of the data structures which make up a linked list are below.

```C++
struct node {
	int val;
	node *next;
}

struct linked_list {
	node* head;
}
```

# Time Complexity of Operations

In the following, $N$ represents the number of nodes in the linked list.

| Operation | Time Complexity |
| --------- | --------------- |
| Insert    | $O(1)$          |
| Delete    | $O(1)$          |
| Search    | $O(N)$          |

Note that although insertions and deletions are $O(1)$, the search time to find the node to insert/delete often makes it $O(N)$. This coupled with poor cache locality can lead to poor performence if used incorrectly.

# Doubly Linked List

A **doubly linked list** is the same as a singly linked list with the exception that each node in the sequence contains a reference to the nodes *before* and after it in the sequence.

A simple implementation of the data structures which make up a doubly linked list are below.

```C++
struct node {
	int val;
	node *next;
	node *prev;
}

struct linked_list {
	node* head;
}
```

The benefit of a doubly linked list is that it is far easier to traverse backwards from a given node without needing a reference to the head of the list.

## Time Complexity of Operations

The time complexity of operations in doubly linked list is the same as that of a singly linked list.