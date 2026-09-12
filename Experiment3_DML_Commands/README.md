# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

For example:

Test Result select changes(); changes()

4--


```sql
UPDATE products
set reorder_lvl=40
where category='Grocery';
```

**Output:**

<img width="845" height="298" alt="image" src="https://github.com/user-attachments/assets/eea06513-7146-4011-bf8d-a42d6a9bac4f" />


**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.
---


```sql
product_id product_name category cost_price sell_price reorder_lvl quantity supplier_id

UPDATE products
set product_name ='Premium Bread' 
where product_id=5;
```

**Output:**

<img width="851" height="327" alt="image" src="https://github.com/user-attachments/assets/a7125610-ceaf-4ca6-ba00-4a79dc36ab84" />


**Question 3**
---
Write a SQL statement to double the availability of the product with product_id 1.
---

```sql
UPDATE products 
set  availability = availability *2
where product_id =1;
```

**Output:**

<img width="843" height="212" alt="image" src="https://github.com/user-attachments/assets/1b25c33d-a677-48f5-a4d7-efd83a8857c6" />


**Question 4**
---
Write a SQL statement to Update the grade of all customers in Chennai city as 5.

```sql
UPDATE customer 
set grade=5
where city='Chennai';
```

**Output:**

<img width="851" height="377" alt="image" src="https://github.com/user-attachments/assets/74eb3e55-c819-4995-afbc-244bf3325af1" />


**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ |CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 | For example:

Test Result select changes(); changes() 14

```sql
DELETE FROM customer
where grade%2=1;
```

**Output:**

<img width="853" height="338" alt="image" src="https://github.com/user-attachments/assets/9f7f00c4-030b-4970-a74c-d0c10c5b443d" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date For example:

Test Result SELECT * FROM surgeries; surgery_id patient_id surgeon_id surgery_date

1 1 1 2024-01-15 2 2 2 2024-02-28 3 3 3 2024-03-25 surgery_id patient_id surgeon_id surgery_date

1 1 1 2024-01-15 3 3 3 2024-03-25

```sql
DELETE FROM Surgeries
where surgery_date='2024-02-28';
```

**Output:**

<img width="855" height="305" alt="image" src="https://github.com/user-attachments/assets/6fb3dba0-d28b-4e66-a5d3-d6068b8a67ff" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ |CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 | For example:

Test Result select changes(); CUST_CODE CUST_NAME CUST_CITY WORKING_AREA CUST_COUNTRY GRADE OPENING_AMT RECEIVE_AMT PAYMENT_AMT OUTSTANDING_AMT PHONE_NO AGENT_CODE

C00013 Holmes London London UK 2 6000 5000 7000 4000 BBBBBBB A003 changes() 1

```sql
DELETE FROM Customer
where CUST_NAME like '%Holmes%';
```

**Output:**

<img width="840" height="437" alt="image" src="https://github.com/user-attachments/assets/a16ac6bc-dc44-4172-82d9-a540123cc34d" />


**Question 8**
---
Write a SQL query to Select all patients whose name starts with A.

Table: Patients

name type

patient_id INT first_name VARCHAR(50) last_name VARCHAR(50) date_of_birth DATE admission_date DATE discharge_date DATE doctor_id INT For example:

Result patient_id first_name last_name date_of_birth admission_date discharge_date doctor_id

1 Alice Williams 1980-05-12 2024-01-10 1
```sql
SELECT * FROM Patients
where first_name>='A'
and first_name<'B';

```

**Output:**

<img width="851" height="287" alt="image" src="https://github.com/user-attachments/assets/ff59cae6-75a2-4e94-92c6-752bce194e07" />


**Question 9**
---
Write a query to find all the employees whose salary is between 50000 to 100000 from employeeposition table.

EmpID

EmpPosition

DateOfJoining

Salary

1

Manager

01/05/2024

500000

2

Executive

02/05/2024

75000

For example:

Result EmpID EmpPosition DateOfJoining Salary

2 Executive 2024-05-02 75000 3 Manager 2024-05-01 90000 2 Lead 2024-05-02 85000

```sql
 SELECT * FROM employeeposition
where salary between 50000 and 100000;
```

**Output:**

<img width="837" height="252" alt="image" src="https://github.com/user-attachments/assets/0f27c8db-bcd7-4409-8027-7c9dfbe6d142" />


**Question 10**
---
Write a SQL query to assign a priority of 'Low', 'Medium', or 'High' to value2 based on whether it is less than 20, between 20 and 50, or greater than 50, respectively in the Calculations table.

cid name type notnull dflt_value pk

0 id INTEGER 0 1 1 value1 REAL 0 0 2 value2 REAL 0 0 3 base INTEGER 0 0 4 exponent INTEGER 0 0 5 number REAL 0 0 6 decimal REAL 0 0

For example:

Result id value2 priority

1 2.0 Low 2 5.0 Low 3 7.0 Low 4 9.0 Low
---


```sql
SELECT id,value2 ,
case 
when value2<20 then "Low"
when value2 between 20 and 50 then "Medium"
else "High"
end as priority
from Calculations
```

**Output:**

<img width="847" height="547" alt="image" src="https://github.com/user-attachments/assets/b58fae72-8464-49eb-ae0a-46ffc268fd9d" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
