```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```

# PL/SQL Conditional and Iterative Statements

## 1. Get FARENHEIT and convert into CELSIUS

``` sql
DECLARE
   fahrenheit NUMBER;
   celsius NUMBER;
BEGIN
   DBMS_OUTPUT.PUT('Enter temperature in Fahrenheit: ');
   fahrenheit := &fahrenheit;
   
   celsius := (fahrenheit - 32) * 5/9;
   
   DBMS_OUTPUT.PUT_LINE('Temperature in Celsius: ' || celsius);
END;
```

## 2. Write a pl/sql program to find SUM OF EVEN INTEGERS

``` sql
DECLARE
   sum NUMBER := 0;
BEGIN
   FOR i IN 1..10 LOOP
      IF i MOD 2 = 0 THEN
         sum := sum + i;
      END IF;
   END LOOP;
   
   DBMS_OUTPUT.PUT_LINE('Sum of even integers from 1 to 10: ' || sum);
END;
```

## 3. Write a pl/sql program to find GREATEST OF THREE NUMBERS USING IF ELSEIF

``` sql
DECLARE
   a NUMBER := &a;
   b NUMBER := &b;
   c NUMBER := &c;
   max NUMBER;
BEGIN
   max := a;
   
   IF b > max THEN
      max := b;
   END IF;
   
   IF c > max THEN
      max := c;
   END IF;
   
   DBMS_OUTPUT.PUT_LINE('The greatest of ' || a || ', ' || b || ', and ' || c || ' is ' || max);
END;
 ```
 
 ## 4. Write a pl/sql program to find a number is ODD OR EVEN
 
 ``` sql
 DECLARE
   num NUMBER;
BEGIN
   num := &num;
   
   IF num MOD 2 = 0 THEN
      DBMS_OUTPUT.PUT_LINE(num || ' is even');
   ELSE
      DBMS_OUTPUT.PUT_LINE(num || ' is odd');
   END IF;
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
