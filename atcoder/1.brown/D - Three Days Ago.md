### STATEMENT:
link - [[D - Three Days Ago (atcoder.jp)](https://atcoder.jp/contests/abc295/tasks/abc295_d)]

# IMPLEMENTATION:
```python
s = inp().strip()  
bit_set, count, state = [0] * (1 << 10), 0, 0  
bit_set[state] = 1  
for i in s:  
    bit = 1 << int(i)  
    state ^= bit  
    count += bit_set[state]  
    bit_set[state] += 1  
out(f'{count}\n')  
flush()
```