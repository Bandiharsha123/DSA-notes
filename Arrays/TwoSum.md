# Two Sum

## Problem
Find two numbers whose sum equals the target.

---

## Logic

1. Create an empty dictionary.
2. Traverse the array.
3. Find the remaining value.
4. If remaining exists, return indices.
5. Otherwise, store current number and index.

---

## Code

```python
class Solution(object):
    def twoSum(self, nums, target):
        seen = {}

        for i in range(len(nums)):
            remaining = target - nums[i]

            if remaining in seen:
                return [seen[remaining], i]

            seen[nums[i]] = i
```

---

## Dry Run

nums = [3,2,4]

target = 6

i=0

remaining=3

seen={}

store {3:0}

i=1

remaining=4

store {2:1}

i=2

remaining=2

2 exists in seen

return [1,2]

---

## Time Complexity

O(n)

---

## Space Complexity

O(n)

---

## Important Points

- Dictionary stores number → index.
- Calculate remaining before storing.
- HashMap lookup is O(1).
