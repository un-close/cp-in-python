# Link:
[E - Kth Takoyaki Set (atcoder.jp)](https://atcoder.jp/contests/abc297/tasks/abc297_e)

# IMPLEMENTATION:
```python
def solve():  
    n, k = map(int, inp().split())  
    nums = list(map(int, inp().split()))  
    org_nums = nums.copy()  
    heapify(nums)  
    seen = set()  
    while nums:  
        number = heappop(nums)  
        if number in seen:  
            continue
        seen.add(number)  
        k -= 1  
        if k == 0:  
            print(number)  
            break  
        for i in org_nums:  
            heappush(nums, i + number)
```