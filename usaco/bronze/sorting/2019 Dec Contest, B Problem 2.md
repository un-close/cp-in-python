## Summary:
find the  smallest window size k for which no two substring of k is same.  

# OBSERVATIONS:
- the length of the given string is $10^2$, so 0($n^4$) or better is expected
- brute force, set the the window size to length of given string as it can also be the ans and reduce it till we can't form a group of unique sub-strings
- can use Rabin Karp rolling hash with sliding window for checking and binary search on the answer to get a time complexity of 0(n * log(n)) 

```py
# USACO Bronze 2019 December - Where Am I?  
# 0(n*log(n)) solution :binary search on answer + rabin karp ( it's based on probability)  
import sys  
  
sys.stdin = open("whereami.in", "r")  
sys.stdout = open("whereami.out", "w")  
  
inp = sys.stdin.readline  
out = sys.stdout.write  
n = int(inp())  
s = inp()  
  
  
def sliding_window(k):  # 0(n) rabin karp with sliding window  
    p = 31  # prime number  
    m = 10 ** 9 + 9  # modulo  
    h = 0  # hash value of current substring  
    pow_p = 1  # p^k modulo m  
    for i in range(k):  
        h = (h * p + ord(s[i])) % m  
        pow_p = (pow_p * p) % m  
    substrings = {h}  
    for i in range(1, len(s) - k + 1):  
        # Compute the hash value of the next substring  
        h = (h * p - ord(s[i - 1]) * pow_p + ord(s[i + k - 1])) % m  
        if h in substrings:  
            return False  # Duplicate substring found  
        substrings.add(h)  
    return True  
  
  
left, right = 0, len(s) - 1  
while left < right:  # binary search on the ans log(n) * n  
    mid = (left + right) // 2  
    if sliding_window(mid):  
        right = mid  
    else:  
        left = mid + 1  
out(left)
```

