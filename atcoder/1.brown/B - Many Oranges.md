# LINK:
- [Submission #40291901 - Panasonic Programming Contest (AtCoder Beginner Contest 195)](https://atcoder.jp/contests/abc195/submissions/40291901)

# IMPLEMENTATION:
```python
def solve():
    a, b, w = map(int, inp().split())
    min_oranges, max_oranges = float('inf'), float('-inf')
    for i in range(1, 10 ** 6 + 1):
        if i * a <= w * 1000 <= i * b:
            min_oranges, max_oranges = min(min_oranges, i), max(max_oranges, i)
    if min_oranges == float('inf') or max_oranges == float('-inf'):
        print('UNSATISFIABLE')
    else:
        out(f'{min_oranges} {max_oranges}\n')
```