# LINK:
- [Tasks - AtCoder Beginner Contest 185](https://atcoder.jp/contests/abc185/tasks)

# IMPLEMENTATION:
```python
def solve():  
    total, blues = map(int, inp().split())  
    if not blues or total == blues:  
        print(0 if blues == total else 1)  
        return  
    blue_blocks = sorted(map(int, inp().split()))  
    blue_blocks.insert(0, 0) if blue_blocks[0] > 1 else None  
    blue_blocks.append(total + 1) if blue_blocks[-1] < total else None  
    difference, min_diff = list(), total - blues  
    for blocks in range(len(blue_blocks) - 1):  
        ele = blue_blocks[blocks + 1] - blue_blocks[blocks] - 1  
        min_diff = min(ele if ele else float('inf'), min_diff)  
        difference.append(ele)  
    steps = 0  
    for diff in difference:  
        steps += math.ceil(diff / min_diff)  
    out(f'{steps}\n')
```