### Coverage calculation - Solutions

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

**Solution**

1. Test cases 100% statement coverage

    ```
    #1. Values: q = 3, r = 25, s = 10 (all ifs)

    #2. Values: q = 8, r = 25, s = 10 (first else, then all ifs)
    ```

2. Test cases 100% decision coverage

    ```
    #1. Values: q = 3, r = 25, s = 10 (all ifs)

    #2. Values: q = 8, r = 20, s = 10 (first and second elses)

    #3. Values: q = 8, r = 25, s = 15 (else – if - else)
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

**Solution**

1. Test cases 100% statement coverage

    ```
    #1. Values: StudentScore = 85
    
    #2. Values: StudentScore = 65
    
    #3. Values: StudentScore = 45
    
    #4. Values: StudentScore = 35
    ```

2. Test cases 100% decision coverage

    Same as statement coverage, because every if has an else.

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

**Solution**

1. Test cases 100% statement coverage

    ```
    #1. Values: Balance = 5000

    #2. Values: Balance = 15000
    ```

2. Test cases 100% decision coverage

    ```
    #1. Values: Balance = 500

    #2. Values: Balance = 5000

    #3. Values: Balance = 15000
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

**Solution**

1. Test cases 100% statement coverage

    ```
    #1. Values: nNumber = 0
    
    #2. Values: nNumber = 4, nOption = 1, nNumber = 5, nOption = 1, nNumber = 5, nOption = 2, nNumber = 4, nOption = 2, nNumber = 4, nOption = 0
    ```

2. Test cases 100% decision coverage

    Same as statement coverage, but test case #2 needs another value for the only if without an else (`if(nOption = 2)`):

    ```
    #3. Values: nNumber = 4, nOption = 1, nNumber = 5, nOption = 1, nNumber = 5, nOption = 2, nNumber = 4, nOption = 2, nNumber = 4, nOption = 3, nOption = 0
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

**Solution**

1. Test cases 100% statement coverage

    ```
    #1. Values: CountryCode = DK, country code in file's first line = DK
    
    #2. Values: broken file
    ```
    
2. Test cases 100% decision coverage

    ```
    #1. Values: CountryCode = DK, country code in file's first line = DK, country code in file's second line = SE (to execute the else of the inner if)
    
    #2. Values: broken file
    ```

Exercises based on Brian Hambling’s *Software Testing: An ISTQB-BCS Certified Tester Foundation Guide*, 4th ed. (2019)
