## Summary:
classical stairs problem with some steps as traps

# INTUITION:
dp.

# IMPLEMENTATION:
```python
def solve():  
    n, m = map(int, inp().split())  
    broken, mod = set(), 10**9 + 7  
    for _ in range(m):  
        broken.add(int(inp()))  
    cnt = [0] * (n + 1)  
    cnt[0] = 1  
    if 1 not in broken:  
        cnt[1] = 1  
    for i in range(2, n + 1):  
        if i not in broken:  
            cnt[i] = (cnt[i - 1] + cnt[i - 2]) % mod  
    print(cnt[-1])
```