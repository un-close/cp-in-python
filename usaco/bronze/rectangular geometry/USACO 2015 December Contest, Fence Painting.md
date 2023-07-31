## Summary:
find the total area covered 

# OBSERVATION:
- individual area covered minus their intersection

# IMPLEMENTATION:
```python
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    a, b = map(int, inp().split())  
    c, d = map(int, inp().split())  
    intersect = max(min(b, d) - max(a, c), 0)  
    paint = b - a + d - c - intersect  
    out(f'{paint}\n')  
    flush()  
  
  
if __name__ == "__main__":  
    file('paint')  
    main()
```