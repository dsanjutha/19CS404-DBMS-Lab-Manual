# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table For example:

Result Specialty Gender TotalDoctors

Cardiology Male 1 Dermatology Male 1 Gastroenterology Female 4 Gastroenterology Male 1 Pediatrics Female 1 Pediatrics Male 2

```sql

SELECT Specialty,Gender,count(*) as TotalDoctors
from Doctors
group by Specialty,Gender
order by Specialty,Gender;

```

**Output:**

<img width="841" height="622" alt="image" src="https://github.com/user-attachments/assets/86e83892-6e75-4200-872a-d3c00c034b93" />


**Question 2**
---

Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee For example:

Result city Income

Alaska 450000 Arizona 1000000 California 5300000 Florida 5350000 Georgia 250000 here


```sql
SELECT city, sum(income) as Income from employee
group by city having Income > 200000;
```

**Output:**

<img width="822" height="753" alt="image" src="https://github.com/user-attachments/assets/964833d7-3b2e-4527-8cfa-aad33f6006d1" />


**Question 3**
---

Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1

For example:

Result occupation MIN(workhour)

Business 10 Doctor 15 Engineer 12 Teacher 9


```sql
SELECT occupation,  AVG(workhour) from employee1
group by occupation having AVG(workhour) between 10 and 12;
```

**Output:**

<img width="813" height="597" alt="image" src="https://github.com/user-attachments/assets/41322fd4-43dc-4d30-865c-e0b67c4c7e26" />


**Question 4**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

For example:

Result occupation AVG(workhour)

Business 10.0 Engineer 12.0

```sql
SELECT occupation,  AVG(workhour) from employee1
group by occupation having AVG(workhour) between 10 and 12;
```

**Output:**

<img width="808" height="575" alt="image" src="https://github.com/user-attachments/assets/f0689e09-6613-4395-9e64-d81270b1c96d" />


**Question 5**
---
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name type

id INTEGER name TEXT city TEXT email TEXT phone INTEGER For example:

Result avg_name_length 10.0

```sql
SELECT avg(length(name)) as avg_name_length from customer
where city = 'Chennai';

```

**Output:**

<img width="670" height="530" alt="image" src="https://github.com/user-attachments/assets/d019a481-649d-494f-88fd-3966dfbcf62f" />




**Question 6**
---
Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

For example:

Result MINIMUM

```sql
SELECT min(purch_amt) as MINIMUM FROM orders
order by MINIMUM ASC LIMIT 1;
```

**Output:**

<img width="680" height="527" alt="image" src="https://github.com/user-attachments/assets/965b7feb-b419-4fee-91a7-3655d5751f6d" />


**Question 7**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name type

id INTEGER name TEXT city TEXT email TEXT phone INTEGER For example:

Result name email min_email_length

Ravi Kumar ravi@gmail.com 14

```sql
SELECT name,email, length(email) as min_email_length
from customer
order by length(email) asc
limit 1;
```

**Output:**

<img width="817" height="298" alt="image" src="https://github.com/user-attachments/assets/332ea122-ba92-42a2-998c-44441da0f714" />


**Question 8**
---

Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name type

id INTEGER name TEXT unit TEXT inventory INTEGER price REAL

For example:

Result fruit_name lowest_quantity

Watermelon 15
```sql
SELECT name as fruit_name, inventory as lowest_quantity from fruits
order by inventory asc limit 1;
```

**Output:**

<img width="821" height="446" alt="image" src="https://github.com/user-attachments/assets/49374776-de6c-4ea4-aa55-0bd8c25c5b9c" />


**Question 9**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table

For example:

Result Frequency TotalPrescriptions

Every 3 weeks 1 Every 6 hours 1 Once 1 Once daily 4 Once daily at 1 Pending 1 Twice daily 1

```sql
SELECT Frequency,count(*) as TotalPrescriptions 
from Prescriptions
group by Frequency  
order by Frequency ;
```

**Output:**

<img width="818" height="653" alt="image" src="https://github.com/user-attachments/assets/18cb84fd-75dc-4ef3-9ef4-bc07be1c8732" />


**Question 10**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

For example:

Result COUNT 6

```sql
select count(distinct salesman_id) as COUNT
from orders;
```

**Output:**

<img width="716" height="590" alt="image" src="https://github.com/user-attachments/assets/08473653-51ff-4ebf-9a00-207b376722d5" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
