## Summary:
tic tac game with each letter of alphabet. Need to find the if there is a single letter or group of 2 letter that can form a row, col or diagonal in the given matrix

# OBSERVATION:
- using set , track each element in a row, col and matrix. Rotating 90 once will cover all the possible way of forming the words

# IMPLEMENTATION:

```py
import sys  
  
  
def file(name):  
    # Redirect standard input/output to input/output files  
    sys.stdin = open(name + '.in', 'r')  
    sys.stdout = open(name + '.out', 'w')  
  
  
def main():  
    # Initialize input/output functions  
    inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
  
    # Read in the tic-tac-toe board as a 2D list of characters  
    matrix = [list(inp().strip()) for _ in range(3)]  
  
    # Initialize sets to keep track of single and double winners  
    singles, doubles = set(), set()  
  
    # Loop through the rows and columns of the board  
    for _ in range(2):  
        diagonal, i = '', 0  
        for row in matrix:  
            letters, diagonal, i = set(row), diagonal + row[i], i + 1  
            # Check for single and double winners in each row  
            if len(letters) == 1:  
                singles |= letters  
            elif len(letters) == 2:  
                doubles |= {tuple(sorted(letters))}  
  
        # Check for single and double winners in the diagonal  
        letters = set(diagonal)  
        if len(letters) == 1:  
            singles |= letters  
        elif len(letters) == 2:  
            doubles |= {tuple(sorted(letters))}  
  
        # Rotate the board 90 degrees for the next iteration  
        matrix = [list(row) for row in list(zip(*matrix[::-1]))]  
  
    # Output the number of single and double winners  
    out('{}\n{}\n'.format(len(singles), len(doubles)))  
  
  
if __name__ == "__main__":  
    # Call file() function to redirect standard input/output  
    file('tttt')  
    main()
```