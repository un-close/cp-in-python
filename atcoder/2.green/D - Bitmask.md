## Summary:
Given a string consisting of 0, 1, '?' and a number n, find the largest number less than or equal to n that can be created by the choosing '?' to be either 0 or 1.

# INTUITION:
- replace the '?' with 0 to get the lowest possible value and try to add '1' from left to right 

# IMPLEMENTATION:
```python
def solve():  
    s, n = inp().strip(), int(inp().strip())  
    high, low = s.replace('?', '1'), s.replace('?', '0')  
    if int(high, 2) <= n:  
        print(int(high, 2))  
        return  
    if int(low, 2) > n:  
        print(-1)  
        return  
    no = int(low, 2)  
    for i in range(len(s)):  
        shift = len(s) - i - 1  
        if s[i] == '?' and (no | (1 << shift)) <= n:  
            no |= (1 << shift)  
    print(no)
```