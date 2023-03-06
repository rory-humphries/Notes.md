---
title: Four Colouring of Planar Graphs with Max Degree 3
---

# Problem

This is a simplified case of the [Four Colour Theorem](Four_Colour_Theorem.md), which restricts the maximum [degree](Degree.md) of a [Planar Graph](planar_Graph.md) to 3. The goal is to associate one of four colours with each vertex of a planar graph, such that none of the neighbours of a vertex has the same colour as it.

With the restriction that the maximum degree is 3, given any vertex in a graph, we are guaranteed that there exists a colour which is not shared with its neighbours.

# Algorithm

- The algorithm is relatively straight-forward. We associate the four different colours with the integers `1`, `2`, `3`, and `4` respectively.
- Assuming our graph as `N` vertices, we initialise the array `colours` of type `int` and size `N` with `0`'s. Here `0` indicates that no colour has been chosen for a vertex yet.
- For each vertex `i` in the graph, set `colours[i]` to be an integer `1` through `4` such that it's not equal to the colours of any of its neighbours. This is guaranteed to exist. If more than one option is possible the choice of integer does not matter as long as it's between `1` and `4`. 

## Implementation

```cpp
vector<int> four_col_max_deg3(int n, vector<vector<int>>& edges) {
        vector<vector<int>> adj(n);
        for (auto &k: edges) {
            adj[k[0]-1].push_back(k[1]-1);  
            adj[k[1]-1].push_back(k[0]-1);  
        }
        vector<int> cols(n, 0);        
        array<bool, 4> arr = {false, false, false, false};
        
        for (int i = 0; i < n; i++) {
            arr = {false, false, false, false};
            for (auto &v: adj[i]) {
                if (cols[v] != 0) {
                    arr[cols[v]-1] = true;
                }
            }
            for (int j = 0; j < 4; j++) {
                if (arr[j] == false) {
                    cols[i] = j+1;
                    break;
                }
            }
        }     
    return cols;
    }
```
