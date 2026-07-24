# Valid Anagram

## Problem

Given two strings `s` and `t`, return `True` if `t` is an anagram of `s`. Otherwise, return `False`.

An anagram contains the same characters with the same frequencies, but possibly in a different order.

Example:

```text
s = "anagram"
t = "nagaram"

Output: True
```

---

# Approach 1: Sorting

## Logic

1. Sort the characters of `s`.
2. Sort the characters of `t`.
3. Convert the sorted characters back into strings using `join()`.
4. Compare both strings.
5. If they are equal, return `True`.

## Code

```python
class Solution(object):
    def isAnagram(self, s, t):

        # Sort s and convert the list back into a string
        ss = ''.join(sorted(s))

        # Sort t and convert the list back into a string
        tt = ''.join(sorted(t))

        # Compare both sorted strings
        return ss == tt
```

## Time Complexity

**O(n log n)** because sorting takes O(n log n).

---

# Approach 2: Hashing

## Logic

1. If the lengths are different, return `False`.
2. Create an empty dictionary called `count`.
3. Traverse `s` and count the frequency of every character.
4. Traverse `t` and decrease the frequency.
5. If a character doesn't exist or its count goes below zero, return `False`.
6. Otherwise, return `True`.

## Code

```python
class Solution(object):
    def isAnagram(self, s, t):

        # Anagrams must have the same length
        if len(s) != len(t):
            return False

        # Dictionary to store character frequencies
        count = {}

        # Count characters in s
        for i in s:
            if i in count:
                count[i] += 1
            else:
                count[i] = 1

        # Subtract characters using t
        for i in t:

            # Character doesn't exist in s
            if i not in count:
                return False

            count[i] -= 1

            # t contains this character too many times
            if count[i] < 0:
                return False

        return True
```

## Time Complexity

**O(n)** average.

## Space Complexity

**O(n)** in the general case.

---

# Comparison

| Approach | Time Complexity | Main Concept |
|----------|-----------------|--------------|
| Sorting | O(n log n) | Sorting |
| Hashing | O(n) average | Dictionary / Hash Map |

## Best Approach

**Hashing** is asymptotically faster because it avoids sorting.

---

# Key Point to Remember

### Sorting

```text
Sort s
Sort t
Compare
```

### Hashing

```text
Count characters in s
        ↓
Subtract characters using t
        ↓
If counts match → Anagram
```

---

# What I Learned

- `sorted()` returns a list.
- `''.join()` converts the sorted characters into a string.
- A dictionary can store `character → frequency`.
- Hashing improves the average time from O(n log n) to O(n).