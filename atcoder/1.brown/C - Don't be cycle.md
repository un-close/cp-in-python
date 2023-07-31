## Summary:
find the minimum no of edges to remove to make the graph acyclic

# INTUITION:
- To make a graph acyclic means to make the graph into a tree.
- A tree with n nodes have at-most n-1 edges
- So let there be k connected components in the graph with `g1, g2,... gk` representing the no of vertex in each of them.
- The maximum no of edges possible for the graph is `g1-1 + g2-1 +.... gk-1.
- which is equal to `n(total no of vertex) - k`.
- so the minimum no of edges to remove to make the graph acyclic is equal to the total no of edges - maximum no of edges possible
- `ans = m - n + k`

# IMPLEMENTATION:
```python
def solve():

    n, m = map(int, inp().split())

    components = DSU(n)

    for _ in range(m):

        u, v = map(int, inp().split())

        u, v = u - 1, v - 1

        components.union(u, v)

    no_of_components = {components.find(i) for i in range(n)}

    ans = m - n + len(no_of_components)

    print(ans)
```