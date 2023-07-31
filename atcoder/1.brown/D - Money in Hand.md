## Summary:
- given n kind of coins with no of times they appear, determine whether a no 'x' can be formed using them

# INTUITION:
- define a `dp[i][j]` where it true if from `i` kind of coins, `j` can be formed.
- then the required answer becomes `dp[n][x]`.

# IMPLEMENTATION:
```python
def solve():

    n, x = map(int, inp().split())

    coins = list(list(map(int, inp().split())) for _ in range(n))

    dp = [[False] * (x+1) for _ in range(n+1)]

    dp[0][0] = True

    for i in range(1, n+1):

        value, times = coins[i-1]

        for j in range(x+1):

            dp[i][j] |= dp[i-1][j]

            for k in range(1, times+1):

                if j < k * value or dp[i][j]:

                    break

                dp[i][j] |= dp[i-1][j - k * value]

    print('Yes' if dp[-1][-1] else 'No')
```