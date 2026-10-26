### End-to-End Testing Exercises

In both Selenium WebDriver, Cypress and Playwright:
1. Design, code and execute UI automation end-to-end tests for a web application of yours.
2. Automate every page in [Formy](https://formy-project.herokuapp.com/)<br>Warning: `autocomplete` may not work, as it no longer communicates with the Google Maps API.
3. Automate everything at https://the-internet.herokuapp.com/.

### Webshop Exercise

In Selenium WebDriver, Cypress, and Playwright, write a happy path end-to-end test for [the webshop sample](https://github.com/arturomorarioja/js_webshop) that covers the following business path:

1. Click on "Sign up"
2. Insert the e-mail "test@ek.dk", password and repeat password "Testing". Click on "Sign up"
3. Click on the subsequent alert’s Ok button
4. Click on "log in"
5. Insert the e-mail "test@ek.dk" and password "Testing". Click on "Log in"
6. Add to cart one unit of the product "Mens Casual Premium Slim Fit T-Shirts"
7. Scroll down. In the product "SanDisk SSD PLUS 1TB Internal SSD – SATA III 6 Gb/s", increase the quantity to 2 units. Add both units to the cart
8. Click on "Cart"
9. Increase the units of the product "SanDisk SSD PLUS 1TB Internal SSD – SATA III 6 Gb/s" to 3
10. Click on "Check out"
11. Introduce the address "Guldbergsgade 29N", postal code "2200", city "Copenhagen", in Billing address check "Same as delivery address", in Credit card introduce the name "Pernille L. Hansen", expiration "December 2027", CVV "666". Click on "Place Purchase"
12. Click on "Cart". Confirm that it is empty. Leave the modal
13. Log out. Confirm that the option "Log in" is on the page

**NOTE**: JSON server must be started with `--host 127.0.0.1`. Otherwise Cypress will have trouble opening same-server services from different ports.
