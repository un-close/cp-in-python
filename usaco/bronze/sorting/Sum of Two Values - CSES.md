You are given an array of n integers, and your task is to find two values (at distinct positions) whose sum is x.  
  
**Input**  
  
The first input line has two integers n and x: the array size and the target sum.  
  
The second line has n integers a1, a2, a3,...: the array values.

**Output**  
  
Print two integers: the positions of the values. If there are several solutions, you may print any of them. If there are no solutions, print `IMPOSSIBLE`.

# INTUITION:
- one sol is inserting num into the dictionary and checking if target - current number exist in the dict but the constant time is high even the C++ solution was giving TLE
- the other way to do this is by sorting the numbers with their previous indexes attached to them and doing a two pointer approach in which if the current sum is less than the target, we increase the left pointer and vice-versa.

# IMPLEMENTATION:
```py
import sys  
  
inp = sys.stdin.readline  
out = sys.stdout.write  
  
n, x = map(int, inp().split())  
array = (map(int, inp().split()))  
left, right = 0, n-1  
nums = [(num, i+1) for i, num in enumerate(array)]  
nums.sort()  
while left < right:  
    lr_sum = nums[left][0] + nums[right][0]  
    if lr_sum == x:  
        out(f'{nums[left][1]} {nums[right][1]}\n')  
        break  
    elif lr_sum > x:  
        right -= 1  
    else:  
        left += 1  
else:  
    print('IMPOSSIBLE')
```


