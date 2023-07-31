## Summary:
- find the maximum and minimum no of strawberries found in a piece after the whole cake of dimension w * h is divided by *A* lines parallel to y and *B* lines parallel to x.

# INTUITION:
- Assign an id for each strawberry by finding the nearest x from set of 'A' and nearest y from set of 'B'.
- This can be done using binary search
- Now from the dictionary, we can find the no of strawberries associated with each id

# IMPLEMENTATION:
```python
def solve():

    w, h = map(int, inp().split())

    n = int(inp())

    P, Q = list(), list()

    for _ in range(n):

        i, j = map(int, inp().split())

        P.append(i), Q.append(j)

    A = int(inp())

    a = list(map(int, inp().split()))

    B = int(inp())

    b = list(map(int, inp().split()))

    a.append(w+1), b.append(h+1)

    id = defaultdict(int)

    for p, q in zip(P, Q):

        x, y = bisect.bisect_left(a, p), bisect.bisect_left(b, q)

        id[(x, y)] += 1

    M, m = float('-inf'), float('inf')

    if len(id) < (A + 1) * (B + 1):

        m = 0

    for val in id.values():

        M, m = max(M, val), min(m, val)

    print(f'{m} {M}')
```