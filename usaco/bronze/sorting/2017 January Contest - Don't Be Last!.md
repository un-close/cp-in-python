## Summary:
There are 7 cows and we have the logging of the amount of milk they produce. From the data we have to find the second smallest milk producing cow. There are multiple or none, print 'tie'.
# OBSERVATION:
- there are 7 cows, so making a dict and tracking the amount of milk will do the trick

# IMPLEMENTATION:
```py
import sys  
  
sys.stdin = open("notlast.in", "r")  
sys.stdout = open("notlast.out", "w")  
  
inp = sys.stdin.readline  
out = sys.stdout.write  
flush = sys.stdout.flush  
  
cows = {'Bessie': 0, 'Elsie': 0, 'Daisy': 0, 'Gertie': 0, 'Annabelle': 0, 'Maggie': 0, 'Henrietta': 0}  
n = int(inp())  
for _ in range(n):  
    name, milk = inp().split()  
    cows[name] += int(milk)  
k = 2  # here the second-smallest cow is asked  
if len(set(cows.values())) < k:  
    out('Tie\n')  
    sys.exit()  
kth_smallest_value = sorted(set(cows.values()))[k - 1]  
potential_cows = [cow for cow, milk in cows.items() if milk == kth_smallest_value]  
if len(potential_cows) == 1:  
    out(f'{potential_cows[0]}\n')  
else:  
    out('Tie\n')  
flush()
```