### Order Pricing Service

**Part I**

Implement an order pricing service using the programming language of your choice and according to the following requirements:
- The `OrderPricingService` is part of the checkout process of an e-commerce platform
- The service depends on two external collaborators that are not yet implemented:
  - `DiscountService.getDiscount(subtotal)` provides a discount for an order
  - `ShippingService.getShippingCosts(countryCode, subtotal)` provides shipping costs
    - `countryCode` uses ISO-3166 alpha-2 (e.g., `DK`, `SE`, `NO`)
- The service must implement the method `calculateTotal(countryCode, subtotal)` according to the following business rule:
  - `finalTotal = subtotal - discount + shippingCosts`
- All monetary values are in Danish kroner

**Part II**

Design and write unit tests for `OrderPricingService.calculateTotal()` so that both collaborators are mocked.
