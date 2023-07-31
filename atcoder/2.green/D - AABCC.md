## Summary:
Given a upper limit, find the no of numbers that can be formed using $a^2 * b * c^2$ ,where a, b, c are prime numbers and are in ascending order in terms of their value.

## LINK:
[Editorial - ユニークビジョンプログラミングコンテスト2023 春 (AtCoder Beginner Contest 300)](https://atcoder.jp/contests/abc300/editorial/6288)

# INTUITION:
- the upper limit is at-most $10^{12}$. So the largest possible c is $10^{12} / (4 * 3)$, which is around 288675. Using prime number theorem, we can find the no of primes less than a given number 'n' by using the formula $n / ln(n)$. So the total no of primes possible is around 25k.
- Using Sieve of Eratosthenes, we can generate the prime numbers.
- Then we can go through all the possibility of a, b, c.

# IMPLEMENTATION:
```python
def solve():  
    n = int(inp())  
    length = int(sqrt(n)) + 1  
    primes, total_primes = [True] * length, list()  
    primes[0] = primes[1] = False  
    for i in range(2, length):  
        if primes[i]:  
            total_primes.append(i)  
            for j in range(i * i, length, i):  
                primes[j] = False  
    ans, length = 0, len(total_primes)  
    for i in range(length):  
        a = total_primes[i]  
        if a ** 5 > n:  
            break        
        for j in range(i + 1, length):  
            b = total_primes[j]  
            c = n // (a ** 2 * b)  
            if b > c:  
                break            
            for k in range(j + 1, length):  
                c = total_primes[k]  
                if (a ** 2 * b * c ** 2) > n:  
                    break                
                ans += 1  
    print(ans, flush=True)
```