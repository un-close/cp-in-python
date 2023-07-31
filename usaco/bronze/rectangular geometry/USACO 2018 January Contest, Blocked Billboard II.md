## Summary:
to find the rectangular area to cover the remaining part of the lawnmower billboard

# OBSERVATION:
- the length/breadth of the intersection should be equal to that of the lawnmower's for the remaining area to be covered by an rectangular tarp.

# IMPLEMENTATION 1:

```python
# naive solution import sys  
  
  
def file(name):  
    # Redirect standard input and output to file for testing  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
class Rectangle:  
    def __init__(self, bx, by, tx, ty):  
        # Initialize instance variables  
        self.bx, self.by, self.tx, self.ty = bx, by, tx, ty  
        self.bottom, self.top = (bx, by), (tx, ty)  
        self.length, self.breadth = tx - bx, ty - by  
  
    def area(self):  
        # Calculate and return the area of the rectangle  
        height, width = self.tx - self.bx, self.ty - self.by  
        return height * width  
  
    def output(self):  
        # Print the coordinates of the bottom-left and top-right points of the rectangle  
        plane = ((self.bx, self.by), (self.tx, self.ty))  
        print(plane)  
  
    @staticmethod  
    def intersection(rect1, rect2):  
        # Calculate and return the area of intersection between two rectangles  
        width = max(0, min(rect1.tx, rect2.tx) - max(rect1.bx, rect2.bx))  
        height = max(0, min(rect1.ty, rect2.ty) - max(rect1.by, rect2.by))  
        return height * width  
  
    @staticmethod  
    def roi(rect1, rect2):  
        # Calculate and return a new rectangle representing the region of intersection between two rectangles  
        x1, y1 = max(rect1.bx, rect2.bx), max(rect1.by, rect2.by)  
        x2, y2 = min(rect1.tx, rect2.tx), min(rect1.ty, rect2.ty)  
        return Rectangle(x1, y1, x2, y2)  
  
  
def main():  
    # Read input from standard input and initialize rectangles  
    bx, by, tx, ty = map(int, inp().split())  
    lawnmower = Rectangle(bx, by, tx, ty)  
    bx, by, tx, ty = map(int, inp().split())  
    bill = Rectangle(bx, by, tx, ty)  
  
    # Calculate initial area of lawnmower and area of intersection with billboard  
    tarp_area = lawnmower.area()  
    area = Rectangle.intersection(lawnmower, bill)  
  
    if area:  
        # If there is an intersection, calculate the region of intersection  
        tarp = Rectangle.roi(lawnmower, bill)  
        if (tarp.length == lawnmower.length or tarp.breadth == lawnmower.breadth) and (  
                tarp.bottom == lawnmower.bottom or tarp.top == lawnmower.top):  
            # If the region of intersection is the same as the lawnmower, subtract it from the total area  
            tarp_area = max(0, tarp_area - area)  
  
    # Output the remaining area of the lawnmower  
    out(f'{tarp_area}\n')  
    flush()  
  
  
if __name__ == "__main__":  
    # Initialize standard input and output and run main function  
    file('billboard')  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    main()
```

# IMPLEMENTATION 2:

```python
fin, fout = open("billboard.in"), open("billboard.out", "w")

x1, y1, x2, y2 = map(int, fin.readline().split())
x3, y3, x4, y4 = map(int, fin.readline().split())

# which corners are covered by the feed billboard
tl_corner = x3 <= x1 and y4 >= y2
tr_corner = y4 >= y2 and x4 >= x2
br_corner = x4 >= x2 and y3 <= y1
bl_corner = y3 <= y1 and x3 <= x1

corner_num = sum([tl_corner, tr_corner, br_corner, bl_corner])
# if these two corners are covered, the lawnmower billboard is completely covered
if bl_corner and tr_corner:
	fout.write(str(0))

elif corner_num in [0, 1]:
	fout.write(str(abs(x2 - x1) * abs(y2 - y1)))

elif br_corner and tr_corner:
	fout.write(str(abs(y2 - y1) * abs(x2 - x4)))

elif bl_corner and tl_corner:
	fout.write(str(abs(y2 - y1) * abs(x2 - x4)))

elif tr_corner and tl_corner:
	fout.write(str(abs(x2 - x1) * abs(y3 - y1)))

elif br_corner and bl_corner:
	fout.write(str(abs(x2 - x1) * abs(y3 - y1)))
```