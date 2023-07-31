## Summary:
Find the kth marked element in a circular list in which an step size of D is used to mark the next and a step size of 1 if the given element is already marked.

# INTUITION:
- let the `gcd` of N, *size of the list* and D, *step size* be **g**.
- Then we can represent $N = a*g$ and $D = b * g$
- According to the problem, the marking happens as follows
	- `0, D, 2D, 3D .. nD` where n is less than a.
	- for n = a(*or the $a+1th$ square to be marked*), we have `aD % N = a*b*g % N = N % N = 0` which is already marked, so we move on to the next square, i.e. 1
	- so next series is `1, 1 + D, 1 + 2D, ... 1 + nD` and so on.
- So the `ith` marked square is `(i-1)D % N` for `i` less than a.
- for `i` in between a and 2a, we have the marked square as `1 + (i-1)D % N`.
- for `i` in between 2a and 3a, we have the marked square as `2 + (i-1)D % N`.
- One may wonder how it's guaranteed that `0, D % N, 2D % N, ..` won't have any duplicates. Pls refer to the [proof](https://atcoder.jp/contests/abc290/editorial/5812)
- so for general `k`, the index of the marked square is `(k-1)/a + (k-1)D % N`.

# IMPLEMENTATION:
```python
def solve():

    t = int(inp())

    for _ in range(t):

        n, d, k = map(int, inp().split())

        a = n // gcd(n, d)

        first_term = (k-1)// a

        second_term = (k-1)*d % n

        print(first_term + second_term)
```