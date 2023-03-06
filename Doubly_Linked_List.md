---
title: Doubly Linked List
tags: 
  - Data_Type
---

# Definition

A **doubly linked list** is the same as a [[Singly_Linked_List|singly linked list]] with the added condition that each node also contains a reference to its previous node in the sequence.

# Concepts

The last node of a doubly linked list is usually identified by its reference to the next node being null and the [[Singly_Linked_List#Definition|head]] is identified by its reference to the previous node being null.

# Examples

An example representation of a doubly linked list of 4 nodes which hold an integer as their data:

| 2 | <-- --> | 5 | <-- --> | 33 | <-- --> | -4 | <-- --> | null |

# Advantages

The benefit of a doubly linked list is that it is far easier to traverse backwards from a given node without needing a reference to the head of the list.

# Implementation

A simple implementation of the data structures used to represent a doubly linked list:

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
