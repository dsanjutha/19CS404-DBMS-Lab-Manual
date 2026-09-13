# Experiment 10: PL/SQL – Triggers

## AIM
To write and execute PL/SQL trigger programs for automating actions in response to specific table events like INSERT, UPDATE, or DELETE.

---

## THEORY

A **trigger** is a stored PL/SQL block that is automatically executed or fired when a specified event occurs on a table or view. Triggers can be used for enforcing business rules, auditing changes, or automatic updates.

### Types of Triggers:
- **Before Trigger**: Executes before the operation (INSERT, UPDATE, DELETE).
- **After Trigger**: Executes after the operation.
- **Row-level Trigger**: Executes for each affected row.
- **Statement-level Trigger**: Executes once for the triggering statement.

**Basic Syntax:**
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
[FOR EACH ROW]
BEGIN
   -- trigger logic
END;
```

## 1. Write a trigger to log every insertion into a table.
**Steps:**
- Create two tables: `employees` (for storing data) and `employee_log` (for logging the inserts).
- Write an **AFTER INSERT** trigger on the `employees` table to log the new data into the `employee_log` table.
program
```
CREATE OR REPLACE TRIGGER trg_after_employee_insert
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_log (emp_id, name, position, salary)
    VALUES (:NEW.emp_id, :NEW.name, :NEW.position, :NEW.salary);
END;
/
SELECT table_name FROM user_tables WHERE table_name IN ('EMPLOYEES', 'EMPLOYEE_LOG');
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    name VARCHAR2(100),
    position VARCHAR2(100),
    salary NUMBER(10, 2)
);
CREATE OR REPLACE TRIGGER trg_after_employee_insert
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_log (emp_id, name, position, salary)
    VALUES (:NEW.emp_id, :NEW.name, :NEW.position, :NEW.salary);
END;
/
INSERT INTO employees (emp_id, name, position, salary)
VALUES (1, 'Alice', 'Engineer', 75000);
SELECT * FROM employee_log;
```


**Expected Output:**
- A new entry is added to the `employee_log` table each time a new record is inserted into the `employees` table.

<img width="810" height="210" alt="image" src="https://github.com/user-attachments/assets/ca8964be-d9c8-4d2c-b796-7a4b2a691dec" />


---

## 2. Write a trigger to prevent deletion of records from a sensitive table.
**Steps:**
- Write a **BEFORE DELETE** trigger on the `sensitive_data` table.
- Use `RAISE_APPLICATION_ERROR` to prevent deletion and issue a custom error message.
program
```
CREATE OR REPLACE TRIGGER prevent_sensitive_data_deletion
BEFORE DELETE ON sensitive_data
FOR EACH ROW
BEGIN
    RAISE_APPLICATION_ERROR(-20001, 'Deletion not allowed on this table.');
END;
```

**Expected Output:**
- If an attempt is made to delete a record from `sensitive_data`, an error message is raised, e.g., `ERROR: Deletion not allowed on this table.`

  <img width="777" height="347" alt="image" src="https://github.com/user-attachments/assets/4f657c89-77d9-4376-81cc-8208766af1f8" />


---

## 3. Write a trigger to automatically update a `last_modified` timestamp.
**Steps:**
- Add a `last_modified` column to the `products` table.
- Write a **BEFORE UPDATE** trigger on the `products` table to set the `last_modified` column to the current timestamp whenever an update occurs.
program
```

CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(255),
    -- other columns...
    last_modified TIMESTAMP
);
CREATE OR REPLACE TRIGGER update_products_timestamp
BEFORE UPDATE ON products
FOR EACH ROW
BEGIN
    :NEW.last_modified := SYSTIMESTAMP;
END;
/
```

**Expected Output:**
- The `last_modified` column in the `products` table is updated automatically to the current date and time when any record is updated.

<img width="565" height="160" alt="image" src="https://github.com/user-attachments/assets/47433415-4bc6-4113-82a0-22a9d36762eb" />


---

## 4. Write a trigger to keep track of the number of updates made to a table.
**Steps:**
- Create an `audit_log` table with a counter column.
- Write an **AFTER UPDATE** trigger on the `customer_orders` table to increment the counter in the `audit_log` table every time a record is updated.

program
```
CREATE TABLE customer_orders (
    order_id NUMBER PRIMARY KEY,
    customer_id NUMBER,
    order_date DATE,
    order_total NUMBER,
    -- Add other relevant columns as needed
    order_status VARCHAR2(20) -- Added a sample column
);
CREATE TABLE audit_log (
    table_name VARCHAR2(255),
    update_count NUMBER
);

INSERT INTO audit_log (table_name, update_count) VALUES ('customer_orders', 0);
CREATE OR REPLACE TRIGGER customer_orders_update_audit
AFTER UPDATE ON customer_orders
BEGIN
    UPDATE audit_log
    SET update_count = update_count + 1
    WHERE table_name = 'customer_orders';
END;
/
UPDATE customer_orders SET order_status = 'Shipped' WHERE order_id = 1;
SELECT update_count FROM audit_log WHERE table_name = 'customer_orders';
```

**Expected Output:**
- The `audit_log` table will maintain a count of how many updates have been made to the `customer_orders` table.

<img width="666" height="212" alt="image" src="https://github.com/user-attachments/assets/bf030ef1-3960-4331-b13c-ce2dacdb22e3" />


---

## 5. Write a trigger that checks a condition before allowing insertion into a table.
**Steps:**
- Write a **BEFORE INSERT** trigger on the `employees` table to check if the inserted salary meets a specific condition (e.g., salary must be greater than 3000).
- If the condition is not met, raise an error to prevent the insert.

 program
  ```
INSERT INTO audit_log (table_name, update_count) VALUES ('customer_orders', 0);
CREATE OR REPLACE TRIGGER customer_orders_update_audit
AFTER UPDATE ON customer_orders
BEGIN
    UPDATE audit_log
    SET update_count = update_count + 1
    WHERE table_name = 'customer_orders';
END;
/
CREATE OR REPLACE TRIGGER check_employee_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    IF :NEW.salary < 3000 THEN
        RAISE_APPLICATION_ERROR(-20002, 'Salary below minimum threshold.');
    END IF;
END;
/
INSERT INTO employees (employee_id, employee_name, salary) VALUES (1, 'Alice Smith', 3500);
INSERT INTO employees (employee_id, employee_name, salary) VALUES (2, 'Bob Johnson', 2500);
SELECT * from employees;
```

**Expected Output:**

- If the inserted salary in the `employees` table is below the condition (e.g., salary < 3000), the insert operation is blocked, and an error message is raised, such as: `ERROR: Salary below minimum threshold.`


<img width="796" height="300" alt="image" src="https://github.com/user-attachments/assets/3c7c6a9d-5c24-4690-9fc9-2640195f3ec4" />


## RESULT
Thus, the PL/SQL trigger programs were written and executed successfully.
