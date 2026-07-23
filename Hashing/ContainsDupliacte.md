# Contains Duplicate

## Problem

Given an integer array `nums`, return `True` if any value appears at least twice in the array. Otherwise, return `False`.

---

## Pattern

**Hashing (Set)**

---

## Logic

1. Create an empty set called `seen`.
2. Traverse each element in the array.
3. Check if the current element already exists in `seen`.
   - If yes, a duplicate is found, so return `True`.
4. Otherwise, add the current element to `seen`.
5. If the loop finishes without finding any duplicate, return `False`.

---

## Code with Explanation

```python
class Solution(object):          # Define the Solution class

    def containsDuplicate(self, nums):   # Function to check duplicates

        seen = set()            # Create an empty set to store unique elements

        # Traverse each element in the array
        for i in nums:

            # Check if the current element is already in the set
            if i in seen:

                # Duplicate found
                return True

            # Add the current element to the set
            seen.add(i)

        # No duplicates found after checking all elements
        return False
```

---

## Dry Run

### Input

```python
nums = [1, 2, 3, 1]
```

| Current Element | Seen Before | Duplicate? | Seen After |
|-----------------|-------------|------------|------------|
| 1 | {} | No | {1} |
| 2 | {1} | No | {1,2} |
| 3 | {1,2} | No | {1,2,3} |
| 1 | {1,2,3} | Yes | Return True |

---

## Why Set?

A **set** stores only unique values.

Example:

```python
seen = set()

seen.add(10)
seen.add(20)
seen.add(10)

print(seen)
```

Output:

```
{10, 20}
```

The second `10` is ignored because sets do not allow duplicate values.

---

## Time Complexity

- Traversing the array → **O(n)**
- Set lookup (`in`) → **O(1)** average

**Overall:** **O(n)**

---

## Space Complexity

The set may store every unique element.

**O(n)**

---

## Key Points to Remember

- Use a **set** when you only need to know whether an element has already appeared.
- Sets provide **O(1)** average lookup and insertion.
- Return immediately when a duplicate is found.
- If the loop completes, there are no duplicates.

---

## Mistakes to Avoid

❌ Using a list instead of a set (lookup becomes O(n)).

❌ Forgetting to add the current element to the set.

❌ Returning `False` inside the loop instead of after the loop.