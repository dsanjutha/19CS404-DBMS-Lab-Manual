# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="827" height="447" alt="image" src="https://github.com/user-attachments/assets/7b8545ee-3549-4627-91f5-3ee592234901" />


```sql
SELECT p.first_name, s.*
FROM patients p
INNER JOIN surgeries s ON p.patient_id = s.patient_id
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31'
  AND NOT (p.admission_date BETWEEN '2024-03-01' AND '2024-03-31');

```

**Output:**

<img width="822" height="327" alt="image" src="https://github.com/user-attachments/assets/6fa1210c-2c6f-4c89-be39-3b81538f6644" />


**Question 2**
---
<img width="821" height="492" alt="image" src="https://github.com/user-attachments/assets/aa74d27f-6efa-4b18-a4ca-e69258e86c91" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="827" height="518" alt="image" src="https://github.com/user-attachments/assets/df1c05d1-d63c-47a5-8de8-63cd6a8c6584" />


**Question 3**
---
<img width="828" height="467" alt="image" src="https://github.com/user-attachments/assets/471d9aef-69e3-4c97-b3e3-1ae164ea2bfb" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**
<img width="825" height="538" alt="image" src="https://github.com/user-attachments/assets/cfbe0158-24a3-4fcf-937f-6f36a9cf54b1" />


**Question 4**
---
<img width="822" height="332" alt="image" src="https://github.com/user-attachments/assets/a1f0825d-bf8c-4d91-979f-a4fd46e5ecbb" />


```sql
SELECT 
    s.name AS salesman_name,
    c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id;

```

**Output:**

<img width="793" height="812" alt="image" src="https://github.com/user-attachments/assets/498f6259-0140-4e0f-abf6-8572e40708ce" />


**Question 5**
---
<img width="816" height="438" alt="image" src="https://github.com/user-attachments/assets/d22ef875-a39c-4a05-949b-1be6da58330c" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;

```

**Output:**

<img width="822" height="360" alt="image" src="https://github.com/user-attachments/assets/592856a5-e36e-4c75-89e2-ad17cdb0a91e" />


**Question 6**
---
<img width="821" height="270" alt="image" src="https://github.com/user-attachments/assets/aa48464f-6f47-4bc5-8c30-4949f27ce1f1" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE c.city = 'London';

```

**Output:**

<img width="827" height="367" alt="image" src="https://github.com/user-attachments/assets/d3f9bc29-2329-4082-b0ee-3886a333a5b2" />


**Question 7**
---
<img width="820" height="478" alt="image" src="https://github.com/user-attachments/assets/bea00b2f-2330-4ed3-bec3-a7fcf43edf72" />


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="823" height="538" alt="image" src="https://github.com/user-attachments/assets/2739eb6c-e838-417c-9714-4bb46ade6abc" />


**Question 8**
---
<img width="818" height="416" alt="image" src="https://github.com/user-attachments/assets/cffedc26-302f-4a8c-a459-e7b44a71bbda" />


```sql
SELECT 
    p.first_name AS patient_name,
    t.result_id,
    t.patient_id,
    t.test_name,
    t.result,
    t.test_date
FROM patients p
JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';

```

**Output:**
<img width="822" height="312" alt="image" src="https://github.com/user-attachments/assets/93d100c4-c042-4d29-abea-6724371052c0" />


**Question 9**
---
<img width="821" height="467" alt="image" src="https://github.com/user-attachments/assets/fbb651ce-3cb8-4df6-a5e5-cd5b3a29f5f2" />


```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;

```

**Output:**

<img width="830" height="543" alt="image" src="https://github.com/user-attachments/assets/c22c0de3-04eb-4013-bcd8-9be6af57b9dd" />


**Question 10**
---
<img width="822" height="452" alt="image" src="https://github.com/user-attachments/assets/3bf1f2fb-9dd9-4848-9feb-4344ada689ef" />


```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;

```

**Output:**

<img width="722" height="315" alt="image" src="https://github.com/user-attachments/assets/4d0f6b62-c73b-4ad8-a1c1-79594bac5109" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
