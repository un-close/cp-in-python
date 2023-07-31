## Summary:
You are given a positive integer N.  
Find the number of quadruples of positive integers (A,B,C,D) such that AB+CD=N.

# EDITORIAL:
link - [[Editorial - AtCoder Beginner Contest 292](https://atcoder.jp/contests/abc292/editorial/5914)]

# IMPLEMENTATION:
```python
n = int(inp())  
ans = 0  
for i in range(1, n):  
    X, Y = i, n - i  
    x = y = 0  
    for j in range(1, int(math.sqrt(X)) + 1):  
        if X % j == 0:  
            x += 2 if X != j * j else 1  
    for j in range(1, int(math.sqrt(Y)) + 1):  
        if Y % j == 0:  
            y += 2 if Y != j * j else 1  
    ans += x * y  
out(f'{ans}\n')
```

# IMPLEMENTATION 2:
```python
n = int(input())
ans =0
X =[0] *(n+1)
for a in range(1,int(n**0.5)+1):
    for b in range(a,n):
        if a*b>n:
            break
        if a==b:
            X[a*b]+=1
        else:
            X[a*b] +=2
for i in range(1,n):
    ans+=X[i]*X[n-i]
print(ans)
```