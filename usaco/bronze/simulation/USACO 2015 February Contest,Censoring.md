## Summary:
Given two strings, magazine & censor , remove all the occurrence of censor from magazine.

# OBSERVATION:
- using string slicing from the end, we can check if censor is present and remove it

# IMPLEMENTATION:
```py
import sys  
  
  
def file(name):  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    inp, out = sys.stdin.readline, sys.stdout.write  
    word = inp().strip()  
    censor = inp().strip()  
    censored, l = str(), len(censor)  
    for letter in word:  
        censored += letter  
        if censored[-l:] == censor:  
            censored = censored[:-l]  
    out(censored + '\n')  
  
  
if __name__ == "__main__":  
    file('censor')  
    main()
```