## Summary:
- To find the total no of ways to get the end result as true.

## LINK:
[D - Logical Expression (atcoder.jp)](https://atcoder.jp/contests/abc189/tasks/abc189_d)

# INTUITION:
- dp

# IMPLEMENTATION:
```python
def solve():  
    n = int(inp())  
    operator = [inp().strip() for _ in range(n)]  
    dp = [[1, 1]] + [[0, 0] for _ in range(n)]  
    for i in range(1, n + 1):  
        for j in range(2):  
            if operator[i - 1] == 'AND':  
                if j == 0:  # no of false  
                    x_true, x_false = dp[i - 1][0], dp[i - 1][0] + dp[i - 1][1]  
                else:  # no of true  
                    x_true, x_false = dp[i - 1][1], 0  
            else:  
                if j == 0:  
                    x_true, x_false = 0, dp[i - 1][0]  
                else:  
                    x_true, x_false = dp[i - 1][0] + dp[i - 1][1], dp[i - 1][1]  
            dp[i][j] = x_true + x_false  
    print(dp[-1][1])
```