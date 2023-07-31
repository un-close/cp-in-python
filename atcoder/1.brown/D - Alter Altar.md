# LINK:
- [D - Alter Altar (atcoder.jp)](https://atcoder.jp/contests/abc174/tasks/abc174_d)

# IMPLEMENTATION:

```python
def solve1(n, s):  
    red_count = s.count('R')  
    count = s.count('W', 0, red_count)  
    out(f'{count}\n'), flush()
```