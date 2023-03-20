```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```
# SQL FUNCTIONS 
# Drop the existing table
```sql
Drop table emp;
```
# Create The table emp
```sql
CREATE TABLE emp (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
# Insert Values
```sql
INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Q1) Find number of rows in the table EMP
```sql
SELECT COUNT(*) FROM emp;
```

## Q2)	Find number of designations available in EMP table.
```sql
SELECT COUNT(DISTINCT job) FROM emp;
```

## Q3)	What is the difference between the following queries
```sql
select count(comm) from emp;
```
```sql
select count(nvl(comm,0)) from emp;
```

## Q4)	Find maximum, minimum and average salary in EMP table.
```sql
SELECT MAX(sal), MIN(sal), AVG(sal) FROM emp;
```

## Q5)	Find number of employees who work in department number 30
```sql
SELECT COUNT(*) FROM emp WHERE deptno = 30;
```

## Q6)	Find the maximum salary paid to a ‘CLERK’
```sql
SELECT MAX(sal) FROM emp WHERE job = 'CLERK';
```

## Q7)	List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
```sql
SELECT job, COUNT(*) as num_employees FROM emp GROUP BY job ORDER BY num_employees DESC;
```

## Q8) List the total salary, maximum and minimum salary and average salary of the employees jobwise.
```sql
SELECT job, SUM(sal) as total_salary, MAX(sal) as max_salary, MIN(sal) as min_salary, AVG(sal) as avg_salary FROM emp GROUP BY job;
```

## Q9) List the total salary, maximum and minimum salary and average salary of the employees jobwise, for department 20 and display only those rows having an average salary > 1000.
```sql
 SELECT job, SUM(sal) as total_salary, MAX(sal) as max_salary, MIN(sal) as min_salary, AVG(sal) as avg_salary FROM emp WHERE deptno = 20 GROUP BY job HAVING AVG(sal) > 1000;
```

## Q10)	List the job and total salary of employees jobwise, for jobs other than ‘PRESIDENT’ and display only those rows having total salary > 5000.
```sql
 SELECT job, SUM(sal) as total_salary FROM emp WHERE job != 'PRESIDENT' GROUP BY job HAVING SUM(sal) > 5000;
```