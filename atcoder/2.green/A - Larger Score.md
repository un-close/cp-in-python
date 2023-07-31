## Summary:
given an array with score as the sum of first k element, determine the minimum no of swaps needed to increase the score of array

# LINK:
[A - Larger Score (atcoder.jp)](https://atcoder.jp/contests/arc138/tasks/arc138_a)

# OBSERVATIONS:
- If the min of the first k element is greater than the max of the rest of the elements in the array, the increment in the score is not possible
- Else the answer always occur
- For the minimum swaps, we need to find 2 elements within k and outside k range such the element inside is lesser than that of outside and the difference between their indexes is minimum.
- We can achieve this by sorting the elements in the increasing order and breaking the tie by decreasing order of their indexes. We keep track of the largest index inside k and look for potential answers.

# IMPLEMENTATION:
```python
def solve():  
    n, k = map(int, inp().split())  
    nums = list(map(int, inp().split()))  
    b = [(nums, i) for i, nums in enumerate(nums)]  
    b.sort(key=lambda x: (x[0], -x[1]))  
    j, ans = -1, float('inf')  
    for _, i in b:  
        if i < k:  
            j = max(j, i)  
        elif j != -1:  
            ans = min(ans, i - j)  
    print(ans if ans != float('inf') else -1)
```