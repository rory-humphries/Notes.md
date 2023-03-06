---
title: Singly Linked List
alias: Linked List
tags:
  - Data_Type
---

# Definition

A **singly linked list**, or just often called linked list, is a linear collection of objects or nodes, which together represent a sequence. Each node contains data and a reference to the next node in the sequence.

# Terminology

The first node is referred to as the **head** and any node past the head, or the last node, is referred to as the **tail**.

# Concepts

The last node of a singly linked list is usually identified by its reference to the next node being null.

A singly linked list data structure often only holds a reference to the head of the list. Sometimes the last node of the list is also stored.

# Examples

An example representation of a singly linked list of 4 nodes which hold an integer as their data:

| 2 | ---> | 5 | ---> | 33 | ---> | -4 | ---> | null |

# Implementation

A simple implementation of the data structures used to represent a singly linked list:

```cpp
struct node {
	int val;
	node *next;
}

struct linked_list {
	node *head;
}
```

# References

- <https://en.cppreference.com/w/cpp/container/forward_list>
