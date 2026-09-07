### Unit Testing: Classical vs. London Approaches
The SUT is a booking system for a movie theatre.

Two business scenarios need testing:
1. A booking succeeds
2. A booking fails because there are not enough seats

Implement the corresponding unit tests in two ways:
1. Following the Classical Approach to Unit Testing
2. Following the London Approach to Unit Testing

Use the programming language of your choice (Java, C#, Python, JavaScript, or PHP). Find the corresponding SUT implementations below:

### System Under Test

#### Java
```Java
public class BookingService
{
    public boolean book(Screening screening, int numberOfSeats)
    {
        if (!screening.hasAvailableSeats(numberOfSeats))
        {
            return false;
        }

        double price = calculatePrice(screening.getTicketPrice(), numberOfSeats);

        screening.reserveSeats(numberOfSeats);

        return price > 0;
    }

    private double calculatePrice(double ticketPrice, int numberOfSeats)
    {
        return ticketPrice * numberOfSeats;
    }
}
```

```Java
public class Screening
{
    private int availableSeats;
    private final double ticketPrice;

    public Screening(int availableSeats, double ticketPrice)
    {
        this.availableSeats = availableSeats;
        this.ticketPrice = ticketPrice;
    }

    public boolean hasAvailableSeats(int numberOfSeats)
    {
        return availableSeats >= numberOfSeats;
    }

    public void reserveSeats(int numberOfSeats)
    {
        availableSeats -= numberOfSeats;
    }

    public int getAvailableSeats()
    {
        return availableSeats;
    }

    public double getTicketPrice()
    {
        return ticketPrice;
    }
}
```

#### C#

```C#
public class BookingService
{
    public bool Book(Screening screening, int numberOfSeats)
    {
        if (!screening.HasAvailableSeats(numberOfSeats))
        {
            return false;
        }

        double price = CalculatePrice(screening.GetTicketPrice(), numberOfSeats);

        screening.ReserveSeats(numberOfSeats);

        return price > 0;
    }

    private double CalculatePrice(double ticketPrice, int numberOfSeats)
    {
        return ticketPrice * numberOfSeats;
    }
}
```

```C#
public class Screening
{
    private int availableSeats;
    private readonly double ticketPrice;

    public Screening(int availableSeats, double ticketPrice)
    {
        this.availableSeats = availableSeats;
        this.ticketPrice = ticketPrice;
    }

    public bool HasAvailableSeats(int numberOfSeats)
    {
        return availableSeats >= numberOfSeats;
    }

    public void ReserveSeats(int numberOfSeats)
    {
        availableSeats -= numberOfSeats;
    }

    public int GetAvailableSeats()
    {
        return availableSeats;
    }

    public double GetTicketPrice()
    {
        return ticketPrice;
    }
}
```

#### Python

```Python
class BookingService:
    def book(self, screening, number_of_seats):
        if not screening.has_available_seats(number_of_seats):
            return False

        price = self._calculate_price(screening.get_ticket_price(), number_of_seats)

        screening.reserve_seats(number_of_seats)

        return price > 0

    def _calculate_price(self, ticket_price, number_of_seats):
        return ticket_price * number_of_seats
```

```Python
class Screening:
    def __init__(self, available_seats, ticket_price):
        self._available_seats = available_seats
        self._ticket_price = ticket_price

    def has_available_seats(self, number_of_seats):
        return self._available_seats >= number_of_seats

    def reserve_seats(self, number_of_seats):
        self._available_seats -= number_of_seats

    def get_available_seats(self):
        return self._available_seats

    def get_ticket_price(self):
        return self._ticket_price
```

#### JavaScript

```JavaScript
export class BookingService
{
    book(screening, numberOfSeats)
    {
        if (!screening.hasAvailableSeats(numberOfSeats))
        {
            return false;
        }

        const price = this.#calculatePrice(screening.getTicketPrice(), numberOfSeats);

        screening.reserveSeats(numberOfSeats);

        return price > 0;
    }

    #calculatePrice(ticketPrice, numberOfSeats)
    {
        return ticketPrice * numberOfSeats;
    }
}
```

```JavaScript
export class Screening
{
    #availableSeats;
    #ticketPrice;

    constructor(availableSeats, ticketPrice)
    {
        this.#availableSeats = availableSeats;
        this.#ticketPrice = ticketPrice;
    }

    hasAvailableSeats(numberOfSeats)
    {
        return this.#availableSeats >= numberOfSeats;
    }

    reserveSeats(numberOfSeats)
    {
        this.#availableSeats -= numberOfSeats;
    }

    getAvailableSeats()
    {
        return this.#availableSeats;
    }

    getTicketPrice()
    {
        return this.#ticketPrice;
    }
}
```

#### PHP

```php
<?php

class BookingService
{
    public function book(Screening $screening, int $numberOfSeats): bool
    {
        if (!$screening->hasAvailableSeats($numberOfSeats))
        {
            return false;
        }

        $price = $this->calculatePrice($screening->getTicketPrice(), $numberOfSeats);

        $screening->reserveSeats($numberOfSeats);

        return $price > 0;
    }

    private function calculatePrice(
        float $ticketPrice,
        int $numberOfSeats
    ): float
    {
        return $ticketPrice * $numberOfSeats;
    }
}
```

```php
<?php

class Screening
{
    private int $availableSeats;
    private float $ticketPrice;

    public function __construct(int $availableSeats, float $ticketPrice)
    {
        $this->availableSeats = $availableSeats;
        $this->ticketPrice = $ticketPrice;
    }

    public function hasAvailableSeats(int $numberOfSeats): bool
    {
        return $this->availableSeats >= $numberOfSeats;
    }

    public function reserveSeats(int $numberOfSeats): void
    {
        $this->availableSeats -= $numberOfSeats;
    }

    public function getAvailableSeats(): int
    {
        return $this->availableSeats;
    }

    public function getTicketPrice(): float
    {
        return $this->ticketPrice;
    }
}
```
