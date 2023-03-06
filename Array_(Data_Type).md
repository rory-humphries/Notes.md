---
title: Array (Data Type)
tags:
  - Data_Type
---

# Definition

An array, when discussed as an [abstract data type](Abstract_Data_Type.md) (ADT), represents an ordered collection of elements, where each of these elements may be accessed by an index, which is a k-tuple of integers.

The length of the tuple used to index is called the _dimension_, and represents the number of axes in the array.

Each axis, $j$, of the array has a minimum, $N_j$ and maximum, $M_j$, index associated with it. Then all valid indices of the array are $i=(i_1, i_2, \dots, i_k)\in[N_1, M_1]\times[N_2,M_2]\times\dots\times[N_k,M_k]$, and an element exists at each of these indices.

It is usually the case that $N_1=N_2=\dots=N_k$ and that they take the value 0 or 1 in order to represent the count along the axes. The 0 or 1 value depends on the programming language, for example, `C` uses 0 based arrays whereas `Julia` uses 1 based arrays.

Arrays in which all $N_j$'s are not equal, or they are not equal to 0 or 1, are often referred to as offset arrays.

# 1-Dimensional Arrays

When the dimension of the array is omitted, it is normally assumed to be 1 dimensional. Also in this case, the index may just be represented by an integer rather than tuple. Many languages only support 1-dimensional arrays as built in types.

# Comparison to List and Associative Array ADT's

An array ADT is simply an [Associative Array ADT](Associative_Array.md) with the restriction that the keys must be integers.

Also, an array ADT is often used to represent linear sequential data with indices representing there order in the sequence. This is the same as the definition of a [List ADT](List_(Data_Type).md).

# Operations

The following operations are usually implemented by an array ADT:

- `get(A,I)`:   Get the element at index `I`, where `I` is an integer or tuple of integers.
- `set(A,I,V)`: Set the element at index `I`, where `I` is an integer or tuple of integers, to value `V`.

# References

- [Wikipedia](https://en.wikipedia.org/wiki/Array_(data_type))
- [Brilliant](https://brilliant.org/wiki/arrays-adt/)
