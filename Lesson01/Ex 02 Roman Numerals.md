### Roman Numerals

**Part I**

Implement a function/method that converts from Roman to decimal numerals, taking into account the following rules:

Relationship between figures
```
I          1
V          5
X         10
L         50
C        100
D        500
M       1000
```

In Roman numbers:
- Larger values preceding smaller or equal ones keep their value (e.g., `MDCCCLXVII = 1000 + 500 + (100 * 3) + 50 + 10 + 5 + (1 * 2) = 1867`)
- When a value precedes a larger one, it means subtraction (e.g, `XCIV = (100 – 10) + (5 – 1) = 94`)
- `I, X, C, M` can be repeated up to 3 times consecutively (e.g., 4 is `IV`, not `IIII`)
- `V, L, D` cannot be repeated
- Only `I, X, C` can be used as subtractive numerals
- The largest value that can be represented is 3999 (`MMMCMXCIX`)

**Part II**

Write unit tests for the function/method.
