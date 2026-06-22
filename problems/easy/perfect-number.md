# Perfect Number

## Problem Summary

Return true if `num` equals the sum of its proper divisors.

## Core Idea

Divisors come in pairs. If `i` divides `n`, then `n // i` is also a divisor.

## Pattern

- Math
- Divisor Pairs
- Square Root Optimization

## Brute Force Solution

### Intuition

Scan all numbers from `1` to `n - 1` and sum the divisors.

### Complexity

- Time: O(n)
- Space: O(1)

## Optimized Solution

### Intuition

Only scan from `2` to `sqrt(n)`. When finding one divisor, add both it and its paired divisor.

### Key Observation

If `i * pair = n`, then one of them is `<= sqrt(n)`.

### Algorithm

1. If `num <= 1`, return False
2. Initialize `total = 1`
3. Iterate `i` from 2 up to `sqrt(num)`
4. If `num % i == 0`, add `i` to `total` and if `i != num // i`, add `num // i` to `total`
5. Return whether `total == num`

### Complexity

- Time: O(sqrt(n))
- Space: O(1)

## Edge Cases

| Case | Expected | Why important |
|---|---|---|
| num <= 1 | False | No proper divisor sum equals num |
| num = 28 | True | Classic perfect number |
| num = 36 | False | Square root divisor should not be double-counted |
| num is prime | False | Only divisor is 1 |

## Final Code

```python
class Solution:
    def checkPerfectNumber(self, num: int) -> bool:
        if num <= 1:
            return False

        total = 1

        i = 2
        while i * i <= num:
            if num % i == 0:
                total += i

                pair = num // i
                if pair != i:
                    total += pair

            i += 1

        return total == num
```

## What I Learned

- Divisors appear in pairs.
- Scanning to sqrt(n) is enough.
- Need to avoid adding n itself.
- Need to avoid double-counting when i == n // i.
