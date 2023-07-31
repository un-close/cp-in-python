## Summary:
Calculate the total amount of time slept between l and r for each query of form l, r.

# INTUITION:
- calculate the prefix sum to get the cumulative sleep 
- We can solve question if we define a function f(x) such that its the total amount of sleep till x. 
- The answer to the problem will now become f(r) - f(l)
- Inside the function, we can use binary search to find the part to be subtracted from prefix sum to get the total sleep

# IMPLEMENTATION:
```python
def solve():

    n = int(inp())

    A = list(map(int, inp().split()))

    A_grouped, pre_sum = [[A[i], A[i+1]] for i in range(1, n, 2)], [0] * (n // 2 + 1)

    for i in range(len(pre_sum)):

        pre_sum[i] = pre_sum[i-1] + A_grouped[i-1][-1] - A_grouped[i-1][0]

    def binary_search(x):

        left, right = 0, len(A_grouped)

        while left < right:

            mid = (left + right)//2

            if A_grouped[mid][0] < x:

                left = mid + 1

            else:

                right = mid

        return left

  

    def slept_till(x):

        i = binary_search(x)

        total_sleep = pre_sum[i]

        if i > 0:

            if A_grouped[i-1][-1] > x:

                total_sleep -= A_grouped[i-1][-1] - x

        return total_sleep

  

    q = int(inp())

    for _ in range(q):

        l, r = map(int, inp().split())

        print(slept_till(r) - slept_till(l))
```

# FASTER :
```python
def solve():

    n = int(inp())

    A = list(map(int, inp().split()))

    A_grouped, A_search, pre_sum =[[0, 0] for _ in range(n // 2)], [0] * (n // 2), [0] * (n // 2 + 1)

    for i in range(1, n, 2):

        A_search[i//2] = A[i]

        A_grouped[i//2] = [A[i], A[i+1]]

        pre_sum[i//2 + 1] = pre_sum[i//2] + A[i+1] - A[i]

    def slept_till(x):

        i = bisect.bisect_left(A_search, x)

        total_sleep = pre_sum[i]

        if i > 0 and A_grouped[i-1][-1] > x:

            total_sleep -= A_grouped[i-1][-1] - x

        return total_sleep

  

    q = int(inp())

    ans = [0] * q

    for i in range(q):

        l, r = map(int, inp().split())

        ans[i] = slept_till(r) - slept_till(l)

    print('\n'.join(map(str, ans)))
```