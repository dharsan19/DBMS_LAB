```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```

# PL/SQL Conditional and Iterative Statements
# ** Execute this command in sqlplus 1st **
## TO display output in the screen – give the below command initially 
```sql
set serveroutput on;
```
## 1. Get FARENHEIT and convert into CELSIUS

``` sql
 DECLARE
        celcius NUMBER;
        fahrenheit NUMBER;
BEGIN
        celcius := &input_celcius;
        fahrenheit := 9/5 * celcius + 32;
        DBMS_OUTPUT.PUT_LINE (celcius ||' Celcius = '||fahrenheit|| ' Fahrenheit');
     END;
```

## 2. Write a pl/sql program to find SUM OF EVEN INTEGERS

``` sql
DECLARE
    num NUMBER(3) := 2;
    sum1 NUMBER(4) := 0;
BEGIN
    WHILE num <= 5 LOOP
        dbms_output.Put_line(num);
        sum1 := sum1 + num;
        num := num + 2;
    END LOOP;
        dbms_output.Put_line('Sum of even numbers is ' || sum1);
END;
```

## 3. Write a pl/sql program to find GREATEST OF THREE NUMBERS USING IF ELSEIF

``` sql
DECLARE
    a NUMBER := 46;
    b NUMBER := 67;
    c NUMBER := 21;
BEGIN
    IF a > b
       AND a > c THEN
      dbms_output.Put_line('Greatest number is '
                           ||a);
    ELSIF b > a
          AND b > c THEN
      dbms_output.Put_line('Greatest number is '
                           ||b);
    ELSE
      dbms_output.Put_line('Greatest number is '
                           ||c);
    END IF;
END;
 ```
 
 ## 4. Write a pl/sql program to find a number is ODD OR EVEN
 
 ``` sql
DECLARE
n1 NUMBER := &num1;
BEGIN
-- test if the number provided by the user is even
IF MOD(n1,2) = 0 THEN
DBMS_OUTPUT.PUT_LINE ('The number. '||n1||
' is even number');
ELSE
DBMS_OUTPUT.PUT_LINE ('The number '||n1||' is odd number.');
END IF;
DBMS_OUTPUT.PUT_LINE ('Done Successfully');
END;
 ```
 
 ## 5. Write a pl/sql program to find a FACTORIAL OF A NUMBER
 
 ``` sql
 DECLARE
   num NUMBER := &num;
   factorial NUMBER := 1;
BEGIN
   FOR i IN 1..num LOOP
      factorial := factorial * i;
   END LOOP;
   
   DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is ' || factorial);
END;
 ```


