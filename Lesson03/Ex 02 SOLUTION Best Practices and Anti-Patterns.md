### Unit Testing Best Practices and Anti-patterns

### Solution

## 1 Avoid branching inside tests
SUT
```Java
public class NumberClassifier
{
    public String classify(int number)
    {
        return number >= 0 ? "positive" : "negative";
    }
}
```
Test A - **GOOD**
```Java
@ParameterizedTest
@CsvSource({ "5, positive", "-5, negative" })
void classifiesNumbers(int number, String expected)
{
    NumberClassifier classifier = new NumberClassifier();

    String result = classifier.classify(number);

    assertEquals(expected, result);
}
```
Test B - **BAD**  
There should be no branching (e.g., if, while, for) in a unit test.
```Java
@Test
void classifiesNumbers()
{
    NumberClassifier classifier = new NumberClassifier();
    int[] numbers = {5, -5};

    for (int number : numbers)
    {
        String result = classifier.classify(number);

        if (number >= 0)
        {
            assertEquals("positive", result);
        }
        else
        {
            assertEquals("negative", result);
        }
    }
}
```

## 2 Never test private methods directly
SUT
```Java
public class Invoice
{
    public double total(double price, int quantity)
    {
        return calculateSubtotal(price, quantity);
    }

    private double calculateSubtotal(double price, int quantity)
    {
        return price * quantity;
    }
}
```
Test A - **GOOD**
```Java
@Test
void calculatesInvoiceTotal()
{
    Invoice invoice = new Invoice();

    double result = invoice.total(25, 4);

    assertEquals(100, result);
}
```
Test B - **BAD**  
Private methods must be tested through the public methods that call them.
```Java
@Test
void calculatesSubtotal() throws Exception
{
    Invoice invoice = new Invoice();

    Method method = Invoice.class.getDeclaredMethod(
        "calculateSubtotal",
        double.class,
        int.class
    );
    method.setAccessible(true);

    double result = (double) method.invoke(invoice, 25, 4);

    assertEquals(100, result);
}
```

## 3 Do not leak domain knowledge into tests
SUT
```Java
public class VatCalculator
{
    private static final double VAT_RATE = 0.25;

    public double addVat(double netPrice)
    {
        return netPrice * (1 + VAT_RATE);
    }
}
```
Test A - **BAD**  
The test is reproducing an SUT calculation. If the calculation is wrong in the SUT, it will also be wrong in the test.
```Java
@Test
void addsVatToPrice()
{
    VatCalculator calculator = new VatCalculator();

    double result = calculator.addVat(100);

    assertEquals(100 * (1 + 0.25), result);
}
```
Test B - **GOOD**
```Java
@Test
void addsVatToPrice()
{
    VatCalculator calculator = new VatCalculator();

    double result = calculator.addVat(100);

    assertEquals(125, result);
}
```

## 4 Avoid regular expressions in unit tests
SUT
```Java
public class UsernameValidator
{
    public boolean isValid(String username)
    {
        return username != null
            && username.matches("[A-Za-z][A-Za-z0-9]{2,11}");
    }
}
```
Test A - **GOOD**
```Java
@ParameterizedTest
@CsvSource({
    "Alice123, true",
    "Bob, true",
    "1Alice, false",
    "Al, false",
    "Alice-123, false"
})
void validatesUsernames(String username, boolean expected)
{
    UsernameValidator validator = new UsernameValidator();

    boolean result = validator.isValid(username);

    assertEquals(expected, result);
}
```
Test B - **BAD**  
Error in the SUT regEx will also occur in the test.
```Java
@Test
void validatesUsername()
{
    UsernameValidator validator = new UsernameValidator();
    String username = "Alice123";

    boolean result = validator.isValid(username);

    assertEquals(
        username.matches("[A-Za-z][A-Za-z0-9]{2,11}"),
        result
    );
}
```

## 5 Avoid chaining Arrange, Act, and Assert
SUT
```Java
public class ShoppingCart
{
    private double total;

    public void add(double price)
    {
        total += price;
    }

    public double getTotal()
    {
        return total;
    }

    public double applyDiscount(double percentage)
    {
        total *= 1 - percentage;

        return total;
    }
}
```
Test A - **BAD**  
The second Act section expects the result of the first. This test should be two independent tests. 
```Java
@Test
void appliesDiscountToCartTotal()
{
    ShoppingCart cart = new ShoppingCart();
    cart.add(60);
    cart.add(40);

    double total = cart.getTotal();

    assertEquals(100, total);

    double result = cart.applyDiscount(0.20);

    assertEquals(80, result);
}
```
Test B - **GOOD**
```Java
@Test
void appliesDiscountToCartTotal()
{
    ShoppingCart cart = new ShoppingCart();
    cart.add(60);
    cart.add(40);

    double result = cart.applyDiscount(0.20);

    assertEquals(80, result);
}
```

