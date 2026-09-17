### Measure converter

**Part I**

Create several classes that perform several measure conversions according to the following specification:
- Length
  - Conversion between the Metric and Imperial systems
  - It only covers centimeters and inches, respectively
  - Length class. Methods:
    - Constructor
      - @param. The numeric measure to convert with up to two decimals
      - @param. The system of said measure (Metric or Imperial)
    - convert()
      - It implements an if (if the system is Metric then … otherwise …)
      - @return. The value of the conversion with up to two decimals
  - Weight
    - Conversion between the Metric and Imperial systems
    - It only covers kilograms and pounds, respectively
    - Free class implementation
  - Temperature
    - Conversion between the Celsius, Fahrenheit, and Kelvin scales
    - Temperature class. Methods:
      - Constructor
        - @param. The numeric measure to convert with up to two decimals
        - @param. The temperature scale of said measure
      - convert()
        - It implements a switch with the 6 possible conversions (C to F, C to K, F to C, F to K, K to C, K to F)
        - Each switch calls a method that performs the specific conversion
        - @param. The destination temperature scale
        - @return. The value of the conversion with up to two decimals
  - Currency
    - Conversion between world currencies
    - Currency class. Methods:
      - Constructor
        - @param. The base currency in 3-letter format (e.g., 'DKK')
      - convert()
        - It calls the API https://freecurrencyapi.net/. This API has an endpoint that returns the conversion rate from the given currency to all other currencies. Use it for this method.
        - @param. The numeric amount to convert with up to two decimals
        - @return. The converted monetary amount with up to two decimals
  - Grades
    - Conversion between the Danish and American grading systems
    - Grade class. Methods:
      - convert()
        - It queries a local database with the conversion information
        - Free choice of database model and DBMS ([MySQL script below]())
        - Possible implementation:

          ​​​​![image](https://github.com/user-attachments/assets/e5bd4dbb-94c6-42b4-bb14-ae05c617c4c8)

        - @param. The grade to convert
        - @param. The country to whose grading system the grade corresponds to
        - @return. The converted grade
 
**Part II**

- Design unit tests for all the classes
  - Use black-box design techniques
- Design a comprehensive set of test cases
  - Look for paradigmatic and boundary values
  - Look for extreme cases
- Write beautiful, efficient, maintainable unit tests
  - Use data providers
  - For Currency and Grades, do it in two different ways:
    - Testing against the dependencies (API/database)
    - Mocking the dependencies

If you cannot finish the whole assignment, work on some specific conversion (preferably currency or grades) and the corresponding tests.
