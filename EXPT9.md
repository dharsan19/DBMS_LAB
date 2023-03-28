```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```
# VIEWS
## Q1) Create a view empv10 that contains empno, ename, job of the employees who work in dept 10. Also describe the structure of the view.
```sql
CREATE VIEW empv10 AS SELECT empno, ename, job FROM EMP WHERE deptno = 10;
```

## Q2) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
```sql
CREATE VIEW empv30 AS SELECT empno AS "Employee Number", ename AS "Employee Name", sal AS "Salary" FROM EMP WHERE deptno = 30;
```

## Q3) Update the view empv10 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
```sql
UPDATE empv10 SET sal = sal * 1.1 WHERE job = 'CLERK';
```

## Q4) Modify the view empv10 which contains the data empno, ename, job, sal. Add an alias for each column name.
```sql
CREATE OR REPLACE VIEW empv10 AS SELECT empno AS "Employee Number", ename AS "Employee Name", job AS "Job Title", sal AS "Salary" FROM EMP WHERE deptno = 10;
```

## Q5) Using emp table, create a view pay which contains ename, monthly_sal, annual_sal, deptno.
```sql
CREATE VIEW pay AS SELECT ename, sal/12 AS monthly_sal, sal*12 AS annual_sal, deptno FROM EMP;

```

## Q6) Create a view dept_stat which contains department no., department name, minimum salary, maximum salary, total salary.
```sql
CREATE VIEW dept_stat AS SELECT d.deptno, d.dname, MIN(e.sal) AS min_sal, MAX(e.sal) AS max_sal, SUM(e.sal) AS total_sal FROM EMP e JOIN DEPT d ON e.deptno = d.deptno GROUP BY d.deptno, d.dname;
```

## Q7) Execute the following query and then try to delete the row with dept no 20. Now write in words that you understand
```sql
/* Note this query is the Question */
create or replace view empv20
as select * from emp where deptno = 20
with check option constraint empv20_ck;
```
```sql
/* Answer */
The given query creates or replaces a view named empv20 that selects all the columns from the EMP table where the deptno column equals 20. The view also has a check option constraint named empv20_ck.

The check option constraint ensures that any data modification to the view only affects rows that meet the view's filter criteria. In this case, the constraint makes sure that any new or modified rows inserted into the empv20 view also have a deptno value of 20. This constraint helps maintain data consistency and integrity by preventing invalid data from being added to the view.

Regarding the task of deleting the row with dept no 20, it is not possible to do so directly since the view empv20 only selects rows with deptno of 20. If you want to delete the row with deptno 20, you will need to delete it from the EMP table directly. However, if you try to delete a row from the EMP table that has a deptno of 20, the check option constraint named empv20_ck will prevent the deletion since it violates the constraint's rule that the deptno must be 20.
```

## Q8) Create a view empv10 with all the details of employees who work in dept no. 10.
```sql
CREATE VIEW empv10 AS SELECT * FROM emp WHERE deptno = 10 WITH READ ONLY;
```
## Q9) Statement1 : Update the view will update data in original table.

## Statement 2: update in main table will affect the created view or not?

## State whether the above statements is True or False with explanation.
```
Statement 1 is True. Updating a view can update the underlying data in the original table. This happens when the view is based on a single table and the update statement only modifies columns in that table. In such cases, the update operation is passed through the view to the underlying table, and the data in the table is updated accordingly.

Statement 2 is also True. If an update is made in the main table, it will affect the data in any views based on that table. Views are simply virtual tables that provide a different way of looking at the data in the original table. Therefore, any updates made to the original table will also be reflected in the views that are based on that table.

It is important to note, however, that some views are based on more than one table, or use complex queries or aggregation functions, and in these cases, updates to the view may not be possible, or may not be passed through to the underlying tables. Additionally, views can have various constraints such as read-only or with-check options, which can further limit the ability to update the data in the underlying tables.
```

## Q10) Delete the view empv20.
```sql
DROP VIEW empv20;
```