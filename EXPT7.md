```
Give this Repository a ⭐️⭐️ Star ⭐️⭐️ for updates.
COPY PASTE ALL THE QUERIES ONE BY ONE IN SQLPLUS TO EXECUTE IT WITHOUT ANY ERROR
```

# JOINING TABLES
## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(50),city VARCHAR(50),grade INT,salesman_id INT);
```

## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```

## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(50),city VARCHAR(50),commission DECIMAL(4,2));
```

## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```

## Create a Order1 table
```sql
CREATE TABLE Order1 (ord_no INT,purch_amt DECIMAL(8,2),ord_date DATE,customer_id INT,salesman_id INT);
```

```sql
ALTER SESSION SET nls_date_format='yyyy-mm-dd';
```

## Inserting Values to the Table
```sql
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70001, 150.5, '2012-10-05', 3005, 5002);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70009, 270.65, '2012-09-10', 3001, 5005);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70002, 65.26, '2012-10-05', 3002, 5001);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70004, 110.5, '2012-08-17', 3009, 5003);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70007, 948.5, '2012-09-10', 3005, 5002);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70005, 2400.6, '2012-07-27', 3007, 5001);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70008, 5760, '2012-09-10', 3002, 5001);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70010, 1983.43, '2012-10-10', 3004, 5006);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70003, 2480.4, '2012-10-10', 3009, 5003);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70012, 250.45, '2012-06-27', 3008, 5002);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70011, 75.29, '2012-08-17', 3003, 5007);
INSERT INTO Order1 (ord_no, purch_amt, ord_date, customer_id, salesman_id) VALUES (70013, 3045.6, '2012-04-25', 3002, 5001);
```
## Q1) write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
```sql
SELECT s.name AS Salesman1, c.cust_name, c.city FROM Salesman1 s INNER JOIN Customer1 c ON s.city = c.city;
```

## Q2) write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.
```sql
SELECT c.cust_name AS Customer_Name, c.city, s.name AS Salesman, s.commission FROM Customer1 c INNER JOIN Salesman1 s ON c.salesman_id = s.salesman_id;
```

## Q3) Write a SQL statement to make a Cartesian product between salesman and customer
```sql
SELECT * FROM Salesman1, Customer1;
```

## Q4) Write a SQL statement to generate a list in ascending order of salespersons who work either for one or more customers or have not yet joined any of the customers.
```sql
SELECT s.name AS Salesman FROM Salesman1 s LEFT JOIN Customer1 c ON s.salesman_id = c.salesman_id WHERE c.salesman_id IS NOT NULL OR c.salesman_id IS NULL ORDER BY s.name ASC;
```

## Q5) Write a SQL query to find salespeople who received commissions of more than 10 percent from the company. Return Customer Name, customer city, Salesman, commission.
```sql
SELECT c.cust_name AS Customer_Name, c.city AS Customer_City, s.name AS Salesman, s.commission FROM Customer1 c JOIN Salesman1 s ON c.salesman_id = s.salesman_id WHERE s.commission > 0.1 ORDER BY s.name ASC;
```