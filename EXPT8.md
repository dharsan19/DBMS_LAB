```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```
# S U B  Q U E R I E S
## Drop the existing table
```sql
Drop table EMP;
```
```sql
Drop table DEPT;
```
## Create The table EMP
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert Values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
## Create the Table dept
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```

## Insert Values to the Table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

## Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
```sql
SELECT ENAME FROM EMP WHERE SAL > (SELECT SAL FROM EMP WHERE EMPNO = 7566);

```

## Q2)List the name of the employees whose job is equal to the job of employee with empno 7369 and salary is greater than that of employee with empno 7876.
```sql
SELECT ENAME FROM EMP WHERE JOB = (SELECT JOB FROM EMP WHERE EMPNO = 7369) AND SAL > (SELECT SAL FROM EMP WHERE EMPNO = 7876);
```

## Q3) List the ename,job,sal of the employee who get minimum salary in the company.
```sql
SELECT ENAME, JOB, SAL FROM EMP WHERE SAL = (SELECT MIN(SAL) FROM EMP);
```

## Q4) List deptno &amp; min(salary) departmentwise, only if min(sal) is greater than the min(sal) of deptno 20.
```sql
SELECT DEPTNO, MIN(SAL) FROM EMP GROUP BY DEPTNO HAVING MIN(SAL) > (SELECT MIN(SAL) FROM EMP WHERE DEPTNO = 20);
```

## Q5) List empno, ename, job of the employees whose job is not a ‘CLERK’ and whose salary is less than at least one of the salaries of the employees whose job is ‘CLERK’.
```sql
SELECT EMPNO, ENAME, JOB FROM EMP WHERE JOB <> 'CLERK' AND SAL < ANY(SELECT SAL FROM EMP WHERE JOB = 'CLERK');
```

## Q6) List empno, ename, job of the employees whose salary is greater than the average salary of each department.
```sql
SELECT EMPNO, ENAME, JOB FROM EMP WHERE SAL > (SELECT AVG(SAL) FROM EMP WHERE DEPTNO = EMP.DEPTNO);
```

## Q7) List ename, job, sal of the employees whose salary is equal to any one of the salary of the employee ‘SCOTT’ and ‘WARD’.
```sql
SELECT ENAME, JOB, SAL FROM EMP WHERE SAL IN (SELECT SAL FROM EMP WHERE ENAME IN ('SCOTT', 'WARD'));
```

## Q8) List ename, job, sal of the employees whose salary and job is equal to the employee ‘FORD’.
```sql
SELECT ENAME, JOB, SAL FROM EMP WHERE SAL = (SELECT SAL FROM EMP WHERE ENAME = 'FORD') AND JOB = (SELECT JOB FROM EMP WHERE ENAME = 'FORD');
```

## Q9) List ename, job, deptno, sal of the employees whose job is same as ‘JONES’ and salary is greater than the employee ‘FORD’.
```sql
SELECT ENAME, JOB, DEPTNO, SAL FROM EMP WHERE JOB = (SELECT JOB FROM EMP WHERE ENAME = 'JONES') AND SAL > (SELECT SAL FROM EMP WHERE ENAME = 'FORD');
```

## Q10) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
```sql
SELECT ENAME, JOB FROM EMP WHERE DEPTNO = 10 AND JOB IN (SELECT JOB FROM EMP WHERE DEPTNO = 30);
```