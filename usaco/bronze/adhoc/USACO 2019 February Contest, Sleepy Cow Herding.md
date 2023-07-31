## Summary:
find the minimum and maximum steps required to make the cows consecutive.

# OBSERVATIONS:
- the minimum steps value is at most 2. This is not the case only when the numbers given are already consecutive or one of the gap with the cows is 1
- the maximum steps is equal the largest gap btw either endpoint standing cow and the mid cow. [[Sleepy Cow Herding (USACO Bronze 2019 February) - Problems and Contests - USACO Forum](https://forum.usaco.guide/t/sleepy-cow-herding-usaco-bronze-2019-february/4120/2)]

# IMPLEMENTATION:
```py
import sys  
  
  
def file(name):  
    # Function to read from input file and write to output file  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    # Function that implements the main logic of the program  
    inp, out = sys.stdin.readline, sys.stdout.write  
    a, b, c = sorted(map(int, input().split()))  
    first_half, second_half = b - a - 1, c - b - 1  
    min_steps = min(2, max(first_half, second_half))  
    if first_half == 1 or second_half == 1:  
        min_steps = 1  
    max_steps = max(first_half, second_half)  
    out(f'{min_steps}\n{max_steps}\n')  
  
  
if __name__ == "__main__":  
    file('herding')  
    main()
```