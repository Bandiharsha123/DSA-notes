# Valid Anagram

## Problem

Given two strings `s` and `t`, return `True` if `t` is an anagram of `s`. Otherwise, return `False`.

An anagram contains the same characters with the same frequencies, but the characters may be in a different order.

Example:

```text
s = "anagram"
t = "nagaram"

Output: True
```

---

## Approach

**Sorting**

If two strings are anagrams, sorting their characters will produce the same result.

Example:

```text
"eat" → "aet"
"tea" → "aet"
```

Since both sorted strings are equal, they are anagrams.

---

## Code with Explanation

```python
class Solution(object):              # Define the Solution class

    def isAnagram(self, s, t):       # Method takes two strings: s and t

        # sorted(s) sorts the characters of s
        # ''.join() converts the sorted characters back into a string
        ss = ''.join(sorted(s))

        # Sort the characters of t and convert them back into a string
        tt = ''.join(sorted(t))

        # Compare both sorted strings
        # If they are equal → True
        # Otherwise → False
        return ss == tt
```

---

## Important: Why `join()`?

`sorted()` does NOT return a string.

```python
sorted("eat")
```

returns:

```text
['a', 'e', 't']
```

This is a **list**.

So:

```python
''.join(sorted("eat"))
```

converts:

```text
['a', 'e', 't']
```

into:

```text
"aet"
```

The `''` means join the characters with **nothing between them**.

---

## Dry Run

```text
s = "rat"
t = "tar"
```

Sort `s`:

```text
sorted("rat")
→ ['a', 'r', 't']

''.join(...)
→ "art"
```

Therefore:

```text
ss = "art"
```

Sort `t`:

```text
sorted("tar")
→ ['a', 'r', 't']

''.join(...)
→ "art"
```

Therefore:

```text
tt = "art"
```

Compare:

```python
ss == tt

"art" == "art"

True
```

---

## Time Complexity

Sorting takes:

**O(n log n)**

So the overall time complexity is approximately:

**O(n log n)**

---

## Key Point to Remember

**Anagram + Sorting**

```text
Sort s
   ↓
Sort t
   ↓
Compare them
   ↓
Same → Anagram
Different → Not Anagram
```

---

## Mistake to Avoid

Make sure you sort both strings:

```python
ss = ''.join(sorted(s))
tt = ''.join(sorted(t))
```

Don't accidentally write:

```python
ss = ''.join(sorted(s))
tt = ''.join(sorted(s))   # ❌ s used again
```