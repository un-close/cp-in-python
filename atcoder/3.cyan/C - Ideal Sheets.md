## Summary:
Given sheet A and B consisting of blacks and transparent blocks, determine whether there exist an arrangement of A & B such that it represents another sheet X by using all the black blocks.
- [C - Ideal Sheet (atcoder.jp)](https://atcoder.jp/contests/abc307/tasks/abc307_c)

# INTUITION:
- find the sub-square which contains all the blacks of the sheets, normalize the co-ordinates
- now slides this sub-squares of A and B over each other and check whether an arrangement is possible

# IMPLEMENTATION:
```python
def solve():

    def normalize(Z):

        x_min, y_min = min(i for i, _ in Z), min(j for _, j in Z)

        return set((i - x_min, j - y_min) for i, j in Z)

    def blacks(mat):

        Z  = set()

        for i, j in product(range(len(mat)), range(len(mat[0]))):

            if mat[i][j] == '#':

                Z.add((i, j))

        return Z

    ha, wa = map(int, inp().split())

    A = list(list(inp().strip()) for _ in range(ha))

    hb, wb = map(int, inp().split())

    B = list(list(inp().strip()) for _ in range(hb))

    hx, wx = map(int, inp().split())

    X = list(list(inp().strip()) for _ in range(hx))

  

    A_blacks, B_blacks, X_blacks = normalize(blacks(A)), normalize(blacks(B)), normalize(blacks(X))

  

    for dx, dy in product(range(-hx, hx), range(-wx, wx)):

        if normalize(A_blacks | {(x + dx, y + dy) for x, y in B_blacks})  == X_blacks:

            print('Yes')

            return

  

    print('No')
```