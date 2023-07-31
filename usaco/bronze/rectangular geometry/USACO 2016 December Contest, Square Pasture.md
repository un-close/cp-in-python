## Summary:
Calculate the smallest square that encloses the same area as the two rectangular field.

# OBSERVATION:
the max length or breadth of the combined rectangular field will form the side of the required square

# IMPLEMENTATION:
```python
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
class Rectangle:  
    def __init__(self):  
        self.bx, self.by, self.tx, self.ty = map(int, inp().split())  
  
    @staticmethod  
    def square(rect1, rect2):  
        bottom = (min(rect1.bx, rect2.bx), min(rect1.by, rect2.by))  
        top = (max(rect1.tx, rect2.tx), max(rect1.ty, rect2.ty))  
        height, width = top[0] - bottom[0], top[-1] - bottom[-1]  
        return height, width  
  
  
def main():  
    rect1, rect2 = Rectangle(), Rectangle()  
    height, width = Rectangle.square(rect1, rect2)  
    side = max(height, width)  
    out(f'{side * side}\n')  
    flush()  
  
  
if __name__ == "__main__":  
    file('square')  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    main()
```