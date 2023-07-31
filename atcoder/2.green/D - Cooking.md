# LINK:
[D - Cooking (atcoder.jp)](https://atcoder.jp/contests/abc204/tasks/abc204_d)

# INTUITION:
- subset sum

# DP IMPLEMENTATION:
```python
n = int(input())
times = list(map(int, input().split()))
total_time, min_time = sum(times), min(times)
poss_sum, ans = [False] * (total_time + 1), total_time
poss_sum[0] = True
for time in times:
    for sums in range(total_time, time - 1, -1):
        poss_sum[sums] |= poss_sum[sums - time]
for time in range(min_time, total_time // 2 + 1):
    if poss_sum[time] and poss_sum[total_time - time]:
        ans = min(ans, total_time - time)
print(ans, flush=True)
```

# BIT MANIPULATION IMPLEMENTATION:
```python
def solve():
    Set, sum, ans = 1, 0, -1
    n = int(inp())
    numbers = list(map(int, inp().split()))
    for i in numbers:
        Set |= (Set << i)
        sum += i
    ans = (sum + 1) // 2
    B = bin(Set)[2:]
    while B[ans] == '0':
        ans += 1
    out(f'{ans}\n')
```