## 6 Test case design must be comprehensive
SUT
```Java
public class AgeValidator
{
    public boolean canRegister(int age)
    {
        return age >= 18 && age <= 120;
    }
}
```
Test A - **GOOD**
```Java
@ParameterizedTest
@CsvSource({
    "18, true",
    "30, true",
    "120, true",
    "17, false",
    "121, false",
    "-1, false"
})
void validatesRegistrationAge(int age, boolean expected)
{
    AgeValidator validator = new AgeValidator();

    boolean result = validator.canRegister(age);

    assertEquals(expected, result);
}
```
Test B - **BAD**  
No negative tests, boundary values, or edge cases.
```Java
@Test
void adultCanRegister()
{
    AgeValidator validator = new AgeValidator();

    boolean result = validator.canRegister(30);

    assertTrue(result);
}
```

## 7 The Act section must contain only one line of code
Test A - **BAD**  
The need for two lines of code in the Act section indicates that the SUT has structural issues. `service.checkout()` and `service.completeOrder()` should not work independently.
```Java
@Test
void checkoutSucceedsWhenPaymentIsAccepted()
{
    Order order = new Order(100);
    PaymentCard card = new PaymentCard(500);
    CheckoutService service = new CheckoutService();

    boolean paymentSucceeded = service.checkout(order, card);
    boolean orderCompleted = service.completeOrder(order);

    assertTrue(paymentSucceeded);
    assertTrue(orderCompleted);
}
```
Test B - **GOOD**
```Java
@Test
void checkoutSucceedsWhenPaymentIsAccepted()
{
    Order order = new Order(100);
    PaymentCard card = new PaymentCard(500);
    CheckoutService service = new CheckoutService();

    boolean success = service.checkout(order, card);

    assertTrue(success);
}
```

## 8 Do not expose private class state
SUT
```Java
public class StatementGenerator
{
    private DateFormatter formatter = new InternationalDateFormatter();

    public void useDanishLocale()
    {
        formatter = new DanishDateFormatter();
    }

    public String generate(LocalDate date)
    {
        return "Statement date: " + formatter.format(date);
    }

    public DateFormatter getFormatter()
    {
        return formatter;
    }
}
```
Test A - **GOOD**
```Java
@Test
void generatesStatementWithDanishDate()
{
    StatementGenerator generator = new StatementGenerator();
    generator.useDanishLocale();

    String result = generator.generate(
        LocalDate.of(2026, 9, 7)
    );

    assertEquals("Statement date: 07-09-2026", result);
}
```
Test B - **BAD**  
Asserting for an object inside the SUT couples the tests to the code, thus making them not resistant to refactoring.
```Java
@Test
void usesDanishFormatterForDanishLocale()
{
    StatementGenerator generator = new StatementGenerator();

    generator.useDanishLocale();

    assertInstanceOf(
        DanishDateFormatter.class,
        generator.getFormatter()
    );
}
```

## 9 Avoid code pollution

**Scenario A** - **BAD**  
The SUT is deciding whether to run the actual service or not based on whether it is being called by a test or by a real system process.

SUT
```Java
public class ReceiptService
{
    private final EmailService emailService;
    private final boolean testing;

    public ReceiptService(EmailService emailService, boolean testing)
    {
        this.emailService = emailService;
        this.testing = testing;
    }

    public void sendReceipt(String email, String receipt)
    {
        if (testing)
        {
            return;
        }
        emailService.send(email, receipt);
    }
}
```
Test
```Java
@Test
void sendsReceipt()
{
    EmailService emailService = new SmtpEmailService();
    ReceiptService service = new ReceiptService(emailService, true);

    assertDoesNotThrow(() ->
        service.sendReceipt(
            "customer@example.com",
            "Receipt #123"
        )
    );
}
```
**Scenario B** - **GOOD**  
Mocking should take place in the tests, not in the SUT.

SUT
```Java
public class ReceiptService
{
    private final EmailService emailService;

    public ReceiptService(EmailService emailService)
    {
        this.emailService = emailService;
    }

    public void sendReceipt(String email, String receipt)
    {
        emailService.send(email, receipt);
    }
}
```
Test
```Java
@Test
void sendsReceipt()
{
    EmailService emailService = mock(EmailService.class);
    ReceiptService service = new ReceiptService(emailService);

    service.sendReceipt("customer@example.com", "Receipt #123");

    verify(emailService).send("customer@example.com", "Receipt #123");
}
```
