### Framing shop
The system calculates the price of picture framing based on the given parameters: width and height of the picture (in centimeters provided as integers). The valid width of the picture is between 30 and 100 cm inclusive. The valid height of the picture is between 30 and 60 cm inclusive. The system calculates the area of the image as the product of width and height. If the surface area exceeds 1600 cm<sup>2</sup>, the framing price is 3500 kr. Otherwise, the framing price is 3000 kr.

Use black-box analysis to identify a comprehensive series of test cases:
1. Identify the corresponding equivalence partitions and propose test cases based on them
2. Use 3-value boundary value analysis to identify further test cases
3. Write down the full resulting list of test case values
4. Implement the discount calculation function in code and write the corresponding unit tests in the language and unit test framework of your choice

<sub>Adapted from Stapp, Lucjan, Roman, Adam, and Michaël Pilaeten (2024). _ISTQB Certified Tester Foundation Level: A Self-Study Guide Syllabus v4.0_. Springer.</sub>

#### Solution

<img width="895" height="584" alt="image" src="https://github.com/user-attachments/assets/abe2a965-d5cb-42ec-8c72-f9ee0e467292" />

1. Equivalence partitions

Besides using black-box analysis on the parameters (width and height), it could be interesting to apply it to the area, as it is a calculated value upon which the calculations depend. As this is based in knowledge of the requirements specification, not of the code, it can still be considered a black-box approach.

Negative values and the zero partition have been excluded from the analysis for the sake of simplicity. They should be taken into account in a real-life situation.

||Valid|Invalid|
|-|--:|--:|
|Width|30-100|0-29|
|||101-MAX INTEGER|
|Height|30-60|0-29|
|||61-MAX INTEGER|
|Area|0-1600||
||1601-MAX INTEGER||

Potential test case values:
- Width `15 cm` `70 cm` `180 cm` (partition middle values)
- Height `15 cm` `45 cm` `95 cm` (partition middle values)
- Width `20 cm` and height `30 cm` (middle value for the valid area partition = `600 cm`)
- Width `50 cm` and height `50 cm` (middle value for the invalid area partition = `2500 cm`)

2. 3-value boundary value analysis

|Value|Partition types|Partitions|Boundary values|Test case values|
|-|-|--:|--:|--:|
|Width|Invalid|0-29|0 29|0 1 28 29 30|
||Valid|30-100|30 100|29 30 31 99 100 101|
||Invalid|101-MAX INTEGER|101|100 101 102|
|Height|Invalid|0-29|0 29|0 1 28 29 30|
||Valid|30-60|30 60|29 30 31 59 60 61|
||Invalid|61-MAX INTEGER|61|60 61 62|
|Area|Valid|0-1600|0 1600|0 1 1599 1600 1601|
||Valid|1601-MAX INTEGER|1601|1600 1601 1602|
   
3. List of test case values

- Width: `0` `1` `15` `28` `29` `30` `31` `70` `99` `100` `101` `180`
- Height: `0` `1` `15` `28` `29` `30` `31` `45` `59` `60` `61` `95`
- To create efficient test cases based on these values, one must analyse width and height combinations leading to specific area values:
   - An area of 0 cm<sup>2</sup> (0 cm<sup>2</sup> height * 0 cm<sup>2</sup> width) cannot be tested, as the width and height values would be below range (0 and 0)
   - An area of 1 cm<sup>2</sup> (1 cm<sup>2</sup> height * 1 cm<sup>2</sup> width) cannot be tested, as the width and height values would be below range (1 and 1)
   - An area of 600 cm<sup>2</sup> cannot be tested, as the width and height values would be below range
   - Width `39` and height `41` => area `1599`
   - Width `40` and height `40` => area `1600`
   - An area of 1601 cm<sup>2</sup> cannot be tested, as it is prime, thus no width and height values exist whose product is 1601
   - An area of 1602 cm<sup>2</sup> cannot be tested, as there is no pair of integers in the provided range whose product is 1602
   - Width `50` and height `50` => area `2500`

4. Code solution

- [Python/Pytest](https://github.com/arturomorarioja/py_framing_shop_unit_tests)
- [JavaScript/Jest](https://github.com/arturomorarioja/js_framing_shop_unit_tests)
- [PHP8/PHPUnit](https://github.com/arturomorarioja/php_framing_shop_unit_tests)
