---
title: Intersection of intervals
---

# Problem

Given two intervals $[x_1,x_2]$ and $[y_1, y_2]$, the two intervals intersect if there exists some value $c$, such that $c\in[x_1,x_2]$ and $c\in[y_1, y_2]$.

This corresponds to the condition that 
$$
\begin{align}
x_1\leq &c\leq x_2\\
y_1\leq &c\leq y_2.
\end{align}
$$
The above inequality is false iff $y_2<x_1$ or $x_2<y_1$.

# Algorithm

The algorithm is straightforward and most efficiently implemented as the following:
The two intervals intersect if and only if
$$
x_1\leq y_2\ \land\ y_1\leq x_2.
$$