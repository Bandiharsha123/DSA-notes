# Valid Palindrome

## Problem

Given a string `s`, return `True` if it is a palindrome after converting all uppercase letters to lowercase and removing all non-alphanumeric characters.

---

## Pattern

**String Manipulation**

---

## Logic

1. Create an empty string `ss`.
2. Traverse each character in the given string.
3. Check whether the character is alphanumeric using `isalnum()`.
4. If it is alphanumeric:
   - Convert it to lowercase.
   - Append it to `ss`.
5. After processing the string, compare `ss` with its reverse.
6. If both are equal, return `True`; otherwise, return `False`.

---

## Code with Explanation

```python
class Solution(object):          # Define the Solution class

    def isPalindrome(self, s):   # Function to check palindrome

        ss = ""                  # Empty string to store cleaned characters

        # Traverse each character in the string
        for i in s:

            # Check if the character is a letter or digit
            if i.isalnum():

                # Convert to lowercase and append to ss
                ss += i.lower()

        # Compare the cleaned string with its reverse
        return ss == ss[::-1]
```

---

## Dry Run

### Input

```python
s = "A man, a plan, a canal: Panama"
```

### Building `ss`

| Character | isalnum() | ss |
|-----------|-----------|-------------------------|
| A | Yes | a |
| space | No | a |
| m | Yes | am |
| a | Yes | ama |
| n | Yes | aman |
| , | No | aman |
| ... | ... | amanaplanacanalpanama |

Final:

```python
ss = "amanaplanacanalpanama"
```

Reverse:

```python
ss[::-1]
```

Result:

```python
True
```

---

## Important Methods

### `isalnum()`

Returns `True` if the character is a letter or digit.

```python
"A".isalnum()      # True
"7".isalnum()      # True
"#".isalnum()      # False
" ".isalnum()      # False
```

---

### `lower()`

Converts uppercase letters to lowercase.

```python
"A".lower()    # "a"
"Hello".lower()    # "hello"
```

---

### `[::-1]`

Reverses a string.

```python
"hello"[::-1]

Output:
"olleh"
```

---

## Time Complexity

- Traversing string → **O(n)**
- Reversing string → **O(n)**

Overall:

**O(n)**

---

## Space Complexity

Extra string `ss` stores the cleaned characters.

**O(n)**

---

## Key Points to Remember

- Ignore spaces and special characters.
- Convert all letters to lowercase.
- Compare the cleaned string with its reverse.
- `isalnum()` keeps only letters and digits.

---

## Mistakes to Avoid

❌ Forgetting to convert characters to lowercase.

❌ Not removing special characters.

❌ Comparing the original string instead of the cleaned string.