# LINK:
[C - Find it! (atcoder.jp)](https://atcoder.jp/contests/abc311/tasks/abc311_c)

# IMPLEMENTATION:
```python

def solve():
        n = int(inp())
        A = list(map(int, inp().split()))
        visited = set()
        ans = []
        node = 0
        while node not in visited:
              visited.add(node)
              node = A[node] - 1
        visited = set()
        while node not in visited:
              visited.add(node)
              ans.append(node+1)
              node = A[node] - 1
        print(len(ans))
        print(*ans)

```