# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="821" height="343" alt="image" src="https://github.com/user-attachments/assets/1a87b3ce-9828-4e72-8952-c83576d22812" />


select * from medications where dosage=(select min(dosage) from medications);



```sql
<img width="808" height="377" alt="image" src="https://github.com/user-attachments/assets/3f564cb5-a0eb-4e11-a896-203eb26c5e50" />

```

**Output:**

<img width="807" height="372" alt="image" src="https://github.com/user-attachments/assets/ae9f6aff-8bd6-475c-b82a-939c334db410" />


**Question 2**
---
<img width="815" height="402" alt="image" src="https://github.com/user-attachments/assets/47ce7a21-facb-4784-8fa0-35f709e16d34" />

select name,city from customer where city in (select city from customer where id in (3,7));

**Output:**

<img width="813" height="712" alt="image" src="https://github.com/user-attachments/assets/94e84900-4f2d-4689-81fa-cb35635547a1" />




**Question 3**
---
<img width="795" height="423" alt="image" src="https://github.com/user-attachments/assets/cba82ce3-72d0-4398-b906-8afccbca0de5" />


select * from medications where dosage=(select max(dosage) from medications);

**Output:**


<img width="758" height="365" alt="image" src="https://github.com/user-attachments/assets/bfbe2b2a-c1b5-4f6f-815b-38af63e5c3c7" />





**Question 4**
---

<img width="783" height="346" alt="image" src="https://github.com/user-attachments/assets/6e388d38-5bca-4ae9-a448-84e7064a74aa" />


select * from departments where length(department_name)>(select avg(length(department_name)) from departments);



**Output:**




<img width="657" height="445" alt="image" src="https://github.com/user-attachments/assets/c15470ac-1ebe-415b-9718-bb97bc7a5769" />


**Question 5**
---
<img width="817" height="398" alt="image" src="https://github.com/user-attachments/assets/4d2dbd5c-d82e-4742-b225-01511598a31d" />

select * from orders where purch_amt > (select avg(purch_amt) from orders where ord_date='2012-10-10');



**Output:**




<img width="810" height="343" alt="image" src="https://github.com/user-attachments/assets/f6bc8d31-28d3-48d1-accb-179a4d3f13b4" />



**Question 6**
---
<img width="787" height="472" alt="image" src="https://github.com/user-attachments/assets/f494bea7-2e2c-4ee4-8265-8ecb8c2cba9e" />

select * from customers where salary=1500;


**Output:**

<img width="813" height="257" alt="image" src="https://github.com/user-attachments/assets/0ab36b35-7da5-4450-b776-eaad37a5dd49" />


**Question 7**
---
<img width="797" height="396" alt="image" src="https://github.com/user-attachments/assets/15d152c8-64d2-448c-bb0b-484d84cb029e" />
select name from customer where phone in (select phone from customer group by phone having count(*)=1);




**Output:**

<img width="631" height="592" alt="image" src="https://github.com/user-attachments/assets/e659a5e9-d1fe-4b1a-8778-cdc4f958cfac" />


**Question 8**
---
<img width="832" height="438" alt="image" src="https://github.com/user-attachments/assets/480ea772-db94-4a17-bfa0-d043ffbd9fd7" />
select * from employee where age < (select avg(age) from employee where income>250000);




**Output:**

<img width="827" height="377" alt="image" src="https://github.com/user-attachments/assets/a87462f6-cbab-4e22-abee-929a444ae68f" />


**Question 9**
---
<img width="816" height="573" alt="image" src="https://github.com/user-attachments/assets/3344edaf-e40b-44cf-97d4-e08664d80c6d" />
select * from customers where salary>1500;




**Output:**

<img width="802" height="446" alt="image" src="https://github.com/user-attachments/assets/ce87a8c5-c5cc-4cec-9280-f00f64ff0510" />


**Question 10**
---
<img width="826" height="331" alt="image" src="https://github.com/user-attachments/assets/130491dd-b90d-4390-8f7f-03ba38129666" />

SELECT grade, COUNT(*) 
FROM customer 
WHERE grade > (SELECT AVG(grade) 
               FROM customer 
               WHERE city = 'New York')
GROUP BY grade;




**Output:**

<img width="750" height="431" alt="image" src="https://github.com/user-attachments/assets/50d55076-e539-4b25-b4e9-bb351f958b90" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
