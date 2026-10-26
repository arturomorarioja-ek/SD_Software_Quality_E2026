Design and document an acceptance test based on the following Software Requirements Specification:

---

## Library Book Reservation System

### System Description

A library provides a web application that allows users to reserve books online.

Users must be logged in to perform reservations.

The system contains a catalogue of books with the following information:
- Title
- Author
- Publication year
- Availability status (Available / Not available)

### Functional Requirements

**FR1 — Search Books**

Users must be able to search the catalogue by:
- Title
- Author

The system displays a list of matching books including:
- Title
- Author
- Year
- Availability status

If no books match the query, the system displays the message `No books found`.

**FR2 — View Book Details**

When clicking on a book from the search results, the user sees the Book Details page showing:
- Title
- Author
- Publication year
- Availability
- Description

**FR3 — Reserve a Book**

If the book is Available, the user can click `Reserve`.

After clicking Reserve:
1. The reservation is confirmed
2. The book status changes to `Reserved`
3. A confirmation message appears: `Book reserved successfully`.

**FR4 — Reservation Restrictions**

A user cannot reserve a book if:
- The book is already reserved
- The user already has 3 active reservations

In these cases the system shows an error message.

**FR5 — View My Reservations**

Users can open My Reservations and see a list containing:
- Book title
- Reservation date
- Status

Users may cancel a reservation.

After cancellation, the book becomes Available again.

---

Work in groups of 4 or 5 students.

Create requirements-based test checks for:
- Searching books
- Viewing book details
- Reserving books
- Reservation restrictions
- Managing reservations

Think about a useful method to document the test
- Although acceptance tests are usually documented in tools like Jira or TestMonitor, use a simpler format like a spreadsheet. Get inspiration from the [Acceptance Test checklist](https://github.com/arturomorarioja-ek/SD_Software_Quality_F2026/blob/main/Lesson08/Acceptance%20Test%20checklist.xlsx), but try to come with your own format
- Remember that it is users, not technical personnel, who will fill the document. Structure it in a clear, easy-to-follow way
