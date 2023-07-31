## Summary:
The problem involves processing a 2D grid of cells and a sequence of statements describing a mowing pattern. The program needs to determine the maximum possible value of time x such that when FJ mows the grass according to the given pattern, he never encounters a cell in which the grass is already cut. In other words, every time FJ visits a cell, his most recent visit to that same cell must have been at least x units of time earlier, in order for the grass to have grown back.

# OBSERVATION:
- As there are four direction to choose from, assign each a axis of 2-D plane.
- To track the last time visited, having an dictionary with key as the coordinates and value as the last time it was visited is good.
- As its guaranteed that the second or the subsequent visits are more than the regrowth time taken for the grass, we just have to find the minimum time between subsequent visits as this will give as the largest possible regrowth time.

# IMPLEMENTATION:
```py
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out = sys.stdin.readline, sys.stdout.write  
    n = int(inp())  
    direction = {'N': (1, 0), 'S': (-1, 0), 'E': (0, 1), 'W': (0, -1)}  # co-ordinates for each direction  
    visited, curr, time, min_time, guide = {(0, 0): 0}, (0, 0), 0, float('inf'), list()  
    for _ in range(n):  
        direct, distances = inp().split()  
        guide.append([direct, int(distances)])  
  
    for direct, distance in guide:  # for each query in guide  
        delta = direction[direct]  # getting the co-ordinates for traveling in the direct. for distances times  
        for _ in range(distance):  
            time += 1  
            curr = (curr[0] + delta[0], curr[1] + delta[1])  
            if curr in visited:  # checking if this cell was visited before  
                min_time = min(min_time, time - visited[curr])  
            visited[curr] = time  # updating the time in which the cell was visited  
  
    res = -1 if min_time == float('inf') else min_time  
    out(f'{res}\n')  
  
  
if __name__ == "__main__":  
    file('mowing')  
    main()
```