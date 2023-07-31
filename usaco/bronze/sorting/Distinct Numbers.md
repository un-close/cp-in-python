## Summary:
find the no of distinct numbers in the given list of numbers

# OBSERVATION:
- sorting and counting

# IMPLEMENTATION:
```python
n = int(input())
# create a sorted list of the numbers
numbers = sorted(map(int, input().split()))
ans = 1
for i in range(1, n):
	# if the current number is different from the previous
	# it is a distinct number so we add 1 to the answer
	if numbers[i] != numbers[i - 1]:
		ans += 1
print(ans)
```

# IMPLEMENTATION orginial:
```python
import sys  
  
inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
n = int(inp())  
nums = sorted(map(int, inp().split()))  
count, prev = 1, nums[0]  
for num in nums[1:]:  
    if prev != num:  
        count += 1  
        prev = num  
out(f'{count}\n')  
flush()
```