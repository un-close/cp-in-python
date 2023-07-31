## Summary:
Given two list, find the maximum value that can be picked from each such that their difference is less than a given no 'D'.

# INTUITION:
- The expected time complexity is $n*logn$. So binary search / sorting is used
- for a given element `x` in a list, the valid pair for this element should be inside the range (x + d, x - d).
- So we can search for this valid range in the other list and update the value for the maximum value seen.
- The search can be done through binary search in which we find the element that is less than or equal to x + d.
- then for the selected element, we check whether the element is greater than x - d to ensure that the selected element resides in the desired range.

# IMPLEMENTATION:
```python
def solve():

    n, m, d = map(int, inp().split())

    A, B = sorted(map(int, inp().split())), list(map(int, inp().split()))

    ans = -1

    for b in B:

        if ( i := bisect_right(A, b + d) - 1) > -1 and A[i] >= b - d:

            ans = max(ans, A[i] + b)

    print(ans)
```


