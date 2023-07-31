## Summary:
Determine the number of times the cow with the highest milk production changes, taking into account that ties are also considered as changes.

# OBSERVATION:
- the days in which update take place are random, so need to sort them
- should have an dictionary to track the change in the production of different cows
- a list called display to show the current highest milk producing cows and checking after each update if it still holds

# IMPLEMENTATION:
```py
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out = sys.stdin.readline, sys.stdout.write  
    n, updates, names = int(inp()), list(), ["Bessie", "Elsie", "Mildred"]  
    for _ in range(n):  
        day, cow, change = inp().split()  
        updates.append([int(day), cow, int(change)])  
    updates.sort()  
    cows, display, required_changes = {name: 7 for name in names}, names.copy(), 0  
    for _, cow, change in updates:  
        cows[cow] += change  
        max_amt = max(cows.values())  
        new_display = [name for name, amt in cows.items() if amt == max_amt]  
        required_changes += new_display != display  
        display = new_display  
    out(f'{required_changes}\n')  
  
  
if __name__ == "__main__":  
    file('measurement')  
    main()
```