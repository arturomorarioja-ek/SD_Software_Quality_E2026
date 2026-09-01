### Printer cartridges
A wholesaler sells printer cartridges. The minimum order quantity is 5. There is a 20% discount for orders of 100 or more printer cartridges. You have been asked to prepare test cases using various values for the number of printer cartridges ordered.

Use black-box analysis to identify a comprehensive series of test cases:
1. Identify the corresponding equivalence partitions and propose test cases based on them
2. Use 3-value boundary value analysis to identify further test cases
3. Write down the full resulting list of test cases
4. Implement the discount calculation function in code and write the corresponding unit tests in the language and unit test framework of your choice

<sub>Adapted from Hambling, Brian (2019). *Software Testing: An ISTQB-BCS Certified Tester Foundation Guide*, 4th ed.</sub>

#### Solution

1. and 2. Equivalence partitions and 3-value boundary value analysis
   
|Partition type|Partitions|Test case values|Expected output|Boundary values|Test case values|
|-|--:|--:|--:|--:|--:|
|Invalid|MIN INTEGER- -1|-15|Error|-1|-2 -1 0|
|Invalid|0|0|Error|0|-1 0 1|
|Invalid|1-4|2|Error|1 4|0 1 2 3 4 5|
|Valid|5-99|47|0% discount|5 99|4 5 6 98 99 100|
|Valid|100-MAX INTEGER|167|20% discount|100|99 100 101|

3. List of test cases
   
`-15` `-2` `-1` `0` `1` `2` `3` `4` `5` `6` `47` `98` `99` `100` `101` `167`

4. Code solution

- [Python/Pytest](https://github.com/arturomorarioja/py_cartridges_unit_tests)
- [JavaScript/Jest](https://github.com/arturomorarioja/js_cartridges_unit_tests)
- [PHP8/PHPUnit](https://github.com/arturomorarioja/php_printer_cartridges_unit_tests)
