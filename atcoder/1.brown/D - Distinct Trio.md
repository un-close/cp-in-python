# LINK:
[Submission #40320655 - AtCoder Beginner Contest 252](https://atcoder.jp/contests/abc252/submissions/40320655)

# IMPLEMENTATION:
```python
import sys
from math import comb
from collections import Counter

def solve1():  
    n = int(inp())  
    nums = list(map(int, inp().split()))  
    distinct = Counter(nums)  # frequency of each digit  
    total_combinations = comb(n, 3)  
    two_duplicates, three_duplicates = list(), list()  
    for v in distinct.values():  
        if v >= 2:  
            two_duplicates.append(v)  
            if v > 2:  
                three_duplicates.append(v)  
    for x in two_duplicates:  
        total_combinations -= comb(n - x, 1) * comb(x, 2)  
    for x in three_duplicates:  
        total_combinations -= comb(x, 3)  
    out(f'{total_combinations}\n')

if __name__ == "__main__":
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush
    solve1()

```