### E-shop
You are testing the payment functionality of an e-shop. The system receives the amount of purchases in kroner with an accuracy of 1 øre. Based on this value, a discount is calculated according to the following rules:

|Amount|Discount|
|-|--:|
|Up to 300 kr|0%|
|Over 300 kr, up to 800 kr|5%|
|Over 800 kr|10%|

Use black-box analysis to identify a comprehensive series of test cases:
1. Identify the corresponding equivalence partitions and propose test cases based on them
2. Use 3-value boundary value analysis to identify further test cases
3. Write down the full resulting list of test cases
4. Implement the discount calculation function in code and write the corresponding unit tests in the language and unit test framework of your choice

<sub>Adapted from Stapp, Lucjan, Roman, Adam, and Michaël Pilaeten (2024). _ISTQB Certified Tester Foundation Level: A Self-Study Guide Syllabus v4.0_. Springer.</sub>

#### Solution

1. Equivalence partitions

|Partition type|Partition|Test cases|Expected output|
|-|-|--:|--:|
|Invalid|MIN DOUBLE- -0.01|-150 kr|0%|
|Invalid|0|0 kr|0%|
|Valid|0.01-300|150 kr|0%|
|Valid|300.01-800|550 kr|5%|
|Valid|800.01-MAX DOUBLE|900 kr|10%|

Notice that, although receiving a negative amount contradicts business rules, the system could receive such an amount. The first partition could be considered within the category of edge cases.

Potential test case values: `-150 kr`, `150 kr` `550 kr` `900 kr`.
   
2. 3-value boundary value analysis

|Partitions|Boundary values|Test case values|
|-|-|-|
|MIN DOUBLE- -0.01|-0.01|-0.02 -0.01 0|
|0|0|-0.01 0 0.01|
|0.01-300|0.01 300|0.01 0.02 299.99 300 300.01|
|300.01-800|300.01 800|300 300.01 300.02 799.99 800 800.01|
|800.01-MAX DOUBLE|800.01|800 800.01 800.02|

3. List of test cases

|Input value|Expected output|
|--:|--:|
|-150 kr|0%|
|-0.02 kr|0%|
|-0.01 kr|0%|
|0.00 kr|0%|
|0.01 kr|0%|
|0.02 kr|0%|
|150.00 kr|0%|
|299.99 kr|0%|
|300.00 kr|0%|
|300.01 kr|5%|
|300.02 kr|5%|
|550.00 kr|5%|
|799.99 kr|5%|
|800.00 kr|5%|
|800.01 kr|10%|
|800.02 kr|10%|
|900.00 kr|10%|

4. Code solution
- [Python/Pytest](https://github.com/arturomorarioja/py_eshop_unit_tests)
- [JavaScript/Jest](https://github.com/arturomorarioja/js_eshop_unit_tests)
- [PHP8/PHPUnit](https://github.com/arturomorarioja/php_eshop_unit_tests)
