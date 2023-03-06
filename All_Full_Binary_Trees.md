---
title: All Full Binary Trees
---

# Problem

Find all [full binary trees](Full_Tree.md) which contain $N$ nodes.

# Algorithm

| Complexity |          |
| ---------- | -------- |
| Time       | $O(2^N)$ |
| Space      | $O(2^N)$ |

## Intuition

The number of possible permutations of full binary trees with $k+1$ leaves, or $k$ internal nodes, is given by the $k^\text{th}$ [Catalan number](Catalan_Number.md), $C_k$.

In a tree with $k$ internal nodes, the total number of nodes, $N$, is given by $N=2k+1$. Thus, there are $C_k$ different permutations of full binary trees with $N$ nodes.

The algorithm is based on the fact that if $fullBinaryTrees(N)$ is a function that returns a set of all full binary trees with $N$ nodes, we have the recursive relationship:

$$
\begin{align}
fullBinaryTrees(N) = \{Tree(l, r) :\ & l\in fullBinaryTrees(x),\\ 
& r\in fullBinaryTrees(N-x-1), \\
& x\in\{y:\ 1\leq y\leq N-2, y \text{ is odd}\} ,
\end{align}
$$

where $Tree(x,y)$ is a function that produces a binary tree with $x$ and $y$ as the left and right sub-trees of the root node respectively.

This algorithm will have to construct every full binary tree consisting of $m$ nodes for $m$ between $1$ and $N$, and store these results. Each time a tree is constructed, it is only an $O(1)$ operation as the left and right sub-trees of the root node have already been computed.

Thus the space and time complexity is given by

$$
O\left(\sum_{i=0}^{N/2}C_{2k+1}\right) \sim O\left(\sum_{i=0}^{N/2}\frac{4^i}{i^{3/2}\sqrt{\pi}}\right)\sim O\left(4^{N/2}\right)\sim O(2^N)
$$

See [OEIS] and [Wikipedia][Catalan Number] for the approximation of the Catalan number used above.

## Implementation

Below is an implementation in `C++`, note that the returned trees share parents so as to save space. 

```cpp
vector<TreeNode*> allPossibleFBT(int n) {
	if (n%2==0 || n < 1) return vector<TreeNode*>();
	unordered_map<int, vector<TreeNode*>> cache;
	allPossibleFBTInner(cache, n);
	return cache[n];
}

void allPossibleFBTInner(
	unordered_map<int, vector<TreeNode*>> &cache, 
	int n
	) {
	if (n == 1) {
		TreeNode* root = new TreeNode(0);
		cache[1] = {root};
		return;
	}

	allPossibleFBTInner(cache, n-2);

	cache[n] = vector<TreeNode*>();

	for (int n1 = 1, n2 = n-2; n1 <= n-2; n1+=2, n2-=2) {
		for (auto &l : cache[n1]) {
			for (auto &r : cache[n2]) {
				TreeNode* root = new TreeNode(0);
				root->left = l;
				root->right = r;
				cache[n].push_back(root);
			}
		}
	}
}
```

[OEIS]: https://oeis.org/A014137

[Catalan Number]: https://en.wikipedia.org/wiki/Catalan_number
