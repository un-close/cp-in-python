
# LINK:
[D - M<=ab (atcoder.jp)](https://atcoder.jp/contests/abc296/tasks/abc296_d)

# IMPLEMENTATION:
```python
def solve1(n, m):  
    if m > n * n:  
        return -1  
    if 1 <= m <= n or (m % 2 == 0 and m // 2 <= n) or m == n * n:  
        return m  
    a, b, high = 1, n, int(sqrt(m) + 1)  
    ans = high * high  
    for a in range(ceil(m/n), high + 1):  
        b = (m + a - 1) // a  
        if b <= n:  
            ans = min(ans, a * b)  
        if b < high or b < a:  
            break    
    return ans
```
