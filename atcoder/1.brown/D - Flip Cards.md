# LINK:
- [D - Flip Cards (atcoder.jp)](https://atcoder.jp/contests/abc291/tasks/abc291_d)

# CODE:
```python
import sys
from itertools import accumulate, product
MOD = 998244353
inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush
n = int(inp())
cards, dp = [list(map(int, inp().split())) for _ in range(n)], [[0, 0] for _ in range(n)]
dp[0] = [1, 1]
for i in range(1, n):
    for flips, prev in product(range(2), range(2)):
        if cards[i][flips] != cards[i - 1][prev]:
            dp[i][flips] += dp[i - 1][prev]
    dp[i][0] %= MOD
    dp[i][1] %= MOD
out(f'{(dp[-1][0] + dp[-1][1]) % MOD}\n'), flush()

```