# Link:
[C - Colorful Leaderboard (atcoder.jp)](https://atcoder.jp/contests/abc064/tasks/abc064_c)

```python
def solve():
    n = int(inp())
    nums = list(map(int, inp().split()))
    freq = defaultdict(int)
    any_number = 0
    for i in nums:
        if i < 3200:
            key = i // 400
            freq[key] += 1
        else:
            any_number += 1
    min_no = max(len(freq), 1)
    max_no = len(freq) + any_number
    print(min_no, max_no, sep=' ', flush=True)

```