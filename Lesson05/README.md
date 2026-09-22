[Software Quality - Autumn 2026](https://github.com/arturomorarioja-ek/SD_Software_Quality_E2026/blob/main/README.md)

# Lesson 5 - 22 September

[Slides DB testing]: #
  [Maybe have them practice a bit with in-memory DBs?]: #
[Slides CT]: #
  [Little GitHub Actions demo: py_length_converter, js_vat, php_printer_cartridges_unit_tests]: #
  [Two dependent job GitHub Actions demo: py_employee_unit_tests]: #
  [API Newman tests demo: https://github.com/arturomorarioja/customers_api]: #
  [Maybe have them make a CI pipeline that runs tests for their previous testing repos?]: #

[Homework: measure converter]: #

## Class takeaways
- Check out the following slide decks on Itslearning:
  - **Integration Testing**, with especial attention to
    - Advantages: protection against regressions, resistance to refactoring
    - Disadvantages: slow, difficult to maintain
    - Broad vs. narrow integration tests
  - **API Testing**. Focus on:
    - How do API calls usually fail?
    - What to test for?
    - An API testing tool (Postman, Insomnia, ThunderClient or any other platform that allows you to write API tests)
  - **Continuous Testing**. Notice:
    - The difference between CI, CT, CD and the other CD
- Check out the following code samples
  - Narrow vs broad integration tests: [Order Service](https://github.com/arturomorarioja/py_order_service)
  - API Testing: [Library API v3](https://github.com/arturomorarioja/py_library_api_v3) Postman tests
    - [Collection](https://github.com/arturomorarioja/py_library_api_v3/blob/main/postman/Library%20API%20v3.postman_collection.json)
    - [Environment](https://github.com/arturomorarioja/py_library_api_v3/blob/main/postman/Library%20API%20v3.postman_environment.json)
  - Continuous Testing
    - Running unit tests in the pipeline: [Python](https://github.com/arturomorarioja/py_length_converter_unit_tests) | [JavaScript](https://github.com/arturomorarioja/js_vat) | [PHP8](https://github.com/arturomorarioja/php_printer_cartridges_unit_tests)
    - Running two dependent jobs (one for the unit tests, another one for static code analysis with SonarQube): [Employee](https://github.com/arturomorarioja/py_employee_unit_tests)
    - Running the API tests in the pipeline (Postman and Newman): [Customers](https://github.com/arturomorarioja/customers_api)

## In-class exercise
- API Tests: [Customers](https://github.com/arturomorarioja-ek/SD_Software_Quality_E2026/blob/main/Lesson05/Ex%2001%20Customers%20API.md)

## Homework
- Catch up on previous homework, specifically [static code analysis](https://github.com/arturomorarioja-ek/SD_Software_Quality_E2026/blob/main/Lesson04/Ex%2002%20Static%20Code%20Analysis.md)
- Finish the Customers API testing exercise
- Practice API testing in existing APIs of yours:
  - Create collections to group requests to the same API and environments to define variables
  - Write tests under "Scripts". You can use snippets and the built-in AI tool
  - Remember to write positive and negative tests
  - Sort your tests so that you can run them in a row
- Solve the [Measure Converter](https://github.com/arturomorarioja-ek/SD_Software_Quality_E2026/blob/main/Lesson05/Ex%2002%20Measure%20Converter.md) integration testing exercise
