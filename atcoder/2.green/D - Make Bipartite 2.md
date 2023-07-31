# NOTES:
- [D - Make Bipartite 2 (atcoder.jp)](https://atcoder.jp/contests/abc282/tasks/abc282_d)

# IMPLEMENTATION:
```python

def solve():
    n, m = map(int, inp().split())
    graph = [[] for _ in range(n)]
    for _ in range(m):
        u, v = map(int, inp().split())
        graph[u-1].append(v-1), graph[v-1].append(u-1)
    white = black = 0
    color = [-1] * n

    def bfs(node, curr_color):
        nonlocal white, black
        q = [node]
        color[node] = curr_color
        black += 1
        while q:
            n = len(q)
            for i in range(n):
                node = q.pop()
                for nei in graph[node]:
                    if color[nei] == color[node]:
                        return False
                    elif color[nei] == -1:
                        color[nei] = 1 - color[node]
                        if color[nei] == 0:
                            black += 1
                        else:
                            white += 1
                        q.append(nei)
        return True
    total = n * (n - 1) // 2 - m
    for i in range(n):
        white = black = 0
        if color[i] == -1:
            if not bfs(i, 0):
                print(0)
                return
            else:
                total -= comb(white, 2) + comb(black, 2)
    print(total)
    

```