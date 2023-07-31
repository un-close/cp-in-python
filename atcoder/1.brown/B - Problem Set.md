# Link:
[B - Problem Set (atcoder.jp)](https://atcoder.jp/contests/code-festival-2017-qualb/tasks/code_festival_2017_qualb_b)

# IMPLEMENTATION:
```python
def solve():
    n = int(inp())
    pool = list(map(int, inp().split()))
    m = int(inp())
    required = list(map(int, inp().split()))
    freq = defaultdict(int)
    freq_re = defaultdict(int)
    for i in pool:
        freq[i] += 1
    for i in required:
        freq_re[i] += 1
    for key, val in freq_re.items():
        if freq.get(key, -1) == -1 or freq[key] < val:
            print('NO')
            return
    print('YES')
```