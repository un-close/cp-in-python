## Summary:
There are N boards lying in the ground with each having 2 animals name. We want to find minimum frequency of letters required to show all the possible combination of animal name that can be formed.

# OBSERVATION:
- the N given is is in the range 100, so the no of words at most possible is 200.
- in a board, one of the two words are available for the combination and taking the maximum frequency of a letter from the both and repeating this for the rest of the board will guarantee as that we have just enough frequency of letters in order to form any combination of words that may be formed

# IMPLEMENTATION:
```py
# time complexity : 0(n * L) L = length of the longest word  
# using dict compression  
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
    N = int(inp())  
    freq = {chr(c): 0 for c in range(ord('a'), ord('z') + 1)}  
    for _ in range(N):  
        word1, word2 = inp().split()  
        freq1, freq2 = {c: word1.count(c) for c in freq}, {c: word2.count(c) for c in freq}  
        freq = {c: freq[c] + max(freq1[c], freq2[c]) for c in freq}  
    out('\n'.join(str(value) for value in freq.values()))  
  
  
if __name__ == "__main__":  
    file('blocks')  
    main()
```