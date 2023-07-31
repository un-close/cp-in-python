## Summary:
-[D - Change Usernames (atcoder.jp)](https://atcoder.jp/contests/abc285/tasks/abc285_d)

# INTUITION:
- check cycle or not, use Kahn's algorithm

# IMPLEMENTATION:
```python
def solve():

    n = int(inp())

    graph = defaultdict(set)

    in_degree = defaultdict(int)

    nodes = set()

    for _ in range(n):

        s, t = inp().split()

        graph[s].add(t)

        in_degree[t] += 1

        nodes.add(s), nodes.add(t)

    q, index = list(), 0

    for node in nodes:

        if in_degree[node] == 0:

            q.append(node)

            index += 1

    while q:

        node = q.pop()

        for nei in graph[node]:

            in_degree[nei] -= 1

            if in_degree[nei] == 0:

                q.append(nei)

                index += 1

    print('Yes' if index == len(graph) else 'No')
```
