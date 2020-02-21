# Prologue
- 3 questions about algorithms:
    1. Correctness.
    2. Time complexity as a function of n, where n is the size of the input.
    3. Can we do better?
- exponential, polynomial, logarithmic...
# 1.1 Basic arithmetic
- Bit complexity
    - We want time complexity as a function of the size of the input, i.e. the
      *number of bits* of the input.
    - As a convention, N = input and n = input size.
        - e.g. if N = 2^10 = 1024, then n = 10.
    - Why does it matter?
        - For very large numbers, the size of the input itself becomes an
          important factor that determines the overall time complexity.
### 1.1.1 Addition
- The bit complexity of binary addition is O(n).
    - Not O(1)! Addition of numbers smaller than word size can be performed in a
      single instruction, but such is not the case for much larger numbers.
### 1.1.2 Multiplication and division
- The bit complexity of multiplication and division is O(n^2).
    - From a bit complexity point of view, there are n (not log n!) recursive
      calls when an input is halved every call, because an input being halved is
      equivalent to a right shift.
    - Each recursive call has time complexity of o(n) because binary addition is
      linear.
- Multiplication pseudocode 
```
function multiply(x, y):
    if y = 0:
        return 0
    else if y is even:
        return 2 * multiply(x, y//2)
    else:
        return x + (2 * multiply(x, y//2))
```
- Division pseudocode
```
function divide(x, y):
    if x = 0:
        return (q, r) = (0, 0)
    else:
        (q, r) = divide(x//2, y) 
        q = 2q, r = 2r
        if x is odd: r = r + 1
        if r >= y: r = r - y, q = q + 1
        return (q, r)
```
# 1.2 Modular arithmetic
- Why is it important?
    - For many applications, e.g. primality testing and cryptography, we have to
      deal with very large numbers.
    - Modular arithmetic provides ways to efficiently perform arithmetic
      operations of such large numbers.
- Modular congruence
    - Definition
        - Numbers x and y are congruent modulo N iff x % N = y & N.
    - Notation
        - x ≡ y (mod N)
    - Congruence class
        - is a set of such congruent numbers.
        - for any number N, there are N congruence classes.
            - e.g. for N = 3:
                - {..., -6, -3, 0, 3, 6, ...}
                - {..., -5, -2, 1, 4, 7, ...}
                - {..., -4, -1, 2, 5, 8, ...}
    - Substitution rule
        - any member of a congruence class is substitutable for any other.
- Characteristics
    - Addition, multiplication are associative, commutative, and distributive.
    - Together with the substitution rule, such characteristics can be used to
      dramatically simplify calculation of large numbers.
        - e.g. 2^345 ≡ (2^5)^69 ≡ 32^69 ≡ 1^69 ≡ 1 (mod 31)
### 1.2.1 Modular addition and multiplication
- The bit complexity of modular addition is O(n).
    - Modular addition of numbers x and y modulo N consists of:
        - Addition of numbers at most n bits long - O(n).
        - (Optional) Subtraction of numbers at most n + 1 bits long - O(n).
- The bit complexity of modular multiplication is O(n^2).
    - Modular multiplication of numbers x and y modulo N consists of:
        - Multiplication of numbers at most n bits long - O(n^2).
        - (Optional) Division of a numbers at most 2n bits long - O(n^2). 
### 1.2.2 Modular exponentiation
### 1.2.3 Euclid's algorithm for greatest common divisor
### 1.2.4 An extension of Euclid's algorithm
### 1.2.5 Modular division
# 1.3 Primality testing
# 1.4 Cryptography
# 1.5 Universal hashing

