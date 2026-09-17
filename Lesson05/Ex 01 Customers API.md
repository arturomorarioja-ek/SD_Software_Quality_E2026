### Customers

Create and automate in Postman the test scripts for the [Customers sample API](https://github.com/arturomorarioja/customers_api) from scratch:

1. Install the Customers sample API and run it on port 8001
2. In Postman, create a new collection
3. Create an environment for said collection with the following variables and values:
    - `BASE_URL: http://localhost:8001`
    - `FIRST_NAME: Selma F.`
    - `LAST_NAME: Lassen`
    - `CUSTOMER_ID: <no initial value>`
    - `SEARCH_TERM: elm`
    - `UPDATED_FIRST_NAME: Rikke G.`
4. Create collection-level scripts for the following tests:
      - All requests return JSON data
      - Response time is always less than 200ms
5. Create the following requests and test scripts in the given order:
      - `POST /customers` without parameters
        - Status code must be 400
        - The response must include the key `"error"` with the value `"Incorrect parameters"`
      - `POST /customers` with correct parameters, including the content of the variable `FIRST_NAME` as `first_name` and `LAST_NAME` as `last_name`
        - Status code must be 201
        - The response must include the key `"customer_id"`, which:
          - Must be a number
          - Must be stored into the variable `CUSTOMER_ID`
      - `GET /customers`
        - Status code must be 200
        - Each item in the response must include the key `"customer_id"`, which must be numeric
        - Each item in the response must include the keys `"first_name"`, `"last_name"`, `"phone_no"`, `"address"`, and `"onboarding_date"`, which must be strings
        - Each `"phone_no"` must be either empty or composed of 8 numeric digits
        - Each `"onboarding_date"` must be composed of 8 numeric digits
      - `GET /customers/{{CUSTOMER_ID}}`
        - Status code must be 200
        - The response must include the key `"customer_id"`, whose value must correspond to that stored in `CUSTOMER_ID`
        - The response must include the keys `"first_name"`, `"last_name"`, `"phone_no"`, `"address"`, and `"onboarding_date"`, which must be strings
        - `"phone_no"` must be either empty or composed of 8 numeric digits
        - `"onboarding_date"` must be composed of 8 numeric digits
      - `GET /customers/s={{SEARCH_TERM}}`
        - Status code must be 200
        - Each item in the response must include the key `"customer_id"`, which must be numeric
        - Each item in the response must include the keys `"first_name"`, `"last_name"`, `"phone_no"`, `"address"`, and `"onboarding_date"`, which must be strings
        - Each `"phone_no"` must be either empty or composed of 8 numeric digits
        - Each `"onboarding_date"` must be composed of 8 numeric digits
        - Each `"first_name"` must include the value in `SEARCH_TERM`
      - `PUT /customers/{{CUSTOMER_ID}}` without parameters
        - Status code must be 400
        - The response must include the key `"error"` with the value `"Incorrect parameters"`
      - `PUT /customers/{{CUSTOMER_ID}}` with parameter first_name and value `UPDATED_FIRST_NAME`
        - Status code must be 200
        - The response must include the key `"message"`, which must be a string
      - `GET /customers/{{CUSTOMER_ID}}`
        - Status code must be 200
        - The response must include the key `"First Name"`, which must correspond to the value of `UPDATED_FIRST_NAME`
      - `DEL /customers/{{CUSTOMER_ID}}`
        - Status code must be 200
        - The response must include the key `"message"`, which must be a string and include the text `"successfully deleted"`
      - `DEL /customers/{{CUSTOMER_ID}}`
        - Status code must be 404
        - The response must include the key `"message"`, which must be a string
      - `GET /customers/{{CUSTOMER_ID}}`
        - Status code must be 404
        - The response must include the key `"message"`, which must be a string
