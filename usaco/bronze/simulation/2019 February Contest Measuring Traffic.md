## Summary:
Given a range of of inflow, outflow and current traffic flow , output the precise range of inflow before the start of 1st mile and after Nth mile.

# OBSERVATION:
- taking the limit as (-inf, inf) initially and making changes as u go would output the desired answer
- for the part where the current traffic flow is taken, we take the max of the lower and min of the upper limit as the current traffic flow guarantees the limit is surely inside the given limits
- For the 'on' and 'off' part, it depends on which inflow you are calculating. If you are calculating the inflow for the last mile, you would sweep from the initial mile, and for the 'off' or 'outflow' range, all possible ranges that can be formed are the current lower limit minus the higher limit of the 'outflow' and the current high limit minus the lower limit of the 'outflow'. This will include all possible ranges that can be expressed.

# IMPLEMENTATION:
```py
import sys

def file(name): # not here

    sys.stdin = open(name + '.in', 'r')

    sys.stdout = open(name + '.out', 'w')

def limit(road, direction): # custom function for the given program

    left, right = float('-inf'), float('inf')

    for pos, lower, higher in road:

        lower, higher = int(lower), int(higher)

        if pos == 'none':

            left, right = max(left, lower), min(right, higher)

        elif pos == ('on', 'off')[direction]:

            left += lower

            right += higher

        else:   # tricky

            left -= higher

            right -= lower

            left = max(0, left)

    return left, right

def main():

    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush    # for faster I/0

    n = int(inp())

    Road = list(list())

    for _ in range(n):

        sensor = inp().split()

        Road.append(sensor)

    for i in (-1, 1):

        s_l, s_h = limit(Road[::i], i == -1)

        out(f'{s_l} {s_h}\n')

        flush()

if __name__ == "__main__":

    file('traffic') # here.

    main()
```
