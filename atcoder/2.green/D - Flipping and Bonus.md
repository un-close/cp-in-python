## Summary:
to maximize the score by performing flipping of coins and respective bonus for certain streak of numbers

# INTUITION:
- have a 2-D dp table with row indicating the index and the col indicating the counter.
- `dp[i][j]` signifies the largest score possible with `ith` index and `jth` streak
- `dp[i][0]` should be the largest score possible from the last row

# IMPLEMENTATION:
```python
def solve():  
    n, m = map(int, inp().split())  
    money = list(map(int, inp().split()))  
    streak = {}  
    for _ in range(m):  
        counter, key = map(int, inp().split())  
        streak[counter] = key  
    dp = [[0] * (n + 1) for _ in range(n + 1)]  
    for i in range(1, n + 1):  
        for j in range(1, i + 1):  
            dp[i][j] = max(dp[i][j], dp[i - 1][j - 1] + money[i - 1] + streak.get(j, 0))  
        dp[i][0] = max(dp[i - 1])  
    print(max(dp[-1]))
```