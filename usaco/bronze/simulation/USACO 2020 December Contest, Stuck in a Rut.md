## Summary:
Find the intersection point of the cows from their starting point to the trail of the other cow which crossed the same point beforehand.

# OBSERVATION:
- sorting the east going cows by their y and north going cows by their x coordinates, we can simulate the event of intersection

# IMPLEMENTATION:
```python
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    north, east = list(), list()  
    n = int(inp())  
    for i, (dir, x, y) in enumerate(inp().split() for _ in range(n)):  
        if dir == 'E':  
            east.append([int(x), int(y), i])  
        else:  
            north.append([int(x), int(y), i])  
    east.sort(key=lambda a: a[1]), north.sort()  
    stop_pos, inf = [float('inf')] * n, float('inf')  
    for north_cow in north:  
        for east_cow in east:  
            if north_cow[0] > east_cow[0] and north_cow[1] < east_cow[1] and stop_pos[north_cow[-1]] == stop_pos[east_cow[-1]] == inf:  
                x_inter, y_inter = north_cow[0] - east_cow[0], east_cow[1] - north_cow[1]  
                if x_inter < y_inter:  
                    stop_pos[north_cow[-1]] = east_cow[1]  
                    break  
                if x_inter > y_inter:  
                    stop_pos[east_cow[-1]] = north_cow[0]  
    ans = ['Infinity'] * n  
    for i, (x, y, index) in enumerate(north + east):  
        if stop_pos[index] != inf:  
            if i < len(north):  
                ans[index] = stop_pos[index] - y  
            else:  
                ans[index] = stop_pos[index] - x  
    print(*ans, sep='\n')  
    flush()  
  
  
if __name__ == "__main__":  
    # file('')  
    main()
```