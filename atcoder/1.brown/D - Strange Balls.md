# Link:
[D - Strange Balls (atcoder.jp)](https://atcoder.jp/contests/abc240/tasks/abc240_d)

# IMPLEMENTATION:
```python
def solve():
    n = int(inp())
    nums = list(map(int, inp().split()))
    stack = []
    decrease,ans = 0, list()
    for i, val in enumerate(nums):
        if not stack or val != stack[-1][0]:
            stack.append([val, 1])
        else:
            stack[-1][1] += 1
            while stack and stack[-1][0] == stack[-1][-1]:
                decrease += stack[-1][0]
                stack.pop()
        ans.append(str(i - decrease + 1))
    print('\n'.join(ans))
```