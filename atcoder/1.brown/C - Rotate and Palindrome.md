## Summary:
- Find the min amount of cost required to make the given string a palindrome
- [C - Rotate and Palindrome (atcoder.jp)](https://atcoder.jp/contests/abc286/tasks/abc286_c)
# INTUITION:
- Try all the possible combinations

# IMPLEMENTATION:
```python
def solve():

    n, a, b = int_inp()

    s = inp().strip()

    cost = inf

    for i in range(n):

        temp_cost = a * i

        for j in range(n//2):

            l, r = (i + j) % n, (i + n - 1 - j) % n

            if s[l] != s[r]:

                temp_cost += b

        cost = min(cost, temp_cost)

    print(cost)
```