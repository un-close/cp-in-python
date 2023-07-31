## Summary:
Given two string s and t, where |s| > |t|, find for each x from 0 to length of t that the string formed from first x character and last x character from s is equal to t. If any character is `?` , then it can be replaced by any other character.

# INTUITION:
- If u visualize what's happening, the prefix and suffix is varied for each x.
- So having a prefix and suffix array denoting till where both are same can be used to tackle the given problem
- For prefix, if any character from the left is not matching, then we know that the coming strings formed after that character is guaranteed for not forming a string equal to t. Similar logic can be applied to suffix.

# IMPLEMENTATION:
```python
def solve():  
    s, t = inp().strip(), inp().strip()  
    s_len, t_len = len(s), len(t)  
    prefix, suffix = [False] * (t_len + 1), [False] * (t_len + 1)  
    prefix[0] = suffix[0] = True  
    for i in range(t_len):  
        if s[i] == '?' or t[i] == '?' or s[i] == t[i]:  
            prefix[i + 1] = True  
        else:            
	        break    
    r_s, r_t = s[::-1], t[::-1]  
    for i in range(t_len):  
        if r_s[i] == '?' or r_t[i] == '?' or r_s[i] == r_t[i]:  
            suffix[i + 1] = True  
        else:            
	        break    
    for x in range(t_len+1):  
        if prefix[x] and suffix[t_len - x]:  
            print('Yes')  
        else:  
            print('No')
```