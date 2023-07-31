## Summary:
There is a circular barn with rooms located for the cows with seats. The question asks to find the entry point through which the total distance travelled by the cows to reach the designated seats are minimal

# OBSERVATION:
- simulate all the possibilities

# IMPLEMENTATION:
```py
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    n = int(inp())  
    cows = list()  
    for _ in range(n):  
        cows.append(int(inp()))  
    min_distance = float('inf')  
    for i in range(n):  
        distance = 0  
        for offset in range(n):  
            distance += offset * (cows[(i + offset) % n])  
        min_distance = min(min_distance, distance)  
    out(f'{min_distance}\n')  
  
  
if __name__ == "__main__":  
    file('cbarn')  
    main()
```