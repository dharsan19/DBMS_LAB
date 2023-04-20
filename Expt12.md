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
## 1) Write a pl/sql function recursive code for finding factorial of a number.
```sql
CREATE OR REPLACE FUNCTION factorial(n IN NUMBER) RETURN NUMBER
IS
BEGIN
  -- base case
  IF n = 0 OR n = 1 THEN
    RETURN 1;
  ELSE
    -- recursive case
    RETURN n * factorial(n - 1);
  END IF;
END;
/
```
```sql
DECLARE
  n NUMBER := 5;
  fact NUMBER;
BEGIN
  fact := factorial(n);
  DBMS_OUTPUT.PUT_LINE('Factorial of ' || n || ' is ' || fact);
END;
/
```

## 2) Write a pl/sql function for finding a number is a prime number.
```sql
CREATE OR REPLACE FUNCTION is_prime(n IN NUMBER) RETURN BOOLEAN
IS
  divisor NUMBER := 2;
BEGIN
  IF n <= 1 THEN
    RETURN FALSE;
  END IF;

  WHILE divisor <= SQRT(n) LOOP
    IF MOD(n, divisor) = 0 THEN
      RETURN FALSE;
    END IF;
    divisor := divisor + 1;
  END LOOP;

  RETURN TRUE;
END;
/
```
```sql
DECLARE
  n NUMBER := 17;
BEGIN
  IF is_prime(n) THEN
    DBMS_OUTPUT.PUT_LINE(n || ' is a prime number.');
  ELSE
    DBMS_OUTPUT.PUT_LINE(n || ' is not a prime number.');
  END IF;
END;
/
```
## Student Table Creation for 3rd Question
``` sql
CREATE TABLE Student (
  Sno NUMBER,
  sname VARCHAR2(50),
  dept VARCHAR2(50),
  cgpa NUMBER
);
```
## Values
```sql
INSERT INTO Student (Sno, sname, dept, cgpa)
VALUES (1, 'John', 'CSE', 8.5);

INSERT INTO Student (Sno, sname, dept, cgpa)
VALUES (2, 'Jane', 'CSE', 9.0);

INSERT INTO Student (Sno, sname, dept, cgpa)
VALUES (3, 'Mike', 'CSE', 7.5);
```
## 3) Write a pl/sql function to retrieve the count of students from ‘CSE’ department from the table Student (Sno, sname, dept, cgpa).
```sql
CREATE OR REPLACE FUNCTION get_cse_student_count RETURN NUMBER
IS
  cse_count NUMBER;
BEGIN
  SELECT COUNT(*) INTO cse_count FROM Student WHERE dept = 'CSE';
  RETURN cse_count;
END;
/
```
```sql
DECLARE
  cse_count NUMBER;
BEGIN
  cse_count := get_cse_student_count;
  DBMS_OUTPUT.PUT_LINE('Number of students in CSE department: ' || cse_count);
END;
/
```

## 4) Write a pl/sql function to retrieve the maximum CGPA of the student  from the table Student (Sno, sname, dept, cgpa).
```sql
CREATE OR REPLACE FUNCTION get_max_cgpa RETURN NUMBER
IS
  max_cgpa NUMBER;
BEGIN
  SELECT MAX(cgpa) INTO max_cgpa FROM Student;
  RETURN max_cgpa;
END;
/
```
```sql
DECLARE
  max_cgpa NUMBER;
BEGIN
  max_cgpa := get_max_cgpa;
  DBMS_OUTPUT.PUT_LINE('Maximum CGPA: ' || max_cgpa);
END;
/
```

## 5) Write a simple PL/SQL Function that computes and returns the average of two numbers.
```sql
CREATE OR REPLACE FUNCTION average_of_two_numbers (
    num1 NUMBER,
    num2 NUMBER
) RETURN NUMBER IS
    avg_num NUMBER;
BEGIN
    avg_num := (num1 + num2) / 2;
    RETURN avg_num;
END;
/
```
```sql
SELECT average_of_two_numbers(10, 20) FROM dual;
```
