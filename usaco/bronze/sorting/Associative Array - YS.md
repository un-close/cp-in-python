## Summary:
given an infinite long array of initial value 0. Do the following queries
- `0 k v` :update array[k] = v
- `1 k`: print array[k]

# INTUITION:
Using a dictionary for storing the key-value pair , (k, v) and if the key is not present, default ans will be 0

# IMPLEMENTATION:
```py
import sys  
  
inp = sys.stdin.readline  
out = sys.stdout.write  
  
q = int(inp())  
look_up = {}  
for _ in range(q):  
    A = inp().split()  
    if A[0] == '0':  
        look_up[A[1]] = A[2]  
    else:  
        out(look_up.get(A[1], '0') + '\n')
```
