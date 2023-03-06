---
title: Catalan Number
---

[Wikipedia]: https://en.wikipedia.org/wiki/Catalan_number

[OEIS]: https://oeis.org/A000108

# Definition

> In combinatorial mathematics, the Catalan numbers are a sequence of natural numbers that occur in various counting problems, often involving recursively defined objects. They are named after the French-Belgian mathematician Eugène Charles Catalan (1814–1894).

- [Wikipedia]

The $n^{th}$ Catalan number can be expressed directly in terms of binomial coefficients by

$$
C_{n}={\frac {1}{n+1}}{2n \choose n}={\frac {(2n)!}{(n+1)!\,n!}}=\prod \limits _{k=2}^{n}{\frac {n+k}{k}}\qquad {\text{for }}n\geq 0.
$$

Defined in [OEIS] as sequence _A000108_.

# Properties

The $n^{th}$ Catalan number can be approximated as,

$$
C_{n}\sim {\frac {4^{n}}{n^{3/2}{\sqrt {\pi }}}}.
$$

# Applications

- $C_k$ is the number of permutations of full binary trees with $k$ internal (non-leaf) nodes.
