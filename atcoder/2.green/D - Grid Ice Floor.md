# Summary:
- [D - Grid Ice Floor (atcoder.jp)](https://atcoder.jp/contests/abc311/tasks/abc311_d)

# IMPLEMENTATION:
```python

def solve():
    n, m = map(int, inp().split())
    mat = [list(inp().strip()) for _ in range(n)]
    s_point, visited = {(1, 1)}, set()
    q = [(1, 1)]
    for x, y in q:
        for dx, dy in ((1, 0), (0, 1), (-1, 0), (0, -1)):
            n_x, n_y = x, y
            while mat[n_x][n_y] != '#':
                visited.add((n_x, n_y))
                n_x, n_y = n_x + dx, n_y + dy
            n_x, n_y = n_x - dx, n_y - dy
            if (n_x, n_y) not in s_point:
                s_point.add((n_x, n_y)), q.append((n_x, n_y))
    print(len(visited))

```