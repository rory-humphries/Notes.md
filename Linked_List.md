---
title: Linked List
tags:
  - Data_Type
---

# Definition

A **linked list** is a linear (or possibly circular) collection of objects or nodes, which together represent a sequence. Each node contains data and a reference to the next node in the sequence. The node may also contain additional data depending on the type of linked list, such as a reference to the previous node.

# Types of Linked List

- [Singly Linked List](Singly_Linked_List.md)
- [Doubly Linked List](Doubly_Linked_List.md)
- [Circular Linked List](Circular_Linked_List.md)

# Time Complexity of Operations

In the following, $N$ represents the number of nodes in the linked list.

| Operation | Time Complexity |
| --------- | --------------- |
| Insert    | $O(1)$          |
| Delete    | $O(1)$          |
| Search    | $O(N)$          |

Note that although insertions and deletions are $O(1)$, the search time to find the node to insert/delete often makes it $O(N)$. This coupled with poor cache locality can lead to poor performance if used incorrectly.

# References

- <https://en.wikipedia.org/wiki/Linked_list>
