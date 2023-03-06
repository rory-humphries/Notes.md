---
title: All Palindromic Sub-Strings of a String
---

# Problem

Find all sub-strings in a given string which are [palindromes](Palindrome.md).

# Example

Given the string `"abnabauyyuabap"`, each single character is a trivial palindrome. The non-trivial palindromic sub-strings in this string are:

- `"yy"`
- `"aba"`
- `"aba"`
- `"uyyu"`
- `"auyyua"`
- `"bauyyuab"`
- `"abauyyuaba"`

# Algorithm

The best time complexity in which this problem is solved is $O(N^2)$. The best space complexity with which this problem can be solved in $O(N^2)$ time complexity is $O(1)$.

## Dynamic Programming Approach

| Time Complexity | Space Complexity |
| --------------- | ---------------- |
| $O(N^2)$        | $O(N)$           |

This approach uses the fact that every palindrome is made from a smaller palindrome with two of the same characters prepended and appended respectively.

1. Given a string $S$, define the state $\text{is\_palin}(i,j)$, a 2-dimensional array of bool's initialised to false. This tells us whether the sub-string composed of the $i^{\text{th}}$ to the $j^{\text{th}}$ characters of the input string, is a palindrome or not.

2. There are two base-cases:

   - Single letter sub-strings are palindromes by definition. i.e. $\text{is\_palin}(i,i)= true$ for all $i$.
   - Double letter sub-strings composed of the same character are palindromes. i.e. $\text{is\_palin}(i,i+1) = true$ if $S(i)=S(i+1)$.

3. A string is considered a palindrome if:

   - Its first and last characters are equal, and
   - The rest of the string (excluding the boundary characters) is also a palindrome.

   This substructure can be formulated into a recurrence rule:

$$
is\_palin(i,j)=
\begin{cases}
	true \quad \text{if}\ is\_palin(i+1,j-1) = true \ \text{and}\ S(i) = S(j)\\
	false \quad \text{otherwise}
\end{cases}
$$

4. Starting from all sub-strings of length 3, determine which are palindromes using the above recurrence relation. Do this again for each increasing sub-string length, until the sub-string length is equal the original string length.

### Implementation

```C++
#include <iostream>
#include <string>
#include <vector>

void print_string(std::string str) {
  for (auto &k : str)
    std::cout << k;
  std::cout << std::endl;
}

int main() {
  std::string str = "abnabauyyuabap";
  int str_size = str.size();

  std::vector<std::vector<bool>> is_palin;
  for (int i = 0; i < str_size; i++)
    is_palin.emplace_back(str_size, false);

  for (int i = 0; i < str_size; i++) {
    is_palin[i][i] = true;
    std::cout << str[i] << std::endl;
  }

  for (int i = 0; i < str_size - 1; i++) {
    if (str[i] == str[i + 1]) {
      is_palin[i][i + 1] = true;
      print_string(str.substr(i, 2));
    }
  }

  for (int pal_size = 3; pal_size < str_size; pal_size++) {
    for (int i = 0, j = i + pal_size - 1; j < str_size; i++, j++) {
      if (str[i] == str[j] && is_palin[i + 1][j - 1]) {
        is_palin[i][j] = true;
        print_string(str.substr(i, pal_size));
      }
    }
  }

  return 0;
}
```

# References

- <https://leetcode.com/problems/palindromic-substrings/solutions/953080/palindromic-substrings/>
