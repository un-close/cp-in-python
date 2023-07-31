## Summary:
Given a vertex and distance, mark all the vertex that can be reached.

# INTUITION:
- put all the vertex and distance, do something similar to Dijkstra's algorithms to select the most promising nodes to avoid unnecessary calculations

# IMPLEMENTATION:
```python
def solve():

    n, m, k = map(int, inp().split())

    graph = [[] for _ in range(n)]

    for _ in range(m):

        a, b = map(int, inp().split())

        a, b = a - 1, b - 1

        graph[a].append(b), graph[b].append(a)

    q, visited = list(), [-inf] * n

    for _ in range(k):

        guard, hp = map(int, inp().split())

        visited[guard-1] = hp

        heapq.heappush(q, [-hp, guard-1])

    while q:

        hp, source = heapq.heappop(q)

        hp = -hp

        if visited[source] > hp or hp - 1 < 0:

            continue

        new_hp = hp - 1

        for nei in graph[source]:

            if visited[nei] < new_hp:

                visited[nei] = new_hp

                heapq.heappush(q, [-new_hp, nei])

    l,ans = 0, str()

    for i in range(n):

        if visited[i] != -inf:

            l += 1

            ans += str(i+1) + ' '

    print(l)

    print(ans)
```