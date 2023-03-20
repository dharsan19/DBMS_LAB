```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```
# DCL
## Q1 Give grant permission to your neighbor for any one of your tables. Tell him/her to access (modify the data) your table from their login.
```SQL
GRANT SELECT, INSERT, UPDATE ON DEPT TO RA2011003010737;
```

## Q2 Check the table again from your login. Observe the inference.
```
DESC DEPT;
```

## Q3 Revoke the permission and tell them to try for accessing your table.
```
REVOKE SELECT, INSERT, UPDATE ON DEPT FROM RA2011003010737;
```

# TCL
## Q1 Create the department table add the details and commit the data.

```sql
CREATE TABLE DEPT1 (DEPTNO INT PRIMARY KEY, DNAME VARCHAR(20), LOC VARCHAR(20));
```
```sql
INSERT INTO DEPT1 (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');
```
```sql
INSERT INTO DEPT1 (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');
```
```sql
INSERT INTO DEPT1 (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');
```
```sql
INSERT INTO DEPT1 (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
```sql
COMMIT;
```

## Q2 Update the location of dept number ‘40’ as ‘San Francisco’  and don’t commit the table.
```sql
UPDATE DEPT1 SET LOC = 'SAN FRANCISCO' WHERE DEPTNO = 40;
```

## Q3 Rollback to the previous state of data in the deparment table and specify the output of the table with select query.
```SQL
ROLLBACK;
```
```SQL
SELECT * FROM DEPT1;
```

## Q4 Delete all the ENTRIES from department table from the location CHICAGO.
```SQL
DELETE FROM DEPT1 WHERE LOC = 'CHICAGO';
```
 
## Q5 Change LOC=’BOSTON’ for deptno=40 in DEPT table
```SQL
UPDATE DEPT1 SET LOC = 'BOSTON' WHERE DEPTNO = 40;
```

## Q6 Create SAVEPOINT in the name ‘update_over’
```SQL
SAVEPOINT update_over;
```

## Q7 Insert another row in DEPT table with your own values
```SQL
INSERT INTO DEPT1 (DEPTNO, DNAME, LOC) VALUES (50, 'MARKETING', 'LOS ANGELES');
```

## Q8 Display the updated data as of now in the department table.
```SQL
SELECT * FROM DEPT1;
```

## Q9 Create SAVEPOINT in the name ‘update_another’
```SQL
SAVEPOINT update_another;
```

## Q10Display the data. Then Rollback the transaction upto the point ‘update_over’ and display the details of table and write the inference.
```SQL
SELECT * FROM DEPT1;
```
```SQL
ROLLBACK TO update_over;
```
```SQL
SELECT * FROM DEPT1;
```
