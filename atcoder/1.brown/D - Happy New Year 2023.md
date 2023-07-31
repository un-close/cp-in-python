## Summary
find 2 prime number p & q, such that the given number N can be represented as 
$N$ = $p^2$ * $q$.

# INTUITION:
- N = $p * p * q$. So the min(p, q) is less than $\sqrt[3]{N}$.
- so just search in this range from 2 to $\sqrt[3]{N}$.

# IMPLEMENTATION:
```python
def solve():

    for _ in range(int(inp())):

        n = int(inp())

        end = pow(n, 1/3)

        for i in range(2, int(end) + 1):

            if n % i == 0:

                if (n//i) % i == 0:

                    p, q = i, n // (i ** 2)

                else:

                    p, q = int(sqrt(n//i)), i

                print(f'{p} {q}')

                break
```
