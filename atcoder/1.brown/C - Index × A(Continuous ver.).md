# Link:
[C - Index × A(Continuous ver.) (atcoder.jp)](https://atcoder.jp/contests/abc267/tasks/abc267_c)

# INITIAL THOUGHTS:
- [X] sliding window with prefix sum 

# OBSERVATIONS:
- mathematical equation formation 

# IMPLEMENTATION:
```python
def window_sum(nums, k):  
    Sum = sum(nums[:k])  
    w_sum = [Sum]  
    for i in range(k, len(nums)):  
        Sum += nums[i] - nums[i - k]  
        w_sum.append(Sum)  
    return w_sum  
  
  
def solve():  
    n, m = map(int, inp().split())  
    nums = list(map(int, inp().split()))  
    if m == n:  
        print(sum((i + 1) * val for i, val in enumerate(nums)))  
        return  
    if m == 1:  
        print(max(nums))  
        return  
    w_sum, index = window_sum(nums, m), 0  
    Sum = [sum((i + 1) * val for i, val in enumerate(nums[:m]))]  
    for i in range(m, len(nums)):  
        new_entry = nums[i] * m + Sum[-1] - w_sum[index]  
        index += 1  
        Sum.append(new_entry)  
    print(max(Sum))
```