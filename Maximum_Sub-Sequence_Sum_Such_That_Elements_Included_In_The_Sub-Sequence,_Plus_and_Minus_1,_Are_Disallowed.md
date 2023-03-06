---
title: Maximum Sub-Sequence Sum Such That Elements Included In The Sub-Sequence, Plus and Minus 1, Are Disallowed
---

# Problem

Given a [list](List_(Data_Type).md) of positive integers `nums`, find the maximum sum such that if `nums[i]` is included in the sum, all values `nums[i] + 1` and `nums[i] - 1` cannot be included.

This problem can be thought of as a rephrasing of the problem [Maximum Sum of Non-Consecutive Elements](Maximum_Sum_of_Non-Consecutive_Elements.md). If we take a new list `nums_sum`, where each element is its index times the number of times it appears in `nums`. In other words, `nums_sum[i] = k*i` where `k` is the number of times `i` appears in `nums`. Now we just have to find the maximum sum of non-consecutive elements on `nums_sum`.

In essence, this is the solution to the problem, however, we will alter the algorithm slightly to deal with the fact that in this case `nums_sum` is likely to contain many zeros.

# Approach 1

| Complexity |            |
| ---------- | ---------- |
| Time       | $O(N + k)$ |
| Space      | $O(N)$     |

Where `N` is the number of values in `nums` and `k` is the max value in `nums`.

## Intuition

The main point of this algorithm is understanding the recurrence relation. Suppose we have `nums_sum` as described above. Let `MaxSumUpTo(i)` be a function that returns the max sum according to the problem restrictions, for all values up to index `i` in `nums_sum`.

We have to two base cases such that `MaxSumUpTo(0)=num_sums[0]` and `MaxSumUpTo(1)=max(MaxSumUpTo(0), num_sums[1])`.Then we have the general relation that `MaxSumUpTo(i)=max(MaxSumUpTo(i-1), MaxSumUpTo(i-2) + num_sums[1])`. Using this relation we may build up to the final answer `MaxSumUpTo(k)`, where `k` is the max value in `nums`.

## Algorithm

1. Assume the list `nums` to have $O(1)$ random access.
2. Initialise a [Hash Map](Hash_Map.md), `nums_sum`.
3. Initialise `max_val=0`.
4. For every `i` in `nums`
   1. update `nums_sum` by `nums_sum[i]+=i`.
   2. `max_val=max(i, max_val)`.
5. Let `getOrDefault(nums_sum, i, val)` be a function that returns `nums_sum[i]` if the key exists, otherwise returns `val`.
6. Initialise `x1=getOrDefault(nums_sum, 0, 0)` and `x2=max(x1, getOrDefault(nums_sum, 1, 0))`
7. for `i = 2` up to `max_val`
   1. `tmp = x2`
   2. `x2 = max(x1 + getOrDefault(nums_sum, i, 0), x2)`
   3. `x1 = tmp`
8. Return `x2`.

A full implementation in `C++`:

```cpp
int maxSum(vector<int>& nums) {
	unordered_map<int, int> nums_sum;
	int max_val = 0;
	for (int &k: nums) {
		if (nums_sum.find(k) != nums_sum.end()) {
			nums_sum[k] += k;
		}
		else {
			nums_sum[k] = k;
			max_val = max(max_val, k);
		}
	}
	int x1, x2, tmp;
	x1 = getOrDefault(nums_sum, 1, 0);
	x2 = max(x1, getOrDefault(nums_sum, 2, 0));
	for (int i = 3; i <= max_val; i++) {
		tmp = x2;
		x2 = max(x1 + getOrDefault(nums_sum, i, 0), x2);
		x1 = tmp;
	}
	return x2;
}

int getOrDefault(unordered_map<int, int>& nums_sum, int k, int l) {
	if(nums_sum.find(k) != nums_sum.end()) return nums_sum[k];
	else return l;
}
```

# Approach 2

| Complexity |               |
| ---------- | ------------- |
| Time       | $O(N\log{N})$ |
| Space      | $O(N)$        |

#TODO

# References

- [Leet Code](https://leetcode.com/problems/delete-and-earn/solutions/1818112/delete-and-earn/)
