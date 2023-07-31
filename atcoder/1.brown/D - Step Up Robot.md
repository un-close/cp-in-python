## Summary:
[[D - Step Up Robot (atcoder.jp)](https://atcoder.jp/contests/abc289/tasks/abc289_d)]

# INTUITION:
- Dijkstra's algorithm

# IMPLEMENTATION:
```python
def solve():    

    n = int(inp())

    increments = list(map(int, inp().split()))

    m = int(inp())

    pits = set(map(int, inp().split()))

    x = int(inp())

    heap, visited = [0], set()

    while heap:

        current = -heappop(heap)

        if current == x:

            print('Yes')

            return 0

        for i in increments:

            if 0 <= i + current <= x and i + current not in pits:

                pits.add(i + current)

                heappush(heap, -(i + current))

    print('No')
```