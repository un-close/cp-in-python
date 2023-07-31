## Summary:
check whether 2 strings can be made equal if '@' in them can be replaced by any letter from 'atcoder' and u can also re-arrange as u please.

# INTUITION:
- the no of '@' character should be equal to the no of character missing in the other string and the missing character must be a character from 'atcoder' too.

# IMPLEMENTATION:
```python
from collections import Counter

s1, s2 = list(input().strip()), list(input().strip())
set_atcoder, freq1, freq2 = set(list('atcoder')), Counter(s1), Counter(s2)
at1, at2, diff_s1, diff_s2 = freq1['@'], freq2['@'], 0, 0
total_char, is_possible = set(list(freq1.keys()) + list(freq2.keys())), True
for char in total_char:
    if char != '@':
        diff = freq1.get(char, 0) - freq2.get(char, 0)
        if char in set_atcoder:
            diff_s2, diff_s1 = diff_s2 + max(0, diff), diff_s1 + max(0, -diff)
        elif diff != 0:
            is_possible = False
            break
if at1 < diff_s1 or at2 < diff_s2:
    is_possible = False
print('Yes' if is_possible else 'No')

```