## Table
```sql
create table manager(enumber number(2),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## Values
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```
## Q1)	Update all the records of manager table by increasing 10% of their salary as bonus.
```sql 
UPDATE manager set salary = salary+salary/10;
```
## Q2)	Delete the records from manager table where the salary less than 2750.
```sql 
DELETE FROM manager WHERE salary < 2750;
```
## Q3)	Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
```sql
SELECT ename as "Name",salary*12 as annualsalary from manager;
```
## Q4)	List concatenated value of name and designation of each employee.
```sql
SELECT ename || ' ' || designation as concat FROM manager;
```
## Q5)	List the names of Clerks from emp table.
```sql 
select ename from manager where designation = 'clerk';
```
## Q6)	List the Details of Employees who have joined before 30 Sept 81.
```SQL
select * from manager where Hiredate < '30-sep-81';
```
## Q7)	List names of employees who’s employee numbers are 7369,7839,7934,7788.
```sql
select enumber from manager where enumber in (7369,7521,7839,7934,7788);
```
## Q8)	List the names of employee who are not Managers.
```sql
select ename from manager where designation != 'manager';
```
## Q9)	List the names of employees not belonging to dept no 30,40 & 10
```sql
select ename from manager where deptno != 30 and deptno != 40 and deptno != 10 ; 
```
## Q10)	List names of those employees joined between 30 June 81 and 31 Dec 81.
```sql
select ename from manager where Hiredate between '30-Jun-81' and '31-Dec-81';
```
## Q11)	List different designations in the company.
```sql
select distinct designation from manager;
```
## Q12)	List the names of employees not eligible for commission.
```sql
select ename from manager where commission =0;
```
## Q13)	List names and designations of employee who does not report to anybody
```sql
select ename,designation from manager where reporting is NULL;
```
## Q14)	List all employees not assigned to any department.
```sql
select ename from manager where deptno is NULL;
```
## Q15)	List names of employee who are eligible for commission.
```sql
select ename from manager where commission > 0;
```
## Q16)	List employees whose name either start or end with ‘s’.
```sql
select ename from manager where ename like 'S%' or ename like '%S';
```
## Q17)	List names of employees whose names have ‘i’ as the second character.
```sql
select ename from manager where ename like '_i%';
```
## Q18)	Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
```sql
select Hiredate,ename,designation,deptno from manager order by Hiredate;
```
## Q19) Sort emp table in descending order by annual salary and list empno, ename, job and annual-salary.
```sql
select enumber,ename,designation,annualsalary from manager order by annualsalary desc;
```
## Q20)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
```sql
select ename,deptno,salary from manager order by deptno, salary desc;
```