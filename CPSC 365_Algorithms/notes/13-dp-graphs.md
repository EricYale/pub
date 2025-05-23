# Dynamic Programming on Graphs

## DP on Directed Acyclic Graphs, allowing Negative Edge Weights
- We can use DP to get the distance to any node in a DAG, even if there are negative edge weights
- Basically do a table filling algorithm, starting from the source node, ending at the sink node
    - We can do this since there are no circular dependencies

If we know $dist(v_1), \dots, dist(v_i)$, we can compute $dist(v_{i_1})$
$$
dist(v_{i+1}) = \min_{u\in Pred(v_{i_1})}\left(dist(u) + w(u, v)\right)
$$

- Runtime: $O(n + m)$

## DP on Directed Cyclic Graphs, allowing Negative Edge Weights
- We can define an alternate distance function, `dist*(v, k)`, to find the shortest _walk_ `v` using `k` steps
    - We can do this with a "multi-layered graph" approach
    - Recurrence: `dist*(v, k) = min(dist*(u, k-1) + w(u, v))` for `u` is a predecessor of `v`
- Then, we can define our normal function $dist(v, k)$ to be the length of the shortest _walk_ to `v` using **at most** `k` steps
    - We can either choose not to use the `k`th step, in which case it's $dist(v, k-1)$
    - Or, we can use all steps, in which case it's $dist(u, k-1) + w(u, v)$ for some $u \in Pred(v)$

### Two Observations
1. If a graph has a _negative weight cycle_, there will be a pair of vertices $u$ and $v$ such that there is a _shorter walk_ from $u$ to $v$ than the _shortest path_ from $u$ to $v$.
2. If there are no negative weight cycles, the _shortest walk_ from $u$ to $v$ is the _shortest path_ from $u$ to $v$, for all $u$ and $v$.

### Determining if there is a Negative Weight Cycle
- Instead of stopping at walks of length $n-1$, we can stop at walks of length $n$
- This extra step in the table computation will tell us if there's a negative weight cycle, which you can tell by if the last entry in the table is the same as the penultimate entry!

### Bellman-Ford Algorithm
```
// Input: weighted graph G=(V,E) with vertices 1..n and source node s
Bellman-Ford(G, n, s):
    Precompute predecessor table Pred(v) for all vertices
    Initialize table D[1, ..., n]
    D[s] = 0; for all other v, D[v] = Infinity

    For k = 1 to n:
        For v = 1 to n:
            D[v] = min(D[v], min(D[u] + w(u))) for all predecessors u
    return D, or report that there was a reachable negative weight cycle
```
Runtime: $O(n \times m)$
