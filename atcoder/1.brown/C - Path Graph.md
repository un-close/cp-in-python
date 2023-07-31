## Summary:
- Check whether the given graph is a path graph or not
- [C - Path Graph? (atcoder.jp)](https://atcoder.jp/contests/abc287/tasks/abc287_c)

# INTUITION:
- a path graph have n-1 edges, at-most 2 out-degree, all are connected
- check the connections using DSU

# IMPLEMENTATION:
```python
def solve():

    n, m = map(int, inp().split())

    connections = [list(map(int, inp().split())) for _ in range(m)]

    graph = [[] for _ in range(n)]

    for u, v in connections:

        u, v = u - 1, v - 1

        graph[u].append(v), graph[v].append(u)

    if m != n - 1 or any(len(a) > 2 for a in graph):

        print('No')

        return

    connected = DSU(n)

    for u, v in connections:

        connected.union(u-1, v-1)

    heads = defaultdict(int)

    for i in range(n):

        parent = connected.find(i)

        heads[parent] += 1

    if any(no == n for no in heads.values()):

        print('Yes')

    else:

        print('No')
```