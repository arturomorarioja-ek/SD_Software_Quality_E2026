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

---

**Solution**

- JavaScript – Jest: https://github.com/arturomorarioja/js_roman_numerals
- Python – Pyunit: https://github.com/arturomorarioja/py_roman_numerals
- PHP – PHPUnit: https://github.com/arturomorarioja/php_roman_numerals

---

**ChatGPT 4o-generated test cases**

|Question|
|-|
|Can you provide a language-independent comprehensive set of unit test cases for a Roman to decimal numeral converter function? Apply black-box techniques.|


Absolutely. To design a language-independent, black-box unit test suite for a Roman-to-decimal numeral converter, we'll apply the following black-box testing techniques:
________________________________________
🧪 Testing Techniques Used
1.	Equivalence Partitioning – Divide inputs into valid/invalid groups.
2.	Boundary Value Analysis – Test limits of valid input ranges.
3.	Cause-Effect (Decision Table) Testing – For interpreting complex rules (like subtractive notation).
4.	Error Guessing – Based on known problems (e.g. repetition rules, invalid order).
5.	Combinatorial Testing – Test combinations of valid Roman characters.
________________________________________
✅ Assumptions of the Converter Function
- Input: String (e.g. "XIV")
- Output: Integer (e.g. 14)
- Supports standard Roman numerals: I, V, X, L, C, D, M
- Handles values from 1 to 3999
- Returns error/exception/null for invalid inputs
________________________________________
📋 Test Case Table (Black-Box Focused)

|#|Test Case|Input|Expected Output / Behavior|
|-|-|-|-|
|1|Valid simple numeral|"III|3|
|2|Valid subtractive notation|"IV|4|
|3|Valid complex numeral|"MCMXCIV|1994|
|4|Minimum valid value|"I|1|
|5|Maximum valid value|"MMMCMXCIX|3999|
|6|Empty string|""|Error/null|
|7|Invalid characters|"ABC"|Error/null|
|8|Repetition beyond allowed limit (IIII)|"IIII|Error|
|9|Valid repetition (XX, CCC)|"XXX"|30|
|10|Invalid subtractive combo (IC, IL, XM)|"IC"|Error|
|11|Valid subtractive + additive combo|"XLIX"|49|
|12|Mixed case input|"xv"|15 or Error (depending on spec)|
|13|Lowercase only|"xiv"|14 or Error|
|14|Embedded invalid characters|"MXD!IV"|Error|
|15|Reversed subtractive pattern (VX)|"VX"|Error|
|16|Valid long additive sequence|"MMMDCCCLXXXVIII"|3888|
|17|Internal whitespace|"M CM"|Error or ignore space|
|18|Input is number (wrong type)|1994|Error (if not string)|
|19|Input is null|null|Error or null|
|20|Duplicate subtractive pattern (IVIV)|"IVIV"|Error|
|21|Valid mix of all numeral types|"CDXLIV"|444|
|22|Excessive valid length|"MMMM"|Error (above 3999)|
|23|Valid single numeral|"L"|50|
|24|Input with trailing spaces|" X "|Trim or error|
|25|Input with newline or tab|"X\n" or "X\t"|Error|
________________________________________
🔎 Notes
- Language-independent: This test suite assumes nothing about how the function is implemented — only what its input/output contract should be.
- Design recommendation: You may want to distinguish between strict mode (e.g. case-sensitive, no whitespace) and lenient mode (e.g. ignore spaces/case).
________________________________________
🧰 Optional Enhancements
If you’re building a robust converter, you may want to:
- Add property-based tests (e.g. all valid Roman numerals from 1 to 3999 round-trip back correctly).
- Include localization tests if your app supports multiple languages.
________________________________________
Would you like this test suite in a specific format (e.g., Jest, PHPUnit, Python pytest, or Excel)?

|Question|
|-|
|All of these test cases are relevant, but I expect more. For example, you have not checked the minimum valid boundary value (I) or excessive repetitions of characters other than M (what if the programmer checked for M but not for C?). Can you expand the list with more relevant test cases (i.e., cases that may find errors without being redundant)?|

Excellent follow-up — you're absolutely right.
Your point reveals a deeper layer of black-box testing: attacking common implementation gaps (like only checking one symbol for repetition limits, or assuming only I, X, and C use subtractive notation). Let’s expand your test suite with more targeted, high-value cases to increase fault detection without redundancy.
________________________________________
🔍 Expanded Roman-to-Decimal Test Case Table
Here are 25 additional well-justified test cases that build on your original suite, targeting:
- Symbol-specific repetition
- Subtractive logic errors
- Edge-case patterns
- Input normalization gaps
- Unicode/formatting issues

|#|Test Case|Input|Expected Behavior|
|-|-|-|-|
|26|Minimum valid Roman numeral|"I"|1|
|27|Valid: M repeated 3 times|"MMM"|3000|
|28|Invalid: M repeated 4 times|"MMMM"|Error|
|29|Valid: C repeated 3 times|"CCC"|300|
|30|Invalid: C repeated 4 times|"CCCC"|Error|
|31|Invalid: X repeated 4 times|"XXXX"|Error|
|32|Valid: X repeated 3 times|"XXX"|30|
|33|Invalid: I repeated 4 times|"IIII"|Error|
|34|Invalid: V repeated twice|"VV"|Error|
|35|Invalid: L repeated twice|"LL"|Error|
|36|Invalid: D repeated twice|"DD"|Error|
|37|Valid subtractive: IX|"IX"|9|
|38|Invalid subtractive: IL|"IL"|Error|
|39|Invalid subtractive: IC|"IC"|Error|
|40|Invalid subtractive: VX|"VX"|Error|
|41|Invalid subtractive: LC|"LC"|Error|
|42|Invalid subtractive: DM|"DM"|Error|
|43|Valid subtractive: XL|"XL"|40|
|44|Valid subtractive: XC|"XC"|90|
|45|Valid subtractive: CD|"CD"|400|
|46|Valid subtractive: CM|"CM"|900|
|47|Valid mix: CDXCIX|"CDXCIX"|499|
|48|Trailing space|"X "|Error or Trim|
|49|Zero-width space (Unicode)|"XV"|Error|
|50|Unicode Roman numeral character (e.g., Ⅸ)|"Ⅸ"|Error (not standard Roman letters)|
________________________________________
🧠 Why These Matter
- Symbol-specific validation: Developers often validate I and forget X, C, or M.
- Wrong subtraction pairs: Easy to miss IC, VX, LD, etc.
- Edge behaviors: Spaces, Unicode punctuation, symbols from other alphabets.
- Normalization: Many bugs arise from untrimmed or malformed strings.
________________________________________
🧰 Additional Advanced Suggestions
If you want even more robust coverage, consider:
- ✔️ Round-trip tests: assertEqual(romanToInt(intToRoman(n)), n) for all 1–3999
- ✔️ Fuzz tests: Random invalid strings with valid-looking characters ("IMXM")
- ✔️ Locale tests: Accented or transliterated variants ("ÍV" or "V.")
- ✔️ Security tests: Extremely long input ("I"*10_000), non-ASCII injection
________________________________________
Would you like this list exported to a spreadsheet or translated into a specific testing framework (e.g., pytest, PHPUnit, Jest, etc.)?

|Assessment|
|-|
|ChatGPT found out that lowercase characters are ignored. Maybe converting them to uppercase could be considered.<br><br>It then raised a series of false positives because of lacking the specification and not knowing implementation details (e.g., “ABC” returns 0, as all three letters are ignored by the function).|
