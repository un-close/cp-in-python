## Summary:
Given a list, u can negate a number and it's adjacent number. Find the maximum sum possible after performing this operation any no of times

## Initial thoughts:
- [-] the current operation at some `ith` index will also affect the result at `i+1th` index too
- [-] Should we try all the possibility of the operation 
- [-] As the constraints are $10^5$ , can dp make it a $n^{2}$ or better solution?
- [-] if the elements inside the window are +ve numbers, we don't want to negate them
- [-] if one or both elements inside the window are -ve numbers, we *want* to use the operation such that it's over-all difference to the sum is positive
- [-] So will an *greedy approach* work in this case?

# OBSERVATIONS:
- here, we can immigrate all the negative signs to one side and positive to other side
- if the no of negative is even, the max sum is the abs sum of all the element
- else, give the negative number to the smallest no possible to maximize the sum

# IMPLEMENTATION:
```python
def solve():
    n = int(inp())
    nums = list(map(int, inp().split()))
    count = sum(i < 0 for i in nums)
    abs_nums = list(abs(i) for i in nums)
    if count & 1:
        print(sum(abs_nums) - 2 * min(abs_nums))
    else:
        print(sum(abs_nums))
```
