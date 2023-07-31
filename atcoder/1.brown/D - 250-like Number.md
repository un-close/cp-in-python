## Summary:
find the total numbers less than given no 'n' such that it can be represented as $p*q^3$ where p, q are prime numbers and p < q.

# INTUITION:
- the maximum value that q can take is around $8*10^5$. So using `The Sieve of Eratosthenes`, find the primes up-to this.
- Now iterate through all the possible value of p with q being the maximum possible number for the current value of p. It can be seen that that all the value of prime between p and q also be a valid answer

# IMPLEMENTATION:
```python
def solve():  
    n = int(inp())  
    l, primes = 800000, list()  
    is_prime = [True] * l  
    for i in range(2, l):  
        if is_prime[i]:  
            primes.append(i)  
            for j in range(i * i, l, i):  
                is_prime[j] = False  
    q, res = len(primes) - 1, 0  
    for p in range(len(primes)):  
        while q >= 0 and primes[p] * primes[q] ** 3 > n:  
            q -= 1  
        if p >= q:  
            break        
        res += q - p  
    print(res)
```