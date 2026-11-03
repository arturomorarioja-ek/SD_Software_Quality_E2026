### Software Requirements Specification
Review the following software requirements specification:

|SRS|
|-|
|The application will consist of a data entry window and a data display window, which will obtain data from the former. It will include a printing option to print the information to a printer, pdf file, etc.<br><br>The data entry window will require the user to input the following customer information: first name, surname, address, city, postal code, phone number, date of birth, and preferred display colour (red, yellow, violet…). If the latter shows that the customer is under 18 years old, the text “Under-aged” will be displayed, showing the text “Adult” if the customer is over 18 years old.<br><br>Once the “Ok” button is clicked, the data display window will show all the information.|

---
**Potential problems found**

|Issues|
|-|
|The application **[what is its name?]** will consist of a data entry window and a data display window, which will obtain data from the former **[“the former”: difficult to read. It could even refer to the application itself]**. It **[who? The application, the data entry window or the data display window?]** will include a printing option to print the information **[which information?]** to a printer, pdf file, etc. **[etc? Does this include/exclude json, xml, Excel, Powerpoint…? AVOID OPEN LISTS!]**<br><br>The data entry window will require the user to input the following customer information: first name, surname, address, city **[from a list of cities, or will the user type the city’s full name (in which case s/he might type Copenhagen or København, or even misspell)?]**, postal code **[which format?]**, phone number **[are international phone numbers allowed?]**, date of birth, and preferred display colour (red, yellow, violet…) **[open list! Are burgundy, light green, and indigo included?]**. If the latter **[Error: the date of birth is not the latter in the list]** shows that the customer is under 18 years old, the text “Under-aged” will be displayed [where? When? How (on the window **[which one?]** or via an alert?)?], showing the text “Adult” if the customer is over 18 years old **[what if the customer is exactly 18 years old?]**.<br><br>Once the “Ok” button is clicked **[does this mean immediately after it is clicked, or later?]**, the data display window will show all the information **[in which format?]**.|

---
**Review document**

- Date: **[TBD]**
- Review meeting time: **[TBD]**
- Author: **[TBD]**
- Moderator: **[TBD]**
- Reviewers: **[TBD]**
- Scribe: **[TBD]**

<img width="869" height="437" alt="image" src="https://github.com/user-attachments/assets/dd9b9f5d-a5e3-406c-a282-c490c25aa322" />

Legend:
- A: To be solved by the author
- U: Updated based on further analysis

Further improvements (especially for bigger tables):
- Sort issues based on priority
- Categorise issues (e.g., syntax, functionality, non-functional requirement, missing, etc.)
- Divide the table into several table (priority-based, category-based, localtion-based, etc.)

---
**Potential improvement to the SRS**

1. System definition
   
The application is called “Customer Information System” (henceforth CIS).

2. System structure

CIS will consist of:
- a data entry window
- a data display window<br><br>The data display window will obtain data from the data entry window. The data display window will include a printing option to print the information to a printer, or to the following file formats:
  - pdf file
  - json
  - csv

3. User interface

The data entry window will require the user to input the customer information according to the following template (“Template 1”):
- First name. Max. 40 characters. Only Danish alphabetic characters and dash allowed
- Surname. Max. 60 characters. Only Danish alphabetic characters and dash allowed
- Address. Max. 120 characters. Only Danish alphabetic characters, numbers, dot (“.”), comma (“,”), and dash (“-”) allowed
- City. From the list of cities in annex I
- Postal code. Danish format: 3 or 4 numeric digits
- Phone number. Danish phone number format: 8 numeric digits
- Date of birth. Danish date format: “dd/MM/yyyy”
- Preferred display colour **[TBD]**.

All the fields are mandatory except “Phone number”.

The default display colour will be “White”.

There will be an “Ok” button and a “Cancel” button in the data entry window’s bottom right position.
- When clicking the “Cancel” button, the data entry window (and, thus, CIS) will be closed.
- When clicking the “Ok” button, the data display window will appear and show the customer information formatted according to Template 1. Besides, a new row will be displayed below to show the customer’s age status based on the customer’s date of birth and according to the following formula:
  - Customer’s age < 18 years → display “Under-aged”
  - Otherwise → display “Adult”

The data display window will include a “Close” button in the data display’s bottom right position. When clicking the “Close” button, the data display window will be closed.
