### Coverage calculation

#### Algorithm
Define a minimum set of test cases for the following pseudocode to reach
1. 100% statement coverage
2. 100% decision coverage

```
IF q <= 5 THEN
    x = 100
ELSE
    x = 50
ENDIF

IF r >= 22 THEN
    x = 500
    IF s < 13 THEN
        x = 200
    ENDIF
ENDIF
```

#### Grading
Define a minimum set of test cases for the following pseudocode to reach
1. 100% statement coverage
2. 100% decision coverage

```
Program Grading
    StudentScore: integer
    Result: string
Begin
    Read StudentScore
    If StudentScore > 79
    Then Result = "Distinction"
    Else
        If StudentScore > 59
        Then Result = "Merit"
        Else
            If StudentScore > 39
            Then Result = "Pass"
            Else Result = "Fail"
            Endif
       Endif
    Endif
    Print ("Your result is", Result)
End
```

#### Interest
Define a minimum set of test cases for the following pseudocode to reach
1. 100% statement coverage
2. 100% decision coverage

```
 1 Program BestInterest
 2 Interest, BaseRate, Balance: Real
 3
 4 Begin
 5 BaseRate = 0.035
 6 Interest = BaseRate
 7
 8 Read (Balance)
 9 If Balance > 1000
10 Then
11     Interest = Interest + 0.005
12     If Balance < 10000
13     Then
14            Interest = Interest + 0.005
15     Else
16            Interest = Interest + 0.01
17     Endif
18 Endif
19
20 Balance = Balance × (1 + Interest)
21
22 End
```

#### Number
Define a minimum set of test cases for the following pseudocode to reach
1. 100% statement coverage
2. 100% decision coverage

```
lContinue = true;

while(lContinue)
  Write "Enter number: ";
  Read nNumber;
  
  if(nNumber = 0) 
    lContinue = false;
  else 
    Write "Choose an option: ";
    Write "0. Quit";
    Write "1. Check if even or odd";
    Write "2. Check if prime";
    Read nOption;

    if(nOption = 0)
      lContinue = false;
    else
      if(nOption = 1)
        if(nNumber MOD 2 = 0)
          Write "Even";
        else
          Write "Odd";
      else
        if(nOption = 2)
          if(IsPrime(nNumber))
            Write "Prime";
          else
            Write "Not prime";
Write "Goodbye";
```

#### Employees

Define a minimum set of test cases for the following pseudocode to reach
1. 100% statement coverage
2. 100% decision coverage

```
NumEmployees = 0

Write "Insert country code"
Read CountryCode

Open employees file
If not error
    While not eof
        Read file line
        If employee's country code = CountryCode
            Write "Name: " + employee's name
            NumEmployees++
        Endif
    Endwhile
    Close employees file
    Write "Total employees: " + NumEmployees
Else
    Write "Error opening the file"
Endif
```

Exercises based on Brian Hambling’s *Software Testing: An ISTQB-BCS Certified Tester Foundation Guide*, 4th ed. (2019)
