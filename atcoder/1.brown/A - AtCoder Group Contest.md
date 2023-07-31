# LINK:
- [A - AtCoder Group Contest](https://atcoder.jp/contests/agc012/tasks/agc012_a)

# IMPLEMENTATION:
```python
1.  def solve():
2.  n = int(inp())
3.  nums = sorted(map(int, inp().split()), reverse=True)
4.  total = sum(nums[1::2][:n]) # starts from 1 index, and select the second element, total n elements are selected
5.  out(f'{total}\n')
```