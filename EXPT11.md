```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```

# PL/SQL Functions
# ** Execute this command in sqlplus 1st **
## TO display output in the screen – give the below command initially 
```sql
set serveroutput on;
```

## 1) creates a simple procedure that displays the string Hello World!; on the screen when executed
```sql
CREATE OR REPLACE PROCEDURE display_hello_world IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Hello World!');
END;
/
```
```sql
EXECUTE display_hello_world;
```
## 2) Create a procedure to find the minimum of two values. HINT - Procedure takes two numbers using the IN mode and returns their minimum using the OUT parameters
```sql
CREATE OR REPLACE PROCEDURE find_minimum (
    num1 IN NUMBER,
    num2 IN NUMBER,
    min_num OUT NUMBER
) IS
BEGIN
    IF num1 < num2 THEN
        min_num := num1;
    ELSE
        min_num := num2;
    END IF;
END;
/
```
```sql
DECLARE
    num1 NUMBER := 10;
    num2 NUMBER := 5;
    min_num NUMBER;
BEGIN
    find_minimum(num1, num2, min_num);
    DBMS_OUTPUT.PUT_LINE('The minimum of ' || num1 || ' and ' || num2 || ' is ' || min_num);
END;
/
```

## 3) Create a procedure, to get cube of passed number.
```sql
CREATE OR REPLACE PROCEDURE get_cube (
    num IN NUMBER,
    cube_num OUT NUMBER
) IS
BEGIN
    cube_num := num * num * num;
END;
/
```
```sql
DECLARE
    num NUMBER := 5;
    cube NUMBER;
BEGIN
    get_cube(num, cube);
    DBMS_OUTPUT.PUT_LINE('The cube of ' || num || ' is ' || cube);
END;
/
```

## 4) Write a procedure to reverse a input string and check it is palindrome or not.
```sql
CREATE OR REPLACE PROCEDURE check_palindrome (
    str IN VARCHAR2,
    is_palindrome OUT BOOLEAN
) IS
    rev_str VARCHAR2(32767);
BEGIN
    -- Reverse the input string
    FOR i IN REVERSE 1..LENGTH(str) LOOP
        rev_str := rev_str || SUBSTR(str, i, 1);
    END LOOP;
    
    -- Check if the reversed string is equal to the original string
    IF str = rev_str THEN
        is_palindrome := TRUE;
    ELSE
        is_palindrome := FALSE;
    END IF;
END;
/
```
```sql
DECLARE
    str VARCHAR2(32767) := 'racecar';
    palindrome BOOLEAN;
BEGIN
    check_palindrome(str, palindrome);
    IF palindrome THEN
        DBMS_OUTPUT.PUT_LINE(str || ' is a palindrome');
    ELSE
        DBMS_OUTPUT.PUT_LINE(str || ' is not a palindrome');
    END IF;
END;
/
```

## 5) Write a procedure to delete a specific row from the table already created.
``` sql
CREATE TABLE student4 (
  id NUMBER(10) PRIMARY KEY,
  name VARCHAR2(100) NOT NULL,
  email VARCHAR2(100) UNIQUE,
  phone VARCHAR2(20),
  age NUMBER(3),
  gender VARCHAR2(10),
  address VARCHAR2(200)
);
```

``` sql
INSERT INTO student4 (id, name, email, phone, age, gender, address)
VALUES (101, 'John Smith', 'john.smith@example.com', '555-1234', 25, 'Male', '123 Main St');

INSERT INTO student4 (id, name, email, phone, age, gender, address)
VALUES (202, 'Jane Doe', 'jane.doe@example.com', '555-5678', 22, 'Female', '456 Maple Ave');

INSERT INTO student4 (id, name, email, phone, age, gender, address)
VALUES (303, 'Bob Johnson', 'bob.johnson@example.com', '555-2468', 28, 'Male', '789 Elm St');
```

``` sql
CREATE OR REPLACE PROCEDURE delete_row(
    row_id IN NUMBER
)
IS
BEGIN
  DELETE FROM student4 WHERE id = row_id;
  COMMIT;
END;
/
```

``` sql
DECLARE
  row_id NUMBER := 101;
BEGIN
  delete_row(row_id);
  DBMS_OUTPUT.PUT_LINE('Row with ID ' || row_id || ' deleted.');
END;
/
```
