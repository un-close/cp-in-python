# LINK:
- [B - DNA Sequence (atcoder.jp)](https://atcoder.jp/contests/arc104/tasks/arc104_b)

# IMPLEMENTATION:
```python
def solve():  
    size, s = inp().split()  
    n, count = int(size), 0  
    for i in range(n):  
        c1 = c2 = 0  
        for j in range(i, n):  
            if s[j] == 'A':  
                c1 += 1  
            elif s[j] == 'T':  
                c1 -= 1  
            elif s[j] == 'C':  
                c2 += 1  
            else:  
                c2 -= 1  
            if not c1 and not c2:  
                count += 1  
    out(f'{count}\n'), flush()
```