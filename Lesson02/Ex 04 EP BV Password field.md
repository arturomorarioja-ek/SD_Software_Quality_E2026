### Password field
A password field accepts a minimum of 6 characters and a maximum of 10 characters. Define:

1. Its corresponding equivalence partitions and test case values
2. The boundary values and resulting test case values with a 3-boundary value approach
3. The final list of test case values

#### Solution

1. and 2. Equivalence partitions and boundary value analysis
   
|Partition type|Partitions|Test case values|Boundary values|Test case values|
|-|--:|--:|--:|--:|
|Invalid|0|0|0 1|0 1|
|Invalid|1-5|3|1 5|0 1 2 4 5 6|
|Valid|6-10|8|6 10|5 6 7 9 10 11|
|Invalid|11-MAX INTEGER|15|11|10 11 12|

3. List of test case values

`0` `1` `2` `3` `4` `5` `6` `7` `8` `9` `10` `11` `12` `15`
