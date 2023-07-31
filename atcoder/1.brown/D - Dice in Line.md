# LINK:
[D - Dice in Line (atcoder.jp)](https://atcoder.jp/contests/abc154/tasks/abc154_d)

# IMPLEMENTATION:
```python
def solve1():  
    n, k = map(int, inp().split())  
    expected_value = list(map(int, inp().split()))  
    for i in range(len(expected_value)):  
        expected_value[i] = (expected_value[i] + 1) / 2  
    ans = window = sum(expected_value[:k])  
    for i in range(k, n):  
        window += expected_value[i] - expected_value[i - k]  
        ans = max(window, ans)  
    out(f'{ans}\n')
```