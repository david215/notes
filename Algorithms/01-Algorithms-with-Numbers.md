# Prologue
- 3 questions about algorithms:
    1. Correctness.
    2. Time complexity as a function of n, where n is the size of the input.
    3. Can we do better?
- exponential, polynomial, logarithmic...
# 1.1 Basic arithmetic
- bit complexity
    - we want time complexity as a function of the size of the input, to be more
      specific, the *number of bits* of the input.
### 1.1.1 Addition
- the bit complexity of binary addition is O(n).
    - even though it is easy to think that binary addition can be done in a
      single instruction, for much larger numbers, binary addition is very much
      like performing the operations bit by bit.
### 1.1.2 Multiplication and division
- the bit complexity of multiplication and division is O(n^2), i.e. quadratic.
    - from a bit complexity point of view, there are n (not log n!) recursive
      calls when an input is halved every call, because an input being halved is
      equivalent to a right shift.
    - each recursive call has time complexity of O(n) because binary addition is
      linear.
- multiplication pseudocode 
```
function multiply(x, y):
    if y = 0: return 0
    z = multiply(x, y>>1)
    if y is even: return 2z
    else: return x + 2z
```
- division pseudocode
```
function divide(x, y):
    if x = 0: return (q, r) = (0, 0)
    (q, r) = divide(x>>1, y) 
    q = 2q, r = 2r
    if x is odd: r = r + 1
    if r >= y: r = r - y, q = q + 1
    return (q, r)
```
# 1.2 Modular arithmetic
# 1.3 Primality testing
# 1.4 Cryptography
# 1.5 Universal hashing

