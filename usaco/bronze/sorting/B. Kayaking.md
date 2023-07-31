## Summary:
"There are 2n people and n-1 boats of capacity 2, as well as 2 boats of capacity 1. Each person has an associated weight, and the instability of a boat is calculated by the absolute difference between the weights of the people in the boat. The instability of a boat with capacity 1 is 0. The question asks to find the minimum total instability possible for the given weights of the people."

Examples:
`input`:
2
1 2 3 4
`output`:
1
Examples:
`input`:
4
1 3 4 6 3 4 100 200
`output`:
5

# OBSERVATION:
- If we group all the people into 'n' groups, we can reduce the instability caused by one group by assigning them to single capability boat since there instability is zero
- constrains of the question are n = 100ish 
- lets say we have numbers a, b, c, d in increasing order, then the min instability of the 2 boat is max(b-a, d-c) as other combination will worsen the instability.
- As the constrains are on the lower side, we could brute force/try all the possible 

# IMPLEMENTATION:
```py
n = int(input())
weights = [int(x) for x in input().split()]
weights.sort()
n *= 2
min_stability = float('inf')
for i in range(n):
    for j in range(i, n):
        include = list()
        for k in range(n):
            if k not in (i, j):
                include.append(weights[k])
        total = 0
        for k in range(0, n - 2, 2):
            total += include[k+1] - include[k]
        min_stability = min(min_stability, total)
print(min_stability)

```