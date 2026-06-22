# Greatest Common Divisor

## Problem Summary

Given two non-negative integers `a` and `b`, return their greatest common divisor.

## Core Idea

GCD có thể được rút gọn bằng công thức:
`gcd(a, b) = gcd(b, a % b)`
Lặp lại cho đến khi `b = 0`.

## Pattern

- Math
- Euclidean Algorithm

## Brute Force Solution

### Intuition

Thử từng số từ `min(a, b)` giảm về 1. Số đầu tiên chia hết cả hai là GCD.

### Complexity

- Time: O(min(a, b))
- Space: O(1)

## Optimized Solution

### Intuition

Dùng Euclidean Algorithm. Mỗi bước thay bài toán lớn bằng bài toán nhỏ hơn.

### Algorithm

1. While `b != 0`
2. Update `a, b = b, a % b`
3. Return `a`

### Complexity

- Time: O(log min(a, b))
- Space: O(1)

## Edge Cases

| Case | Expected | Why important |
|---|---|---|
| gcd(0, 0) | 0 | Theo convention |
| gcd(a, 0) | a | b = 0 thì return a |
| gcd(0, b) | b | Sau 1 vòng lặp sẽ return b |
| gcd(12, 18) | 6 | a không cần lớn hơn b |

## Final Code

```python
class Solution:
    def gcd(self, a: int, b: int) -> int:
        while b != 0:
            a, b = b, a % b
        return a
```

## What I Learned

- Không cần đảm bảo a > b.
- Nếu a < b, bước đầu tiên sẽ tự swap gián tiếp.
- Phải tránh a % b khi b = 0.
