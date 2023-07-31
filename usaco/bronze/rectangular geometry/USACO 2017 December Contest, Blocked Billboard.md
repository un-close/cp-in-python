## Summary:
find the total area minus the intersection with the truck

# OBSERVATION:
the intersection area can be found out by
`width = max(0, min(rect1.tx, rect2.tx) - max(rect1.bx, rect2.bx)) height = max(0, min(rect1.ty, rect2.ty) - max(rect1.by, rect2.by))` 
`intersection area = width * height`

# IMPLEMENTATION:

```python
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
class Rectangle:  
    def __init__(self):  
        self.bx, self.by, self.tx, self.ty = map(int, inp().split())  
  
    def area(self):  
        return (self.tx - self.bx) * (self.ty - self.by)  
  
    @staticmethod  
    def intersection(rect1, rect2):  
        width = max(0, min(rect1.tx, rect2.tx) - max(rect1.bx, rect2.bx))  
        height = max(0, min(rect1.ty, rect2.ty) - max(rect1.by, rect2.by))  
        return width * height  
  
  
def main():  
  
    rectangle1, rectangle2, truck = Rectangle(), Rectangle(), Rectangle()  
    Area1 = rectangle1.area() - Rectangle.intersection(rectangle1, truck)  
    Area2 = rectangle2.area() - Rectangle.intersection(rectangle2, truck)  
    out(f'{Area1 + Area2}\n')  
  
  
if __name__ == "__main__":  
    file('billboard')  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    main()
```

