# 1. Create table
```SQL
CREATE TABLE emp (
    empno NUMBER,
    empname VARCHAR2(255), 
    DOB DATE,
    salary NUMBER, 
    designation VARCHAR2(20)
);
```

# 2. Insert values
```SQL
INSERT INTO emp VALUES(100,'John','4.21.1994', 50000,'Manager');
```
```SQL
INSERT INTO emp VALUES(101,'Greg','6.20.1994',25000,'Clerk');
```

# 3. Display values
```SQL
SELECT * FROM emp;
```
```SQL
SELECT empname,salary FROM emp;
```