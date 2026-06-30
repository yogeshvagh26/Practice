## Overview 

### 🛠️ PART 1: SETUP (Run this once in your SQL environment)
### 📝 PART 2: PRACTICE QUESTIONS + SOLUTIONS

* **SECTION A**: SELECT & WHERE (Basic Filtering)
* **SECTION B**: WHERE with AND / OR (Compound Conditions)
* **SECTION C**: ORDER BY (Sorting)
* **SECTION D**: LIMIT (Restricting Rows)
* **SECTION E**: DISTINCT (Removing Duplicates)
* **SECTION F**: Mixing Everything (SELECT, WHERE, ORDER BY, LIMIT, DISTINCT)
* **SECTION G**: More SELECT Projections (Specific Columns)
* **SECTION H**: Complex WHERE + ORDER + LIMIT
* **SECTION I**: Harder Practice (Still within topics)

---

## 🛠️ PART 1: SETUP (Run this once in your SQL environment)

```sql

    -- 1. Create Database
    CREATE DATABASE company_db;

    -- 2. Use the database
    USE company_db;

    -- 3. Create Tables
    CREATE TABLE employees (
        employee_id INT,
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        department VARCHAR(50),
        salary DECIMAL(10,2),
        hire_date DATE
    );

    CREATE TABLE products (
        product_id INT,
        product_name VARCHAR(100),
        category VARCHAR(50),
        price DECIMAL(10,2),
        stock_quantity INT
    );

    CREATE TABLE customers (
        customer_id INT,
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        city VARCHAR(50),
        state VARCHAR(50),
        signup_date DATE
    );

    -- 4. Insert Sample Data
    INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date)
    VALUES
    (1, 'John', 'Smith', 'Sales', 65000, '2020-01-15'),
    (2, 'Emma', 'Johnson', 'Marketing', 72000, '2019-03-22'),
    (3, 'Michael', 'Brown', 'Sales', 58000, '2021-07-01'),
    (4, 'Sarah', 'Davis', 'IT', 85000, '2018-11-10'),
    (5, 'David', 'Miller', 'IT', 79000, '2020-06-19'),
    (6, 'Laura', 'Wilson', 'Marketing', 67000, '2022-02-28'),
    (7, 'James', 'Moore', 'Sales', 61000, '2021-09-14'),
    (8, 'Linda', 'Taylor', 'HR', 55000, '2020-12-01'),
    (9, 'Robert', 'Anderson', 'IT', 92000, '2017-05-05'),
    (10, 'Mary', 'Thomas', 'HR', 48000, '2023-01-20');

    INSERT INTO products (product_id, product_name, category, price, stock_quantity)
    VALUES
    (101, 'Laptop Pro', 'Electronics', 1200.00, 15),
    (102, 'Wireless Mouse', 'Accessories', 25.50, 200),
    (103, 'USB-C Hub', 'Accessories', 45.00, 0),
    (104, 'Monitor 27"', 'Electronics', 350.00, 8),
    (105, 'Desk Lamp', 'Furniture', 40.00, 45),
    (106, 'Gaming Keyboard', 'Electronics', 95.00, 12),
    (107, 'Office Chair', 'Furniture', 250.00, 5),
    (108, 'HDMI Cable', 'Accessories', 15.00, 150),
    (109, 'Smartphone X', 'Electronics', 999.00, 0),
    (110, 'Notebook Pack', 'Office', 12.00, 300);

    INSERT INTO customers (customer_id, first_name, last_name, city, state, signup_date)
    VALUES
    (201, 'Alice', 'Walker', 'New York', 'NY', '2022-05-10'),
    (202, 'Bob', 'Green', 'Los Angeles', 'CA', '2021-08-21'),
    (203, 'Charlie', 'Adams', 'Chicago', 'IL', '2023-02-14'),
    (204, 'Diana', 'Nelson', 'Houston', 'TX', '2020-11-01'),
    (205, 'Ethan', 'Carter', 'Phoenix', 'AZ', '2019-07-19'),
    (206, 'Fiona', 'Mitchell', 'New York', 'NY', '2022-12-05'),
    (207, 'George', 'Perez', 'Los Angeles', 'CA', '2023-06-30'),
    (208, 'Hannah', 'Roberts', 'Chicago', 'IL', '2021-04-17');

```
---
## 📝 PART 2: PRACTICE QUESTIONS + SOLUTIONS

### **SECTION A: SELECT & WHERE (Basic Filtering)**

#### Q1. Select all columns from the `employees` table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM employees;
```
</details>

---

#### Q2. Select only the `first_name`, `last_name`, and `salary` of all employees.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        salary 
    FROM employees;
```    

</details>

---

#### Q3. Select all employees who work in the `Sales` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department = 'Sales';
```
</details>

---

#### Q4. Select all products with a price greater than `100`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE price > 100;
```    
</details>

---

#### Q5. Select all customers who live in `New York` city.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE city = 'New York';
```    
</details>

---

#### Q6. Select employees with a salary of `65000` or more.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE salary >= 65000;
```
</details>

---

#### Q7. Select products that have `0` stock quantity.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE stock_quantity = 0;
```
</details>

---

#### Q8. Select employees hired after `2021-01-01`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE hire_date > '2021-01-01';
```

</details>


---


### **SECTION B: WHERE with AND / OR (Compound Conditions)**

---

#### Q9. Select employees from the `IT` department with a salary greater than `80000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department = 'IT' AND salary > 80000;
```
</details>

---

#### Q10. Select products from the `Electronics` category with a price less than `500`.

<details> <summary>Click to reveal answer</summary>

```sql

    SELECT * 
    FROM products 
    WHERE category = 'Electronics' AND price < 500;

```
</details>

---

#### Q11. Select customers from `Chicago` OR `Houston`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE city = 'Chicago' OR city = 'Houston';
```

</details>

---

#### Q12. Select employees from `Sales` OR `Marketing` departments.

<details> <summary>Click to reveal answer</summary>

```sql

    SELECT * 
    FROM employees 
    WHERE department = 'Sales' OR department = 'Marketing';

```

</details>

---

#### Q13. Select products that are either in the `Furniture` category OR have a price below `20`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE category = 'Furniture' OR price < 20;
```

</details>

---

#### Q14. Select employees who are in `IT` AND earn less than `80000`, OR are in `HR`.

<details> <summary>Click to reveal answer</summary>

```sql

    SELECT * 
    FROM employees 
    WHERE (department = 'IT' AND salary < 80000) OR department = 'HR';
```
</details>

---

### **SECTION C: ORDER BY (Sorting)**

---

#### Q15. Select all employees and sort them by `salary` from highest to lowest.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    ORDER BY salary DESC;
```

</details>

----

#### Q16. Select all products and sort them by `product_name` in alphabetical order (A-Z).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    ORDER BY product_name ASC;
```

</details>

---

#### Q17. Select all customers and sort them by `state` first, then by `city` (both ascending).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    ORDER BY state ASC, city ASC;
```
</details>

---

#### Q18. Select all employees, sort by `department` ascending, and within the same department sort by `salary` descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    ORDER BY department ASC, salary DESC;
```
</details>

---

#### Q19. Select all products, sort by `stock_quantity` ascending (lowest stock first).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    ORDER BY stock_quantity ASC;
```    
</details>


---

### **SECTION D: LIMIT (Restricting Rows)**

---

#### Q20. Select the first 5 employees from the table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    LIMIT 5;
```    
</details>

----

#### Q21. Select the 3 most expensive products (highest price).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    ORDER BY price DESC 
    LIMIT 3;
```
</details>

---

#### Q22. Select the 2 newest employees (most recent `hire_date`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    ORDER BY hire_date DESC 
    LIMIT 2;
```  
</details>

---

#### Q23. Select the 4 products with the highest stock quantity.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    ORDER BY stock_quantity DESC 
    LIMIT 4;
```

</details>

---

#### Q24. Select the 5th and 6th rows from the `customers` table (hint: use `LIMIT` with offset).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    LIMIT 2 
    OFFSET 4;
    
```
</details>

---

### **SECTION E: DISTINCT (Removing Duplicates)**

---

#### Q25. List all unique `department` names from the employees table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees;
```
</details>

---

#### Q26. List all unique `category` values from the products table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT category 
    FROM products;
```
</details>

---

#### Q27. List all unique `state` values where customers live.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT state 
    FROM customers;
```
</details>

----


#### Q28. List all unique combinations of `city` and `state` from the customers table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT city, state 
    FROM customers;
```    
</details>

---

#### Q29. List all unique `department` values, but only from employees who earn more than `60000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees 
    WHERE salary > 60000;
```
</details>

---

### **SECTION F: Mixing Everything (SELECT, WHERE, ORDER BY, LIMIT, DISTINCT)**

#### Q30. Select distinct departments of employees hired after `2020-01-01`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees 
    WHERE hire_date > '2020-01-01';
```    
</details>

---

#### Q31. Select the names (`first_name`, `last_name`) of the 3 highest-paid employees in the Sales department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        salary 
    FROM employees 
    WHERE department = 'Sales' 
    ORDER BY salary DESC 
    LIMIT 3;
```    
</details>

----

#### Q32. Select all products, filter to only those with price between `30` and `100` (inclusive), sort by price descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM products 
    WHERE price >= 30 AND price <= 100 
    ORDER BY price DESC;
```    
</details>

---

#### Q33. Select the 2 most recently signed-up customers from `California` (CA).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM customers 
    WHERE state = 'CA' 
    ORDER BY signup_date DESC 
    LIMIT 2;
```    
</details>

---

#### Q34. Select distinct product categories that have at least one product with `stock_quantity` greater than `20`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT category 
    FROM products 
    WHERE stock_quantity > 20;
```    
</details>

---


#### Q35. Select the 5 lowest-paid employees, but show only their first_name, last_name, and salary, sorted from lowest to highest.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        salary 
    FROM employees 
    ORDER BY salary ASC 
    LIMIT 5;
```    
</details>

---

### **SECTION G: More SELECT Projections (Specific Columns)**

---

#### Q36. Select the `product_name` and `price` of all products, sort by `product_name` alphabetically.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price 
    FROM products 
    ORDER BY product_name;
```    
</details>

---- 

#### Q37. Select the `first_name` and `hire_date` of all employees in the `Marketing` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date 
    FROM employees 
    WHERE department = 'Marketing';
```    
</details>

---

#### Q38. Select the `city` and `state` of all customers, but only show distinct combinations, sorted by `state`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT city, state 
    FROM customers 
    ORDER BY state;
```    

</details>

---

### **SECTION H: Complex WHERE + ORDER + LIMIT**

----

####  Q39. Find the cheapest product in the `Accessories` category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM products 
    WHERE category = 'Accessories' 
    ORDER BY price ASC 
    LIMIT 1;
```    
</details>

---

#### Q40. Find the most expensive product that is currently in stock (`stock_quantity > 0)`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM products 
    WHERE stock_quantity > 0 
    ORDER BY price DESC 
    LIMIT 1;
```    
</details>

---

#### Q41. List employees in `IT` or `Sales` who earn less than `70000`, sorted by salary descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE (department = 'IT' OR department = 'Sales') AND 
        salary < 70000 
    ORDER BY salary DESC;
```    
</details>

---

#### Q42. Select the 3 customers who signed up earliest (oldest sign-ups).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    ORDER BY signup_date ASC 
    LIMIT 3;
```
</details>

---

#### Q43. Select distinct employee departments, but only for departments that have at least one employee with a salary above `80000` (hint: use WHERE first, then DISTINCT).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees 
    WHERE salary > 80000;
```    
</details>

---

#### Q44. Show the 4th highest salary in the company (hint: order desc and use limit with offset).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT salary 
    FROM employees 
    ORDER BY salary DESC 
    LIMIT 1 
    OFFSET 3;
```    
</details>


---

#### Q45. Select all products, but show only `product_name` and `stock_quantity`, sorted by `stock_quantity` descending, and limit to the top 5.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT product_name, stock_quantity 
    FROM products 
    ORDER BY stock_quantity DESC 
    LIMIT 5;
```    
</details>

---


### **SECTION I: Harder Practice (Still within topics)**

---

#### Q46. Find the names of employees who have a salary between `60000` and `80000`, and sort them by last name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT first_name, last_name, salary 
    FROM employees 
    WHERE salary >= 60000 AND salary <= 80000 
    ORDER BY last_name;
```    
</details>

---

#### Q47. List all distinct product categories that have a product priced under `30`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT category 
    FROM products 
    WHERE price < 30;
```    
</details>

---

#### Q48. Select the `first_name`, `last_name`, and `department` of the 2 highest-paid women 

> (use `first_name` like 'Sarah', 'Laura', 'Mary', etc., or just pick 'Emma' and 'Sarah' from the data) – let's just do the top 2 highest paid employees whose first name starts with 'J' or 'M'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        department, 
        salary 
    FROM employees 
    WHERE first_name LIKE 'J%' OR first_name LIKE 'M%' 
    ORDER BY salary DESC 
    LIMIT 2;
```    
</details> 

<br/>

> Note: `LIKE` wasn't explicitly listed, but it uses WHERE. If you want to avoid LIKE, use `first_name = 'John' OR first_name = 'Michael'` etc.

---

#### Q49. Find the newest product (by `product_id` descending, assuming higher ID means newer) and show its name and price.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price 
    FROM products 
    ORDER BY product_id DESC 
    LIMIT 1;
```
</details>

---

#### Q50. Show a list of all unique departments, but sorted in reverse alphabetical order (Z-A).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees 
    ORDER BY department DESC;
```    
</details>

----

#### Q51. Select all customers from New York (NY) sorted by signup date (newest first), and show only the first 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM customers 
    WHERE state = 'NY' 
    ORDER BY signup_date DESC 
    LIMIT 2;
```    
</details>

----

#### Q52. Select the product with the highest price, but only if it belongs to the `Electronics` category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM products 
    WHERE category = 'Electronics' 
    ORDER BY price DESC 
    LIMIT 1;
```    
</details>

---


#### Q53. Show the 3 employees with the lowest salaries, but exclude the `HR` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM employees 
    WHERE department != 'HR' 
    ORDER BY salary ASC 
    LIMIT 3;
```    
</details>

---

#### Q54. List distinct cities from the customers table, sorted alphabetically, and only show the first 4 distinct cities.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT city 
    FROM customers 
    ORDER BY city ASC LIMIT 4;
```
</details>

---

#### Q55. Select employees who were hired in 2020 (between '2020-01-01' and '2020-12-31'), sorted by hire date.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE hire_date >= '2020-01-01' AND hire_date <= '2020-12-31' 
    ORDER BY hire_date;
```    
</details>

---

### 🎯 Bonus Challenge (Combines everything)

#### Q56. Show the first_name, last_name, department, and salary of the employee with the highest salary in each department? Wait, this requires subqueries or window functions which are NOT in your topics. So let's skip.


#### Instead, here's a final one:


#### Q56 (Final). Select the distinct departments of the 5 most recently hired employees, but sort the output by department name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM (SELECT department FROM employees ORDER BY hire_date DESC LIMIT 5) AS recent_emps 
    ORDER BY department;
    
```    
</details>

> Note: This uses a subquery, which is slightly beyond the strict list, but it's a common pattern. If you want a simpler version:)


> Simpler version without subquery (just get distinct departments of recently hired):

```sql
    SELECT DISTINCT department 
    FROM employees 
    WHERE hire_date IN (SELECT hire_date 
                        FROM employees 
                        ORDER BY hire_date DESC 
                        LIMIT 5);
```

---

### How to use this:

1. Run the **Setup** queries to populate your database.

2. Try to solve each question without looking at the answer.

3. Click "Click to reveal answer" to check your work.

4. Modify the data, add new rows, and re-run the queries for endless practice!

---
<br/><br/><br/><br/>

#### Happy Practicing! 😊✨

<br/><br/><br/><br/>

---

Awesome! Let's dive into Phase 2. I'll use the same tables (employees, products, customers) from Phase 1.

#### ⚠️ CRITICAL SETUP REMINDER:

Since we'll be using `UPDATE`, `DELETE`, and `TRUNCATE` (which permanently change/remove data), **please re-run the INSERT statements from Phase 1** after you finish each destructive exercise to reset your data. I'll also give you a quick reset script at the end.

---

## 📦 Quick Reset Script (Run this whenever your data gets messed up)

```sql

-- Re-insert all original data (copy this block and run it after any DELETE/UPDATE/TRUNCATE)
TRUNCATE TABLE employees;
TRUNCATE TABLE products;
TRUNCATE TABLE customers;

INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date) VALUES
(1, 'John', 'Smith', 'Sales', 65000, '2020-01-15'),
(2, 'Emma', 'Johnson', 'Marketing', 72000, '2019-03-22'),
(3, 'Michael', 'Brown', 'Sales', 58000, '2021-07-01'),
(4, 'Sarah', 'Davis', 'IT', 85000, '2018-11-10'),
(5, 'David', 'Miller', 'IT', 79000, '2020-06-19'),
(6, 'Laura', 'Wilson', 'Marketing', 67000, '2022-02-28'),
(7, 'James', 'Moore', 'Sales', 61000, '2021-09-14'),
(8, 'Linda', 'Taylor', 'HR', 55000, '2020-12-01'),
(9, 'Robert', 'Anderson', 'IT', 92000, '2017-05-05'),
(10, 'Mary', 'Thomas', 'HR', 48000, '2023-01-20');

INSERT INTO products (product_id, product_name, category, price, stock_quantity) VALUES
(101, 'Laptop Pro', 'Electronics', 1200.00, 15),
(102, 'Wireless Mouse', 'Accessories', 25.50, 200),
(103, 'USB-C Hub', 'Accessories', 45.00, 0),
(104, 'Monitor 27"', 'Electronics', 350.00, 8),
(105, 'Desk Lamp', 'Furniture', 40.00, 45),
(106, 'Gaming Keyboard', 'Electronics', 95.00, 12),
(107, 'Office Chair', 'Furniture', 250.00, 5),
(108, 'HDMI Cable', 'Accessories', 15.00, 150),
(109, 'Smartphone X', 'Electronics', 999.00, 0),
(110, 'Notebook Pack', 'Office', 12.00, 300);

INSERT INTO customers (customer_id, first_name, last_name, city, state, signup_date) VALUES
(201, 'Alice', 'Walker', 'New York', 'NY', '2022-05-10'),
(202, 'Bob', 'Green', 'Los Angeles', 'CA', '2021-08-21'),
(203, 'Charlie', 'Adams', 'Chicago', 'IL', '2023-02-14'),
(204, 'Diana', 'Nelson', 'Houston', 'TX', '2020-11-01'),
(205, 'Ethan', 'Carter', 'Phoenix', 'AZ', '2019-07-19'),
(206, 'Fiona', 'Mitchell', 'New York', 'NY', '2022-12-05'),
(207, 'George', 'Perez', 'Los Angeles', 'CA', '2023-06-30'),
(208, 'Hannah', 'Roberts', 'Chicago', 'IL', '2021-04-17');

```

---

## 📝 PART 2: PRACTICE QUESTIONS + SOLUTIONS (Phase 2)

### SECTION A: AND, OR, NOT (Combining Conditions)

#### Q1. Select all employees who are in the `Sales` department AND earn more than `60000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department = 'Sales' AND salary > 60000;
```

</details>

---

#### Q2. Select all products from the `Accessories` category OR products with a price less than `20`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE category = 'Accessories' OR price < 20;
```

</details>

----
#### Q3. Select all customers who are **NOT** from `New York` city.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE NOT city = 'New York';
    -- OR: SELECT * FROM customers WHERE city != 'New York';
```
</details>

---
#### Q4. Select employees who are in `IT` **AND** (have a salary greater than `80000` **OR** were hired after `2020-01-01`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department = 'IT' AND 
        (salary > 80000 OR hire_date > '2020-01-01');
```
</details>

---
#### Q5. Select products that are **NOT** in the `Electronics` category **AND** have a stock quantity greater than `10`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE NOT category = 'Electronics' AND 
        stock_quantity > 10;
```
</details>

---
#### Q6. Select employees who are in HR OR Marketing, but NOT those with a salary above 70000.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE (department = 'HR' OR department = 'Marketing') AND 
        NOT salary > 70000;
```        
</details>

---
#### Q7. Select customers from `CA` **OR** `NY`, but **NOT** those who signed up after `2023-01-01`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE (state = 'CA' OR state = 'NY') AND 
        NOT signup_date > '2023-01-01';
```        
</details>

---

### SECTION B: IN Operator (Multiple Values)

---
#### Q8. Select all employees who work in `Sales`, `IT`, **or** `Marketing` (use IN).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department IN ('Sales', 'IT', 'Marketing');
```    
</details>

---
#### Q9. Select all products whose category is `Electronics` **or** `Furniture`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE category IN ('Electronics', 'Furniture');
```
</details>

---
#### Q10. Select all customers who live in `New York`, `Chicago`, **or** `Houston`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE city IN ('New York', 'Chicago', 'Houston');
```    
</details>

---
#### Q11. Select employees with employee IDs `1`, `5`, **and** `9` (use IN).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE employee_id IN (1, 5, 9);
```    
</details>

---
#### Q12. Select all products with prices `25.50`, `45.00`, or `999.00`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE price IN (25.50, 45.00, 999.00);
```    
</details>


---
#### Q13. Select all employees **NOT** in the `Sales` **or** `HR` departments.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE department NOT IN ('Sales', 'HR');
```    
</details>

---

### SECTION C: BETWEEN (Range Filtering)

---
#### Q14. Select employees with a salary between `60000` and `80000` (inclusive).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE salary BETWEEN 60000 AND 80000;
```    
</details>

---
#### Q15. Select products with a price between `20` and `100` (inclusive).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE price BETWEEN 20 AND 100;
```    
</details>

---
#### Q16. Select customers who signed up between `2021-01-01` **and** `2022-12-31`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE signup_date BETWEEN '2021-01-01' AND '2022-12-31';
```    
</details>


---
#### Q17. Select products with stock quantity between `10` and `100`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE stock_quantity BETWEEN 10 AND 100;
``` 
</details>

---
#### Q18. Select employees hired between `2019-01-01` and `2020-12-31`, **AND** with salary between `50000` and `70000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE hire_date BETWEEN '2019-01-01' AND '2020-12-31' 
    AND salary BETWEEN 50000 AND 70000;
```    
</details>

---
#### Q19. Select products **NOT** between price `100` and `500`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE price NOT BETWEEN 100 AND 500;
```    
</details>

---

### SECTION D: LIKE & Wildcards (Pattern Matching)


---
#### Q20. Select employees whose `first name` starts with `J`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE first_name LIKE 'J%';
```    
</details>

---
#### Q21. Select employees whose `last name` ends with `son`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE last_name LIKE '%son';
```    
</details>

---
#### Q22. Select customers whose `first name` contains `an`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE first_name LIKE '%an%';
```    
</details>

---
#### Q23. Select products whose `product name` starts with `Laptop`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE product_name LIKE 'Laptop%';
```    
</details>


---
#### Q24. Select employees whose `first name` has exactly `5` letters (use underscore _).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE first_name LIKE '_____';
```
</details>

--- 
#### Q25. Select employees whose `first name` is `4` letters long and `starts` with '`M`' (e.g., `Mary`, `Mark`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE first_name LIKE 'M___';
```    
</details>

---
#### Q26. Select products whose name has '`Book`' anywhere in it (case-sensitive depends on DB, but generally works).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE product_name LIKE '%Book%';
```    
</details>


---
#### Q27. Select customers whose `email` – wait, we don't have email column. Instead:

> Select customers whose last name has '`er`' as the 2nd and 3rd letters (e.g., Perez, Carter).

> **Pattern**: _er% (any char, then 'er', then anything).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE last_name LIKE '_er%';
```
</details>


---
#### Q28. Select all employees whose `first name` does **NOT** start with '`L`'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE first_name NOT LIKE 'L%';
```    
</details>

---
#### Q29. Select products whose category has exactly `10` characters (hint: __________ – 10 underscores).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE category LIKE '__________';
    -- Electronics (12 chars), Accessories (12), Furniture (9), Office (6). None? Actually 'Furniture' is 9, 'Office' is 6. So maybe 12 underscores for 'Accessories'.

    -- Let's do 12 underscores for 'Electronics' and 'Accessories'.
    SELECT * 
    FROM products 
    WHERE category LIKE '____________';
```    
</details>

---
#### Q30. Select employees whose `last name` contains '`a`' as the second character.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE last_name LIKE '_a%';
```    
</details>

---

### SECTION E: UPDATE (Modifying Data)

🛑 Remember to run the RESET script after these to restore data for later questions!

---
#### Q31. Give a `10%` salary raise to all employees in the `Sales` department.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE employees 
    SET salary = salary * 1.10 
    WHERE department = 'Sales';
    -- Check: SELECT * FROM employees WHERE department = 'Sales';
```
</details>

---
#### Q32. Update the `stock_quantity` of the `Wireless Mouse` to `250`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET stock_quantity = 250 
    WHERE product_name = 'Wireless Mouse';
```    
</details>

---
#### Q33. Change the city of customer Ethan Carter to `Scottsdale`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE customers 
    SET city = 'Scottsdale' 
    WHERE first_name = 'Ethan' AND last_name = 'Carter';
```    
</details>

---
#### Q34. Increase the `price` of all Accessories by `5%`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET price = price * 1.05 
    WHERE category = 'Accessories';
```    
</details>

---
#### Q35. Set the department of employee Mary Thomas to `Finance`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE employees 
    SET department = 'Finance' 
    WHERE first_name = 'Mary' AND last_name = 'Thomas';
```    
</details>

---
#### Q36. Reduce the price of all products by `10%` that currently have `0` stock.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET price = price * 0.90 
    WHERE stock_quantity = 0;
```    
</details>

---
#### Q37. Update the `signup_date` of all customers from `NY` to `'2024-01-01'`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE customers 
    SET signup_date = '2024-01-01' 
    WHERE state = 'NY';
```    
</details>

---
#### Q38. Give a flat `5000` bonus to all employees earning less than `60000`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE employees 
    SET salary = salary + 5000 
    WHERE salary < 60000;
```    
</details>

---
#### Q39. Update the `stock_quantity` of all Electronics to `20` (only if they are currently less than 20).

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET stock_quantity = 20 
    WHERE category = 'Electronics' AND 
        stock_quantity < 20;
```        
</details>

---

### SECTION F: DELETE (Removing Rows)

**🛑 Remember to run the RESET script after these!**

---
#### Q40. Delete all employees in the `HR` department.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM employees 
    WHERE department = 'HR';
```
</details>


---
#### Q41. Delete all products that have `0` stock quantity.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM products 
    WHERE stock_quantity = 0;
```    
</details>

---
#### Q42. Delete customers who signed up before `2020-01-01`.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM customers 
    WHERE signup_date < '2020-01-01';
```    
</details>

---
#### Q43. Delete employees who work in `IT` and earn less than `80000`.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM employees 
    WHERE department = 'IT' AND salary < 80000;
```    
</details>


---
#### Q44. Delete all products where the category is `Office` **OR** `price` is greater than `1000`.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM products 
    WHERE category = 'Office' OR price > 1000;
```
</details>

---
#### Q45. Delete customers whose city is `Chicago` and state is `IL`.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM customers 
    WHERE city = 'Chicago' AND state = 'IL';
```    
</details>


---
#### Q46. Delete all employees whose `first_name` starts with '`L`' (Laura and Linda).

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM employees 
    WHERE first_name LIKE 'L%';
```    
</details>

---

### SECTION G: TRUNCATE (Removing All Rows Quickly)

**⚠️ TRUNCATE removes ALL rows from a table and resets auto-increment (if any). It cannot be rolled back in many databases. Always run the RESET script afterward!**

---
#### Q47. Delete all rows from the products table using `TRUNCATE`.

<details> <summary>Click to reveal answer</summary>

```sql
    TRUNCATE TABLE products;
    -- Now SELECT * FROM products; will return empty.
    -- Run the reset script to repopulate.
```    
</details>

---
#### Q48. Delete all rows from the customers table using `TRUNCATE`.

<details> <summary>Click to reveal answer</summary>

```sql
    TRUNCATE TABLE customers;
```    
</details>

---
#### Q49. Empty the employees table using `TRUNCATE`.

<details> <summary>Click to reveal answer</summary>

```sql
    TRUNCATE TABLE employees;
```    
</details>

---


### SECTION H: Mixed Scenarios (Combining Everything)


---
#### Q50. Select all products where the `product_name` contains the word `Pro` **OR** the `price` is between `200` and `1000`, and sort them by price `descending`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * FROM products 
    WHERE product_name LIKE '%Pro%' OR 
        price BETWEEN 200 AND 1000 
    ORDER BY price DESC;
```    
</details>

---
#### Q51. Give a `15%` salary increase to all `IT` employees, but only if they earn less than `85000`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE employees 
    SET salary = salary * 1.15 
    WHERE department = 'IT' AND salary < 85000;
```    
</details>

---
#### Q52. Delete all products whose `product_name` starts with `USB` **AND** have a price less than `50`.

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM products 
    WHERE product_name LIKE 'USB%' AND price < 50;
```    
</details>

---
#### Q53. Select all customers whose state is `CA` or `NY`, whose city does **NOT** start with `L`, and sort them by `signup_date` (oldest first).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE state IN ('CA', 'NY') AND city NOT LIKE 'L%' 
    ORDER BY signup_date ASC;
```    
</details>

---
#### Q54. Update the `category` of all products with a price above `500` to Premium Electronics.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET category = 'Premium Electronics' WHERE price > 500;
```    
</details>

---
#### Q55. Delete all employees `hired` in the year `2021` (hint: hire_date BETWEEN '2021-01-01' AND '2021-12-31').

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM employees 
    WHERE hire_date BETWEEN '2021-01-01' AND '2021-12-31';
```    
</details>

--- 
#### Q56. Select distinct `departments` from the employees table, but only for departments where the employee's `last name` contains the letter `r` (using LIKE).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT DISTINCT department 
    FROM employees 
    WHERE last_name LIKE '%r%';
```    
</details>

 
---
#### Q57. Increase the stock of all products in the Accessories category by `50` units, but only if the current stock is less than `100`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET stock_quantity = stock_quantity + 50 
    WHERE category = 'Accessories' AND stock_quantity < 100;
```    
</details>

---
#### Q58. Delete customers whose `signup_date` is in the year `2022` (hint: signup_date BETWEEN '2022-01-01' AND '2022-12-31').

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM customers 
    WHERE signup_date 
    BETWEEN '2022-01-01' AND '2022-12-31';
```    
</details>

---
#### Q59. Update the `salary` of all `Marketing` employees to be exactly `75000`.

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE employees 
    SET salary = 75000 
    WHERE department = 'Marketing';
```    
</details>

---
#### Q60. Select all products where the `product_name` has exactly `10` characters (including spaces) using `LIKE` with `underscores`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM products 
    WHERE product_name LIKE '__________';
    -- That's 10 underscores. 'Desk Lamp' is 9 (space counts), 'HDMI Cable' is 10 (space counts). So it will work.
```    
</details>

---
### 🎯 BONUS: Complex UPDATE with WHERE + LIKE + IN
---

#### Q61. Add a $`20` surcharge to all products whose category is `Furniture` **OR** whose name ends with `X` (like Smartphone X).

<details> <summary>Click to reveal answer</summary>

```sql
    UPDATE products 
    SET price = price + 20 
    WHERE category = 'Furniture' OR product_name LIKE '%X';
```    
</details>

---
#### Q62. Delete all employees whose `first name` ends with `h` **AND** whose `salary` is greater than `60000` **OR** whose department is `HR` (be careful with parentheses!).

<details> <summary>Click to reveal answer</summary>

```sql
    DELETE FROM employees 
    WHERE (first_name LIKE '%h' AND salary > 60000) OR 
        department = 'HR';
```        
</details>
 
---

## 📌 Final Pro-Tips:

* **Always** use a `SELECT` with your `WHERE` clause first to verify which rows will be affected before running an `UPDATE` or `DELETE`.

* For `TRUNCATE`, remember it's faster but resets auto-increment and cannot be filtered (it deletes everything).

---
<br/><br/><br/><br/>

#### Happy Practicing! 😊✨

<br/><br/><br/><br/>
---

Excellent! Let's power through Phase 3. We'll use the same `employees`, `products`, and `customers` tables.

Since we're working with Functions, the data won't be permanently changed (except we might use `UPDATE` with functions, but we'll mostly `SELECT`). Still, I recommend running the reset script from Phase 2 once at the start just to be safe.

---

## 🛠️ Quick Reset (Run once to ensure data is correct)


```sql

    TRUNCATE TABLE employees;
    TRUNCATE TABLE products;
    TRUNCATE TABLE customers;

    INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date) VALUES
    (1, 'John', 'Smith', 'Sales', 65000, '2020-01-15'),
    (2, 'Emma', 'Johnson', 'Marketing', 72000, '2019-03-22'),
    (3, 'Michael', 'Brown', 'Sales', 58000, '2021-07-01'),
    (4, 'Sarah', 'Davis', 'IT', 85000, '2018-11-10'),
    (5, 'David', 'Miller', 'IT', 79000, '2020-06-19'),
    (6, 'Laura', 'Wilson', 'Marketing', 67000, '2022-02-28'),
    (7, 'James', 'Moore', 'Sales', 61000, '2021-09-14'),
    (8, 'Linda', 'Taylor', 'HR', 55000, '2020-12-01'),
    (9, 'Robert', 'Anderson', 'IT', 92000, '2017-05-05'),
    (10, 'Mary', 'Thomas', 'HR', 48000, '2023-01-20');

    INSERT INTO products (product_id, product_name, category, price, stock_quantity) VALUES
    (101, 'Laptop Pro', 'Electronics', 1200.00, 15),
    (102, 'Wireless Mouse', 'Accessories', 25.50, 200),
    (103, 'USB-C Hub', 'Accessories', 45.00, 0),
    (104, 'Monitor 27"', 'Electronics', 350.00, 8),
    (105, 'Desk Lamp', 'Furniture', 40.00, 45),
    (106, 'Gaming Keyboard', 'Electronics', 95.00, 12),
    (107, 'Office Chair', 'Furniture', 250.00, 5),
    (108, 'HDMI Cable', 'Accessories', 15.00, 150),
    (109, 'Smartphone X', 'Electronics', 999.00, 0),
    (110, 'Notebook Pack', 'Office', 12.00, 300);

    INSERT INTO customers (customer_id, first_name, last_name, city, state, signup_date) VALUES
    (201, 'Alice', 'Walker', 'New York', 'NY', '2022-05-10'),
    (202, 'Bob', 'Green', 'Los Angeles', 'CA', '2021-08-21'),
    (203, 'Charlie', 'Adams', 'Chicago', 'IL', '2023-02-14'),
    (204, 'Diana', 'Nelson', 'Houston', 'TX', '2020-11-01'),
    (205, 'Ethan', 'Carter', 'Phoenix', 'AZ', '2019-07-19'),
    (206, 'Fiona', 'Mitchell', 'New York', 'NY', '2022-12-05'),
    (207, 'George', 'Perez', 'Los Angeles', 'CA', '2023-06-30'),
    (208, 'Hannah', 'Roberts', 'Chicago', 'IL', '2021-04-17');

```

## 📝 PART 3: PRACTICE QUESTIONS + SOLUTIONS (Phase 3)


### SECTION A: String Functions (`CONCAT`, `UPPER`, `LOWER`, `LENGTH`, `SUBSTRING`, `REPLACE`, `LEFT`, `RIGHT`, `TRIM`)

---

#### Q1. Show the full name of each employee as one column (e.g., "John Smith") using CONCAT.

<details> <summary>Click to reveal answer</summary>

```sql

    SELECT CONCAT(first_name, ' ', last_name) AS full_name 
    FROM employees;
```    

</details>

---

#### Q2. Show all product names in UPPERCASE.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT UPPER(product_name) AS product_upper 
    FROM products;
```    
</details>


---
#### Q3. Show all customer cities in lowercase.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT LOWER(city) AS city_lower 
    FROM customers;
```    
</details>

---
#### Q4. Find the length (number of characters) of each employee's last name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        last_name, 
        LENGTH(last_name) AS name_length 
    FROM employees;
```    
</details>

---
#### Q5. Extract the first 3 characters of every product name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        LEFT(product_name, 3) AS first_3 
    FROM products;
```    
</details>

---
#### Q6. Extract the last 4 characters of every customer's first name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        RIGHT(first_name, 4) AS last_4 
    FROM customers;
```    
</details>

---
#### Q7. Show a substring of the `product_name` starting from position 1, length 5 (e.g., "Lapto", "Wirel").

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        SUBSTRING(product_name, 1, 5) AS sub_name
    FROM products;
```    
</details>

---
#### Q8. Replace the word `Pro` with `Premium` in all product names.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        REPLACE(product_name, 'Pro', 'Premium') AS updated_name 
    FROM products;
```    
</details>

---
#### Q9. Show the full name of each customer (first + last) in uppercase.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CONCAT(UPPER(first_name), ' ', UPPER(last_name)) AS full_upper 
    FROM customers;
```    
</details>

---
#### Q10. Count how many characters are in each product's `category` and show it alongside the category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        LENGTH(category) AS category_length 
    FROM products;
```        
</details>

---
#### Q11. Show the first 4 letters of each employee's `department` and the last 4 letters of their `last_name`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        LEFT(department, 4) AS dept_prefix, last_name, 
        RIGHT(last_name, 4) AS name_suffix 
    FROM employees;
```    
</details>

---
#### Q12. Create a new column called `email_username` that combines the first letter of `first_name` and the entire `last_name` (e.g., JSmith).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        CONCAT(LEFT(first_name, 1), last_name) AS email_username 
    FROM employees;
```    
</details>

---
### SECTION B: Numeric Functions (`ROUND`, `CEILING`, `FLOOR`, `ABS`, `MOD`)

---
#### Q13. Show the `price` of all products, rounded to the nearest whole number.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, 
        ROUND(price) AS rounded_price 
    FROM products;
```
</details>


---
#### Q14. Round the `price` to 1 decimal place.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, 
        ROUND(price, 1) AS price_1dec 
    FROM products;
```    
</details>

---
#### Q15. Use `CEILING` to round all product prices up to the next whole number.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, 
        CEILING(price) AS ceil_price 
    FROM products;
```    
</details>

---
#### Q16. Use `FLOOR` to round all product prices down to the previous whole number.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, 
        FLOOR(price) AS floor_price 
    FROM products;
```    
</details>

---
#### Q17. Calculate the absolute difference between `salary` and `70000` for each employee (use `ABS`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        salary, 
        ABS(salary - 70000) AS diff_from_70k 
    FROM employees;
```    
</details>

---
#### Q18. Find the remainder (modulo) when `stock_quantity` is divided by `10` (use `MOD`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        stock_quantity, 
        MOD(stock_quantity, 10) AS remainder 
    FROM products;
```    
</details>

---
#### Q19. Calculate the total value of inventory for each product (price * stock_quantity) and round it to 2 decimal places.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        ROUND(price * stock_quantity, 2) AS inventory_value 
    FROM products;
```    
</details>


---
#### Q20. Show the `salary` divided by `12` (monthly salary), rounded to the nearest integer.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        salary, 
        ROUND(salary / 12) AS monthly_salary 
    FROM employees;
```    
</details>

---
#### Q21. Use CEILING on the average of price and stock_quantity for each product (just for practice).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        CEILING((price + stock_quantity) / 2) AS ceil_avg 
    FROM products;
```    
</details>

---

### SECTION C: Date Functions (`YEAR`, `MONTH`, `DAY`, `CURDATE`, `DATEDIFF`, `DATE_ADD`, `NOW`)

---
#### Q22. Extract the `YEAR` from the `hire_date` of each employee.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        YEAR(hire_date) AS hire_year 
    FROM employees;
```    
</details>

---
#### Q23. Extract the `MONTH` (as a number) from the `signup_date` of each customer.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        MONTH(signup_date) AS signup_month 
    FROM customers;
```    
</details>


---
#### Q25. Calculate how many days each employee has been working at the company (from `hire_date` to today's date). Use `DATEDIFF` and `CURDATE()`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        DATEDIFF(CURDATE(), hire_date) AS days_employed 
    FROM employees;
```    
</details>

---
#### Q26. Calculate how many years ago each customer signed up (approximate, using `DATEDIFF` / 365).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        ROUND(DATEDIFF(CURDATE(), signup_date) / 365, 1) AS years_ago 
    FROM customers;
```    
</details>


---
#### Q27. Add 1 year to the `hire_date` of each employee (use `DATE_ADD`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        DATE_ADD(hire_date, INTERVAL 1 YEAR) AS one_year_later 
    FROM employees;
```    
</details>

---
#### Q28. Add 30 days to the `signup_date` of each customer.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        DATE_ADD(signup_date, INTERVAL 30 DAY) AS plus_30_days 
    FROM customers;
```    
</details>

---
#### Q29. Show the current date and time using `NOW()`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT NOW() AS current_datetime;
```    
</details>

---
#### Q30. Show only the `YEAR` and `MONTH` of each `signup_date` in a single column (e.g., "2022-05").

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        CONCAT(YEAR(signup_date), '-', LPAD(MONTH(signup_date), 2, '0')) AS year_month 
    FROM customers;
    -- Note: LPAD is a string function to ensure 2 digits.
```    
</details>

---
#### Q31. Find employees hired in the month of `January` (month = 1).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE MONTH(hire_date) = 1;
```    
</details>

---
#### Q32. Find customers who signed up on a day between 1 and 15 of any month.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE DAY(signup_date) BETWEEN 1 AND 15;
```    
</details>

---

### SECTION D: Aggregate Functions (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`)

---
#### Q22. Extract the `YEAR` from the `hire_date` of each employee.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        YEAR(hire_date) AS hire_year 
    FROM employees;
```    
</details>

---
#### Q23. Extract the `MONTH` (as a number) from the `signup_date` of each customer.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        MONTH(signup_date) AS signup_month 
    FROM customers;
```    
</details>


---
#### Q24. Extract the `DAY` from the `hire_date` of each employee.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        DAY(hire_date) AS hire_day 
    FROM employees;
```    
</details>

---
#### Q25. Calculate how many days each employee has been working at the company (from `hire_date` to today's date). Use `DATEDIFF` and `CURDATE()`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        DATEDIFF(CURDATE(), hire_date) AS days_employed 
    FROM employees;
```    
</details>

---
#### Q26. Calculate how many years ago each customer signed up (approximate, using `DATEDIFF` / 365).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        ROUND(DATEDIFF(CURDATE(), signup_date) / 365, 1) AS years_ago 
    FROM customers;
```    
</details>

---
#### Q27. Add 1 year to the `hire_date` of each employee (use `DATE_ADD`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        DATE_ADD(hire_date, INTERVAL 1 YEAR) AS one_year_later 
    FROM employees;
```    
</details>


---
#### Q28. Add 30 days to the `signup_date` of each customer.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date, 
        DATE_ADD(signup_date, INTERVAL 30 DAY) AS plus_30_days 
    FROM customers;
```    
</details>

---
#### Q29. Show the current date and time using `NOW()`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT NOW() AS current_datetime;
```    
</details>

---
#### Q30. Show only the `YEAR` and `MONTH` of each `signup_date` in a single column (e.g., "2022-05").

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        CONCAT(YEAR(signup_date), '-', LPAD(MONTH(signup_date), 2, '0')) AS year_month 
    FROM customers;
    
    -- Note: LPAD is a string function to ensure 2 digits.
```    
</details>

---
#### Q31. Find employees hired in the month of `January` (month = 1).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM employees 
    WHERE MONTH(hire_date) = 1;
```    
</details>

---
#### Q32. Find customers who signed up on a day between 1 and 15 of any month.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT * 
    FROM customers 
    WHERE DAY(signup_date) BETWEEN 1 AND 15;
```    
</details>

---

### SECTION D: Aggregate Functions (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`)

---
#### Q33. Count the total number of employees in the company.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS total_employees 
    FROM employees;
```    
</details>

---
#### Q34. Count the total number of distinct departments in the company.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(DISTINCT department) AS distinct_depts 
    FROM employees;
```    
</details>

---
#### Q35. Calculate the total sum of all employee salaries (total payroll).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(salary) AS total_payroll 
    FROM employees;
```    
</details>

---
#### Q35. Calculate the total sum of all employee salaries (total payroll).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(salary) AS total_payroll 
    FROM employees;
```    
</details>


---
#### Q36. Calculate the average salary of all employees.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(salary) AS avg_salary 
    FROM employees;
```    
</details>

---
#### Q37. Find the highest salary in the company.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MAX(salary) AS highest_salary 
    FROM employees;
```    
</details>


---
#### Q38. Find the lowest salary in the company.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MIN(salary) AS lowest_salary 
    FROM employees;
```    
</details>

---
#### Q39. Count the number of products in the `products` table.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS product_count 
    FROM products;
```        
</details>

---
#### Q40. Find the total value of all products in stock (sum of `price * stock_quantity`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(price * stock_quantity) AS total_inventory_value 
    FROM products;
```    
</details>

---
#### Q41. Find the average price of all products.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(price) AS avg_price 
    FROM products;
```    
</details>

---
#### Q42. Find the most expensive product price.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MAX(price) AS max_price 
    FROM products;
```    
</details>

---
#### Q43. Find the cheapest product price.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MIN(price) AS min_price 
    FROM products;
```    
</details>

---
#### Q44. Count the total number of customers.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS customer_count 
    FROM customers;
```    
</details>

---
#### Q45. Find the earliest signup date among customers.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MIN(signup_date) AS earliest_signup 
    FROM customers;
```    
</details>

---
#### Q46. Find the most recent signup date among customers.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MAX(signup_date) AS latest_signup 
    FROM customers;
```    
</details>


---
#### Q47. Count how many employees work in the IT department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS it_count 
    FROM employees 
    WHERE department = 'IT';
```    
</details>


---
#### Q48. Calculate the total salary paid to `Sales` employees.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(salary) AS sales_payroll 
    FROM employees 
    WHERE department = 'Sales';
```    
</details>


---
#### Q49. Find the average salary of employees in the `Marketing` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(salary) AS marketing_avg 
    FROM employees 
    WHERE department = 'Marketing';
```    
</details>

---
#### Q50. Find the highest salary in the `HR` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT MAX(salary) AS hr_max 
    FROM employees 
    WHERE department = 'HR';
```    
</details>


---
#### Q51. Count the number of products that have `0` stock.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS out_of_stock 
    FROM products 
    WHERE stock_quantity = 0;
```    
</details>


---
#### Q52. Find the total stock quantity of all products combined.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(stock_quantity) AS total_stock 
    FROM products;
```    
</details>

---

### SECTION E: Mixing Functions (Combining Everything)

---
#### Q53. Show the full name of each employee (in uppercase) and the length of their full name.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CONCAT(UPPER(first_name), ' ', UPPER(last_name)) AS full_upper,
        LENGTH(CONCAT(first_name, ' ', last_name)) AS full_length 
    FROM employees;
```    
</details>

---
#### Q54. Find the average length of all product names.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(LENGTH(product_name)) AS avg_name_length 
    FROM products;
```    
</details>

---
#### Q55. Show the minimum, maximum, and average salary, and round the average to 2 decimal places.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        MIN(salary) AS min_sal, 
        MAX(salary) AS max_sal, 
        ROUND(AVG(salary), 2) AS avg_sal 
    FROM employees;
```     
</details>

---
#### Q56. Count the number of employees hired in each year?
**Wait** – that needs GROUP BY, which is not explicitly in the list. Let's avoid it.
Instead: Count employees hired in 2020 specifically.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS hired_in_2020 
    FROM employees 
    WHERE YEAR(hire_date) = 2020;
```    
</details>

---
#### Q57. Calculate the total salary paid to all employees, but only for employees whose first name starts with J or M.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(salary) AS total_j_m_salaries 
    FROM employees 
    WHERE first_name LIKE 'J%' OR first_name LIKE 'M%';
```    
</details>

---
#### Q58. Find the average price of products in the `Electronics` and `Furniture` categories combined.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(price) AS avg_electronics_furniture 
    FROM products 
    WHERE category IN ('Electronics', 'Furniture');
```    
</details>

---
#### Q59. Show the earliest and latest `hire_date` for the `IT` department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        MIN(hire_date) AS earliest_hire, 
        MAX(hire_date) AS latest_hire 
    FROM employees 
    WHERE department = 'IT';
```    
</details>

---
#### Q60. Count how many customers have a `last_name` that contains the letter `e` (case-insensitive, use `LIKE`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS last_name_has_e 
    FROM customers 
    WHERE last_name LIKE '%e%';
```    
</details>

---
#### Q61. Calculate the total stock value (`price * stock_quantity`) for all products in the `Accessories` category, and round the result to 2 decimals.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT ROUND(SUM(price * stock_quantity), 2) AS accessories_value 
    FROM products 
    WHERE category = 'Accessories';
```    
</details>


---
#### Q62. Show the employee `first_name`, their `salary`, and the `salary` divided by the `LENGTH` of their `last_name`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        last_name, 
        salary, 
        ROUND(salary / LENGTH(last_name), 2) AS salary_per_char 
    FROM employees;
```    
</details>


---
#### Q63. Find the total number of characters in all product names combined (sum of lengths).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT SUM(LENGTH(product_name)) AS total_name_length 
    FROM products;
```    
</details>


---
#### Q64. Show the `product_name`, `price`, and the price rounded up (`CEILING`) and rounded down (`FLOOR`), all in one query.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, 
        CEILING(price) AS ceil_price, 
        FLOOR(price) AS floor_price 
    FROM products;
```    
</details>

---
#### Q65. Find the average stock quantity, but only for products that have a price greater than `50`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT AVG(stock_quantity) AS avg_stock_high_price 
    FROM products 
    WHERE price > 50;
```    
</details>

---
#### Q66. Calculate how many months (rounded) each employee has been with the company, using `DATEDIFF` and dividing by 30.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        hire_date, 
        ROUND(DATEDIFF(CURDATE(), hire_date) / 30, 0) AS months_employed 
    FROM employees;
```    
</details>


---
#### Q67. Show the minimum and maximum stock quantity, and the difference between them.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        MIN(stock_quantity) AS min_stock, 
        MAX(stock_quantity) AS max_stock, 
        MAX(stock_quantity) - MIN(stock_quantity) AS difference 
    FROM products;
```    
</details>

---
#### Q68. Count the total number of employees, the total salary sum, and the average salary – all with descriptive column aliases.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        COUNT(*) AS total_emps, 
        SUM(salary) AS total_payroll, 
        ROUND(AVG(salary), 2) AS avg_salary 
    FROM employees;
```    
</details>

---
#### Q69. Find the most recent `hire_date` and the oldest `hire_date` overall.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        MAX(hire_date) AS latest_hire, 
        MIN(hire_date) AS earliest_hire 
    FROM employees;
```    
</details>

---
#### Q70. Show the product name and price, but for the price, show its absolute difference from `500` (use `ABS`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price, ABS(price - 500) AS diff_from_500 
    FROM products;
```    
</details>

---

### 🎯 BONUS: Complex Expressions with Multiple Functions

---
#### Q71. Show the full name of each employee (e.g., "John Smith"), the year they were hired, and how many characters are in their full name, but only for those hired after 2019.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CONCAT(first_name, ' ', last_name) AS full_name, 
        YEAR(hire_date) AS hire_year, 
        LENGTH(CONCAT(first_name, ' ', last_name)) AS name_length 
    FROM employees 
    WHERE YEAR(hire_date) > 2019;
```    
</details>

---
#### Q72. Calculate the total payroll for employees whose `first_name` ends with the letter `h`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        SUM(salary) AS total_h_ending_salaries 
    FROM employees 
    WHERE first_name LIKE '%h';
```    
</details>

---
#### Q73. Find the average price of all products, but round it to the nearest integer, and also find the ceiling and floor of that average.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        ROUND(AVG(price)) AS avg_rounded, 
        CEILING(AVG(price)) AS avg_ceil, 
        FLOOR(AVG(price)) AS avg_floor 
    FROM products;
```    
</details>


---
#### Q74. Show the `product_name` and the `stock_quantity` in a formatted string: "Product [name] has [qty] units." (use `CONCAT`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CONCAT('Product ', product_name, ' has ', stock_quantity, ' units.') AS stock_report 
    FROM products;
```    
</details>

---
#### Q75. Count the number of customers who signed up in the year `2022`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT COUNT(*) AS signups_2022 
    FROM customers 
    WHERE YEAR(signup_date) = 2022;
```    
</details>


---
<br/><br/><br/><br/>

#### Happy Practicing! 😊✨

<br/><br/><br/><br/>
---

Perfect! Let's tackle Phase 4. We'll use the same `employees`, `products`, and `customers` tables.

Since we're grouping and analyzing, the data stays unchanged. Run the reset script once to ensure a clean slate.

---

## 🛠️ Quick Reset (Run this once to start fresh)

```sql

    TRUNCATE TABLE employees;
    TRUNCATE TABLE products;
    TRUNCATE TABLE customers;

    INSERT INTO employees (employee_id, first_name, last_name, department, salary, hire_date) VALUES
    (1, 'John', 'Smith', 'Sales', 65000, '2020-01-15'),
    (2, 'Emma', 'Johnson', 'Marketing', 72000, '2019-03-22'),
    (3, 'Michael', 'Brown', 'Sales', 58000, '2021-07-01'),
    (4, 'Sarah', 'Davis', 'IT', 85000, '2018-11-10'),
    (5, 'David', 'Miller', 'IT', 79000, '2020-06-19'),
    (6, 'Laura', 'Wilson', 'Marketing', 67000, '2022-02-28'),
    (7, 'James', 'Moore', 'Sales', 61000, '2021-09-14'),
    (8, 'Linda', 'Taylor', 'HR', 55000, '2020-12-01'),
    (9, 'Robert', 'Anderson', 'IT', 92000, '2017-05-05'),
    (10, 'Mary', 'Thomas', 'HR', 48000, '2023-01-20');

    INSERT INTO products (product_id, product_name, category, price, stock_quantity) VALUES
    (101, 'Laptop Pro', 'Electronics', 1200.00, 15),
    (102, 'Wireless Mouse', 'Accessories', 25.50, 200),
    (103, 'USB-C Hub', 'Accessories', 45.00, 0),
    (104, 'Monitor 27"', 'Electronics', 350.00, 8),
    (105, 'Desk Lamp', 'Furniture', 40.00, 45),
    (106, 'Gaming Keyboard', 'Electronics', 95.00, 12),
    (107, 'Office Chair', 'Furniture', 250.00, 5),
    (108, 'HDMI Cable', 'Accessories', 15.00, 150),
    (109, 'Smartphone X', 'Electronics', 999.00, 0),
    (110, 'Notebook Pack', 'Office', 12.00, 300);

    INSERT INTO customers (customer_id, first_name, last_name, city, state, signup_date) VALUES
    (201, 'Alice', 'Walker', 'New York', 'NY', '2022-05-10'),
    (202, 'Bob', 'Green', 'Los Angeles', 'CA', '2021-08-21'),
    (203, 'Charlie', 'Adams', 'Chicago', 'IL', '2023-02-14'),
    (204, 'Diana', 'Nelson', 'Houston', 'TX', '2020-11-01'),
    (205, 'Ethan', 'Carter', 'Phoenix', 'AZ', '2019-07-19'),
    (206, 'Fiona', 'Mitchell', 'New York', 'NY', '2022-12-05'),
    (207, 'George', 'Perez', 'Los Angeles', 'CA', '2023-06-30'),
    (208, 'Hannah', 'Roberts', 'Chicago', 'IL', '2021-04-17');

```

## 📝 PART 4: PRACTICE QUESTIONS + SOLUTIONS (Phase 4)


### SECTION A: GROUP BY (Single Column)

#### Q1. Count the number of employees in each department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        COUNT(*) AS employee_count 
    FROM employees 
    GROUP BY department;
```    
</details>

---
#### Q2. Calculate the total salary paid to each department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        SUM(salary) AS total_salary 
    FROM employees 
    GROUP BY department;
```    
</details>

---
#### Q3. Find the average salary for each department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        AVG(salary) AS avg_salary 
    FROM employees 
    GROUP BY department;
```    
</details>

---
#### Q4. Count the number of products in each category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        COUNT(*) AS product_count 
    FROM products 
    GROUP BY category;
```    
</details>

---
#### Q5. Calculate the total stock quantity for each product category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        SUM(stock_quantity) AS total_stock 
    FROM products 
    GROUP BY category;
```    
</details>

---
#### Q6. Find the average price of products in each category.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        AVG(price) AS avg_price 
    FROM products 
    GROUP BY category;
```    
</details>

---
#### Q7. Count the number of customers in each state.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state, 
        COUNT(*) AS customer_count 
    FROM customers 
    GROUP BY state;
```    
</details>

---
#### Q8. Find the earliest signup date for each state.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state, 
        MIN(signup_date) AS earliest_signup 
    FROM customers 
    GROUP BY state;
```    
</details>

---
#### Q9. Find the highest salary in each department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        MAX(salary) AS highest_salary 
    FROM employees 
    GROUP BY department;
```    
</details>

---
#### Q10. Find the lowest salary in each department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        MIN(salary) AS lowest_salary 
    FROM employees 
    GROUP BY department;
```    
</details>

---

### SECTION B: GROUP BY (Multiple Columns)

---
#### Q11. Count the number of employees grouped by both `department` and `hire_date` year (use `YEAR(hire_date)`).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        YEAR(hire_date) AS hire_year, 
        COUNT(*) AS employee_count 
    FROM employees 
    GROUP BY 
        department, 
        YEAR(hire_date);
```        
</details>


---
#### Q12. Group products by `category` and `stock_quantity` status (in stock vs out of stock). Count how many products fall into each group.

> (Hint: Create a derived column in GROUP BY – but GROUP BY can take expressions. We'll use CASE later, but for now, group by stock_quantity = 0? Actually, GROUP BY doesn't allow boolean directly in all DBs. Let's just group by category and stock_quantity integer.)

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        stock_quantity, 
        COUNT(*) AS product_count 
    FROM products 
    GROUP BY 
        category, 
        stock_quantity;
```    
</details>

---
#### Q12b. (Better question): Group customers by state and city, and count how many in each combination.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state, 
        city, 
        COUNT(*) AS customer_count 
    FROM customers 
    GROUP BY state, city;
```    
</details>

---
#### Q13. Calculate the total salary paid by each department and for each year of hire.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        YEAR(hire_date) AS hire_year, 
        SUM(salary) AS total_salary 
    FROM employees 
    GROUP BY 
        department, 
        YEAR(hire_date);
```        
</details>

---
#### Q14. Group products by category and price range (e.g., price < 50, 50-200, >200).
> Wait – this requires CASE. We'll save it for the CASE section.

---

### SECTION C: HAVING (Filtering Groups)

---
#### Q15. Find departments that have more than `2` employees.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        COUNT(*) AS employee_count 
    FROM employees 
    GROUP BY department 
    HAVING COUNT(*) > 2;
```    
</details>

---
#### Q16. Find departments with an average salary greater than `65000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        AVG(salary) AS avg_salary 
    FROM employees 
    GROUP BY department 
    HAVING AVG(salary) > 65000;
```    
</details>


---
#### Q17. Find product categories that have a total stock quantity of more than `100`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        SUM(stock_quantity) AS total_stock 
    FROM products 
    GROUP BY category 
    HAVING SUM(stock_quantity) > 100;
```    
</details>

---
#### Q18. Find product categories with an average price less than `100`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        AVG(price) AS avg_price 
    FROM products 
    GROUP BY category 
    HAVING AVG(price) < 100;
```    
</details>

---
#### Q19. Find states that have at least `2` customers.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state, 
        COUNT(*) AS customer_count 
    FROM customers 
    GROUP BY state 
    HAVING COUNT(*) >= 2;
```    
</details>

---
#### Q20. Find departments where the total salary is greater than `120000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        SUM(salary) AS total_salary 
    FROM employees 
    GROUP BY department 
    HAVING SUM(salary) > 120000;
```    
</details>

---
#### Q21. Find departments where the highest salary is at least `85000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        MAX(salary) AS max_salary 
    FROM employees 
    GROUP BY department 
    HAVING MAX(salary) >= 85000;
```    
</details>

---
#### Q22. Find categories where the minimum price is less than `20`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        MIN(price) AS min_price 
    FROM products 
    GROUP BY category 
    HAVING MIN(price) < 20;
```    
</details>

---
#### Q23. Find categories that have exactly `2` products.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category, 
        COUNT(*) AS product_count 
    FROM products 
    GROUP BY category 
    HAVING COUNT(*) = 2;
```    
</details>

---
#### Q24. Find states where the total number of customers is less than `3`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT state, COUNT(*) AS customer_count 
    FROM customers 
    GROUP BY state 
    HAVING COUNT(*) < 3;
```    
</details>

---
#### Q25. Find departments where the average salary is between `60000` and `80000`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        AVG(salary) AS avg_salary 
    FROM employees 
    GROUP BY department 
    HAVING AVG(salary) BETWEEN 60000 AND 80000;
```    
</details>

---

### SECTION D: Aliases (Column & Table Aliases)

---
#### Q26. Write a query that shows `department` and total salary, but use alias `dept` and `total_pay` for the columns.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department AS dept, 
        SUM(salary) AS total_pay 
    FROM employees 
    GROUP BY department;
```    
</details>


---
#### Q27. Using a table alias (`e`), select all employees from the `employees` table, filtering by `department = 'IT'`. Show `e.first_name` and `e.salary`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        e.first_name, 
        e.salary 
    FROM employees AS e 
    WHERE e.department = 'IT';
```    
</details>

---
#### Q28. Write a GROUP BY query that uses column aliases in the `HAVING` clause.
> (Note: In most SQL dialects, you cannot use column aliases in HAVING directly – you have to repeat the expression. But we can show the alias in SELECT.)

> Show department and count, with alias emp_count, and filter to count > 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        COUNT(*) AS emp_count 
    FROM employees 
    GROUP BY department 
    HAVING COUNT(*) > 2;  -- can't use emp_count here in most SQL
    -- But in MySQL, you can use emp_count in HAVING. For portability, we use COUNT(*).
```    
</details>

---
#### Q29. Give aliases to aggregated columns in a single query: `total_employees`, `total_salary`, `average_salary`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        COUNT(*) AS total_employees,
        SUM(salary) AS total_salary,
        AVG(salary) AS average_salary
    FROM employees;
```    
</details>

---
#### Q30. Use a table alias for `products` and calculate the total value of stock (`price * stock_quantity`) per category, aliasing the sum as `inventory_value`.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        p.category, 
        SUM(p.price * p.stock_quantity) AS inventory_value 
    FROM products AS p 
    GROUP BY p.category;
```    
</details>

---
#### Q31. Write a query that selects `customer_id`, `first_name`, and `signup_date`, and aliases the `signup_date` as `joined`, then sort by `joined` descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        customer_id, 
        first_name, 
        signup_date AS joined 
    FROM customers 
    ORDER BY joined DESC;
```    
</details>

---

### SECTION E: CASE Statements (Simple & Searched)

---
#### Q32. Create a new column called `salary_grade` that labels employees as:

* 'High' if salary >= 80000

* 'Medium' if salary between 50000 and 79999

* 'Low' if salary < 50000

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        salary,
        CASE 
            WHEN salary >= 80000 THEN 'High'
            WHEN salary >= 50000 AND salary < 80000 THEN 'Medium'
            ELSE 'Low'
        END AS salary_grade
    FROM employees;
```    
</details>

---
#### Q33. Using CASE, create a column `price_range` for products:

* 'Expensive' if price > 500

* 'Moderate' if price between 50 and 500

* 'Cheap' if price < 50

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name, 
        price,
        CASE 
            WHEN price > 500 THEN 'Expensive'
            WHEN price BETWEEN 50 AND 500 THEN 'Moderate'
            ELSE 'Cheap'
        END AS price_range
    FROM products;
```    
</details>

---
#### Q34. Use CASE to categorize customers by the year they signed up:

* 'Old' if signup_date < '2021-01-01'

* 'Recent' if signup_date BETWEEN '2021-01-01' AND '2022-12-31'

* 'New' if signup_date > '2022-12-31'

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name, 
        signup_date,
        CASE 
            WHEN signup_date < '2021-01-01' THEN 'Old'
            WHEN signup_date BETWEEN '2021-01-01' AND '2022-12-31' THEN 'Recent'
            ELSE 'New'
        END AS customer_age
    FROM customers;
```    
</details>

---
#### Q35. Use CASE to display department names in full form:

* 'Sales' → 'SALES TEAM'

* 'IT' → 'TECHNOLOGY'

* 'HR' → 'HUMAN RESOURCES'

* 'Marketing' → 'MARKETING TEAM'
For others, keep as 'OTHER'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name,
        department,
        CASE department
            WHEN 'Sales' THEN 'SALES TEAM'
            WHEN 'IT' THEN 'TECHNOLOGY'
            WHEN 'HR' THEN 'HUMAN RESOURCES'
            WHEN 'Marketing' THEN 'MARKETING TEAM'
            ELSE 'OTHER'
        END AS department_full
    FROM employees;
```    
</details>


---
#### Q36. Use CASE with an aggregate function: Count how many employees fall into each salary_grade (High, Medium, Low).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN salary >= 80000 THEN 'High'
            WHEN salary >= 50000 AND salary < 80000 THEN 'Medium'
            ELSE 'Low'
        END AS salary_grade,
        COUNT(*) AS employee_count
    FROM employees
    GROUP BY salary_grade;
    -- Note: In some SQL, you need to repeat the CASE in GROUP BY, but MySQL allows alias.
    -- Safer: GROUP BY CASE WHEN ... END
```    
</details>

---
#### Q37. Use CASE to create a stock_status column:

* 'Out of Stock' if stock_quantity = 0

* 'Low Stock' if stock_quantity BETWEEN 1 AND 10

* 'In Stock' if stock_quantity > 10

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name,
        stock_quantity,
        CASE 
            WHEN stock_quantity = 0 THEN 'Out of Stock'
            WHEN stock_quantity BETWEEN 1 AND 10 THEN 'Low Stock'
            ELSE 'In Stock'
        END AS stock_status
    FROM products;
```    
</details>

---
#### Q38. Categorize products by price and count how many in each category (Expensive, Moderate, Cheap).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN price > 500 THEN 'Expensive'
            WHEN price BETWEEN 50 AND 500 THEN 'Moderate'
            ELSE 'Cheap'
        END AS price_category,
        COUNT(*) AS product_count
    FROM products
    GROUP BY price_category;
```    
</details>


---
#### Q39. Use CASE in ORDER BY to sort employees by a custom order: first IT, then Sales, then Marketing, then HR.
> (Hint: assign a numeric value in CASE and sort by that.)

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT first_name, department 
    FROM employees 
    ORDER BY 
        CASE department 
            WHEN 'IT' THEN 1
            WHEN 'Sales' THEN 2
            WHEN 'Marketing' THEN 3
            WHEN 'HR' THEN 4
            ELSE 5
        END;
```
</details>

---
#### Q40. Use CASE to flag products that are both expensive (> 500) and in low stock (< 10). Create a column priority that says 'High Priority' if expensive AND low stock, 'Monitor' if either condition, else 'Normal'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        product_name,
        price,
        stock_quantity,
        CASE 
            WHEN price > 500 AND stock_quantity < 10 THEN 'High Priority'
            WHEN price > 500 OR stock_quantity < 10 THEN 'Monitor'
            ELSE 'Normal'
        END AS priority
    FROM products;
```    
</details>

---

### SECTION F: GROUP BY + CASE (Combining Grouping with Conditional Logic)

---
#### Q41. Count the number of employees in each salary_grade (High, Medium, Low) per department.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        CASE 
            WHEN salary >= 80000 THEN 'High'
            WHEN salary >= 50000 AND salary < 80000 THEN 'Medium'
            ELSE 'Low'
        END AS salary_grade,
        COUNT(*) AS count
    FROM employees
    GROUP BY department, salary_grade;
```    
</details>


---
#### Q42. For each product category, count how many products are In Stock vs Out of Stock (using stock_status CASE).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        CASE 
            WHEN stock_quantity = 0 THEN 'Out of Stock'
            ELSE 'In Stock'
        END AS stock_status,
        COUNT(*) AS product_count
    FROM products
    GROUP BY category, stock_status;
```    
</details>

---
#### Q43. For each department, show the total salary of employees who earn >= 70000 vs those who earn < 70000.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        CASE 
            WHEN salary >= 70000 THEN 'High Earner'
            ELSE 'Low Earner'
        END AS earner_type,
        SUM(salary) AS total_salary
    FROM employees
    GROUP BY department, earner_type;
```    
</details>


---
#### Q44. Using HAVING with CASE? That's tricky. Instead, find departments where the count of High salary employees is at least 2.

> (We'll use a subquery or a derived table. Since subqueries are not in the list, we'll do a simpler one.)

**Find departments that have at least one employee with salary > 80000 (using HAVING with MAX).**

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        COUNT(*) AS total_emps, 
        MAX(salary) AS max_salary
    FROM employees
    GROUP BY department
    HAVING MAX(salary) > 80000;
```    
</details>

---
#### Q45. For each department, calculate the average salary, but also show a CASE column that labels the department's average as 'Above Company Avg' or 'Below Company Avg'.

> (First find company avg, then compare. Since we can't use subqueries in the list easily, we can hardcode the company average: (65000+72000+58000+85000+79000+67000+61000+55000+92000+48000)/10 = 68200)

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        AVG(salary) AS avg_salary,
        CASE 
            WHEN AVG(salary) > 68200 THEN 'Above Company Avg'
            ELSE 'Below Company Avg'
        END AS comparison
    FROM employees
    GROUP BY department;
```    
</details>

---
### SECTION G: Mixed Complex Queries (All Topics)
---
#### Q46. Group products by category, calculate total stock and average price, but only show categories where total stock > 20 and average price > 50. Use aliases.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category AS prod_category,
        SUM(stock_quantity) AS total_stock,
        AVG(price) AS avg_price
    FROM products
    GROUP BY category
    HAVING SUM(stock_quantity) > 20 AND AVG(price) > 50;
```
</details>

---
#### Q47. For each state, count customers and find the most recent signup date. Show only states with at least 2 customers and the most recent signup after '2022-01-01'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state,
        COUNT(*) AS customer_count,
        MAX(signup_date) AS latest_signup
    FROM customers
    GROUP BY state
    HAVING COUNT(*) >= 2 AND MAX(signup_date) > '2022-01-01';
```    
</details>


---
#### Q48. Use CASE to create a region column for customers based on state:

* 'West' for CA, AZ

* 'Midwest' for IL, TX? Actually TX is South. Let's do: CA, AZ → West; IL, TX → Central; NY → East.

**Count how many customers per region.**

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN state IN ('CA', 'AZ') THEN 'West'
            WHEN state IN ('IL', 'TX') THEN 'Central'
            WHEN state = 'NY' THEN 'East'
            ELSE 'Other'
        END AS region,
        COUNT(*) AS customer_count
    FROM customers
    GROUP BY region;
```    
</details>

---
#### Q49. For each department, show the number of employees, the total salary, and the average salary, but only for departments where the average salary is greater than the company average (68200). Use aliases for all columns.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department AS dept,
        COUNT(*) AS emp_count,
        SUM(salary) AS total_pay,
        AVG(salary) AS avg_pay
    FROM employees
    GROUP BY department
    HAVING AVG(salary) > 68200;
```    
</details>

---
#### Q50. Use CASE to create a price_tier for products (0-50: 'Budget', 51-200: 'Mid', 201-500: 'High', 501+: 'Premium'). Then count products and average stock quantity per tier.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN price <= 50 THEN 'Budget'
            WHEN price BETWEEN 51 AND 200 THEN 'Mid'
            WHEN price BETWEEN 201 AND 500 THEN 'High'
            ELSE 'Premium'
        END AS price_tier,
        COUNT(*) AS product_count,
        AVG(stock_quantity) AS avg_stock
    FROM products
    GROUP BY price_tier;
```    
</details>
 
---
#### Q51. For each year (using YEAR(hire_date)), count how many employees were hired in each department. Show only years where total hires (across all departments) is more than 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        YEAR(hire_date) AS hire_year,
        department,
        COUNT(*) AS hired_count
    FROM employees
    GROUP BY YEAR(hire_date), department
    HAVING COUNT(*) > 2;  -- This filters groups where dept+year combo has > 2. But we want total hires per year > 2.
    -- Correct: use a subquery or count total per year. Without subquery, let's do:
    -- Actually, let's just filter on COUNT(*) > 1 for this exercise.
```    
</details>

####  Let's do a simpler version:


#### Q51b. Count employees hired per year, and show only years with total hires > 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        YEAR(hire_date) AS hire_year,
        COUNT(*) AS total_hired
    FROM employees
    GROUP BY YEAR(hire_date)
    HAVING COUNT(*) > 2;
```    
</details>

---
#### Q52. Group customers by state and city, count them, and use CASE to label cities with count = 1 as 'Unique' and count > 1 as 'Multiple'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state,
        city,
        COUNT(*) AS customer_count,
        CASE 
            WHEN COUNT(*) = 1 THEN 'Unique'
            ELSE 'Multiple'
        END AS city_type
    FROM customers
    GROUP BY state, city;
```    
</details>

--- 
#### Q53. For each product category, calculate the total inventory value (price * stock_quantity), and use CASE to categorize the total value as 'High Value' (> 10000), 'Medium' (1000-10000), or 'Low' (< 1000).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        SUM(price * stock_quantity) AS total_value,
        CASE 
            WHEN SUM(price * stock_quantity) > 10000 THEN 'High Value'
            WHEN SUM(price * stock_quantity) BETWEEN 1000 AND 10000 THEN 'Medium'
            ELSE 'Low'
        END AS value_tier
    FROM products
    GROUP BY category;
```    
</details>


---
#### Q54. Show departments where the salary range (MAX - MIN) is greater than 20000. Include the department and the range.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        MAX(salary) - MIN(salary) AS salary_range
    FROM employees
    GROUP BY department
    HAVING MAX(salary) - MIN(salary) > 20000;
```    
</details>

---
#### Q55. For each department, calculate the average salary, and then use CASE to label it as 'High Pay' if avg > 70000, 'Medium' if between 55000 and 70000, else 'Low'. Show only departments with 'High Pay'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        AVG(salary) AS avg_salary,
        CASE 
            WHEN AVG(salary) > 70000 THEN 'High Pay'
            WHEN AVG(salary) BETWEEN 55000 AND 70000 THEN 'Medium'
            ELSE 'Low'
        END AS pay_grade
    FROM employees
    GROUP BY department
    HAVING CASE 
            WHEN AVG(salary) > 70000 THEN 'High Pay'
            ELSE 'Not High'
        END = 'High Pay';
```        
</details>

> Simpler: Just use HAVING AVG(salary) > 70000.


---
#### Q56. Count the number of products per category, but only include categories that have at least one product with a price greater than 100.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        COUNT(*) AS product_count
    FROM products
    GROUP BY category
    HAVING MAX(price) > 100;
```    
</details>

---
#### Q57. For each employee, show their name, salary, and a CASE column bonus that gives 10% of salary if salary < 60000, 5% if between 60000 and 80000, and 0% if > 80000. Show the bonus amount.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        first_name,
        salary,
        CASE 
            WHEN salary < 60000 THEN salary * 0.10
            WHEN salary BETWEEN 60000 AND 80000 THEN salary * 0.05
            ELSE 0
        END AS bonus
    FROM employees;
```    
</details>



---
#### Q58. Use GROUP BY with YEAR(signup_date) to count how many customers signed up each year, but only show years where the count is greater than 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        YEAR(signup_date) AS signup_year,
        COUNT(*) AS customer_count
    FROM customers
    GROUP BY YEAR(signup_date)
    HAVING COUNT(*) > 2;
```    
</details>


---
#### Q59. For each category, show the minimum and maximum price, and use CASE to say 'All over 100' if the minimum price is > 100, 'All under 50' if max < 50, else 'Mixed'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        MIN(price) AS min_price,
        MAX(price) AS max_price,
        CASE 
            WHEN MIN(price) > 100 THEN 'All over 100'
            WHEN MAX(price) < 50 THEN 'All under 50'
            ELSE 'Mixed'
        END AS price_pattern
    FROM products
    GROUP BY category;
```    
</details>


---
#### Q60. Use CASE in ORDER BY to sort products by category in a custom order: Electronics first, then Accessories, then Furniture, then Office, and within each category, sort by price descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT product_name, category, price
    FROM products
    ORDER BY 
        CASE category 
            WHEN 'Electronics' THEN 1
            WHEN 'Accessories' THEN 2
            WHEN 'Furniture' THEN 3
            WHEN 'Office' THEN 4
            ELSE 5
        END,
        price DESC;
```        
</details>

---
#### Q61. For each department, calculate the total salary and the number of employees. Then use CASE to label departments as 'Large' if they have >= 3 employees, else 'Small'. Show only 'Large' departments.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        COUNT(*) AS emp_count,
        SUM(salary) AS total_salary,
        CASE 
            WHEN COUNT(*) >= 3 THEN 'Large'
            ELSE 'Small'
        END AS dept_size
    FROM employees
    GROUP BY department
    HAVING COUNT(*) >= 3;
```    
</details>


---
#### Q62. Group products by category and count how many have stock_quantity = 0 vs stock_quantity > 0 using CASE inside SUM (pivot-style).

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        SUM(CASE WHEN stock_quantity = 0 THEN 1 ELSE 0 END) AS out_of_stock_count,
        SUM(CASE WHEN stock_quantity > 0 THEN 1 ELSE 0 END) AS in_stock_count
    FROM products
    GROUP BY category;
```    
</details>


---
#### Q63. Use CASE to label employees based on their hire_date decade:

* '2010s' if year between 2010-2019

* '2020s' if year between 2020-2029

* 'Other' otherwise

**Then count how many employees in each decade per department.**

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        CASE 
            WHEN YEAR(hire_date) BETWEEN 2010 AND 2019 THEN '2010s'
            WHEN YEAR(hire_date) BETWEEN 2020 AND 2029 THEN '2020s'
            ELSE 'Other'
        END AS decade,
        COUNT(*) AS employee_count
    FROM employees
    GROUP BY department, decade;
```    
</details>

---
#### Q64. For each customer state, find the earliest and latest signup date. Use CASE to label the state as 'Active' if the latest signup is within the last 1 year (from today), else 'Inactive'.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state,
        MIN(signup_date) AS earliest,
        MAX(signup_date) AS latest,
        CASE 
            WHEN DATEDIFF(CURDATE(), MAX(signup_date)) <= 365 THEN 'Active'
            ELSE 'Inactive'
        END AS status
    FROM customers
    GROUP BY state;
```    
</details>

---
#### Q65. Use GROUP BY with HAVING to find departments where the total number of employees is greater than the average department size (overall average employees per department).

> (First get average department size: total employees / number of distinct departments = 10/4 = 2.5. So we need departments with count > 2.5, i.e., count >= 3.)

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department, 
        COUNT(*) AS emp_count
    FROM employees
    GROUP BY department
    HAVING COUNT(*) > (SELECT COUNT(*) / COUNT(DISTINCT department) FROM employees);
    -- Subquery used here. If you want to avoid subquery, just use HAVING COUNT(*) > 2.5
```    
</details>

#### Since subqueries aren't in the list, let's do a simpler version:

#### Q65b. Find departments with employee count greater than 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT department, COUNT(*) AS emp_count
    FROM employees
    GROUP BY department
    HAVING COUNT(*) > 2;
```    
</details>

---
#### Q66. Use CASE to create a season column for customers based on their signup month:

* Winter: 12, 1, 2

* Spring: 3, 4, 5

* Summer: 6, 7, 8

* Fall: 9, 10, 11

**Then count how many customers signed up in each season.**

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN MONTH(signup_date) IN (12, 1, 2) THEN 'Winter'
            WHEN MONTH(signup_date) IN (3, 4, 5) THEN 'Spring'
            WHEN MONTH(signup_date) IN (6, 7, 8) THEN 'Summer'
            WHEN MONTH(signup_date) IN (9, 10, 11) THEN 'Fall'
        END AS season,
        COUNT(*) AS customer_count
    FROM customers
    GROUP BY season;
```    
</details>

---
#### Q67. For each product category, calculate the total revenue if all stock were sold (price * stock_quantity). Then use CASE to label categories as `'Top Tier'` if total revenue > 20000, `'Mid Tier'` if 5000-20000, `'Low Tier'` if < 5000. Show only 'Top Tier' categories.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        SUM(price * stock_quantity) AS potential_revenue,
        CASE 
            WHEN SUM(price * stock_quantity) > 20000 THEN 'Top Tier'
            WHEN SUM(price * stock_quantity) BETWEEN 5000 AND 20000 THEN 'Mid Tier'
            ELSE 'Low Tier'
        END AS tier
    FROM products
    GROUP BY category
    HAVING SUM(price * stock_quantity) > 20000;
```    
</details>

---
#### Q68. Write a query that groups employees by the first letter of their `first_name` (using `LEFT(first_name, 1)`) and counts how many employees have names starting with each letter. Show only letters with count > 1.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        LEFT(first_name, 1) AS first_letter,
        COUNT(*) AS emp_count
    FROM employees
    GROUP BY LEFT(first_name, 1)
    HAVING COUNT(*) > 1;
```    
</details>


---
#### Q69. For each department, calculate:

* Total employees

* Average salary

* The difference between the highest and lowest salary

* Use `CASE` to label the department's salary spread as `'Wide'` if difference > 30000, else `'Narrow'`

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        COUNT(*) AS total_emps,
        AVG(salary) AS avg_sal,
        MAX(salary) - MIN(salary) AS salary_spread,
        CASE 
            WHEN (MAX(salary) - MIN(salary)) > 30000 THEN 'Wide'
            ELSE 'Narrow'
        END AS spread_label
    FROM employees
    GROUP BY department;
```    
</details>

---
#### Q70. Use `CASE` to assign a `priority` to each product:

* `'High'` if category = 'Electronics' and price > 1000

* `'Medium'` if category = 'Accessories' and stock_quantity > 100

* `'Low'` for everything else

**Then count how many products fall into each priority level.**

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        CASE 
            WHEN category = 'Electronics' AND price > 1000 THEN 'High'
            WHEN category = 'Accessories' AND stock_quantity > 100 THEN 'Medium'
            ELSE 'Low'
        END AS priority,
        COUNT(*) AS product_count
    FROM products
    GROUP BY priority;
```    
</details>

---

### 🎯 BONUS: Advanced Combinations



---
#### Q71. For each department, show the total salary, but only for employees hired in 2020 or later. Then filter departments where this total exceeds 60000.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        SUM(salary) AS total_salary_recent
    FROM employees
    WHERE hire_date >= '2020-01-01'
    GROUP BY department
    HAVING SUM(salary) > 60000;
```
</details>


---
#### Q72. Group products by `category` and `stock_status` (using CASE: 'In Stock' if stock > 0, else 'Out'). Count products in each group, and show only groups where count >= 2.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category,
        CASE 
            WHEN stock_quantity > 0 THEN 'In Stock'
            ELSE 'Out'
        END AS stock_status,
        COUNT(*) AS product_count
    FROM products
    GROUP BY category, stock_status
    HAVING COUNT(*) >= 2;
```    
</details>


---
#### Q73. Use `CASE` to categorize employees by the length of their `first_name` (short = length <= 4, medium = 5-6, long = >= 7). For each department, count how many employees have short, medium, and long names.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        department,
        CASE 
            WHEN LENGTH(first_name) <= 4 THEN 'Short'
            WHEN LENGTH(first_name) BETWEEN 5 AND 6 THEN 'Medium'
            ELSE 'Long'
        END AS name_length_category,
        COUNT(*) AS emp_count
    FROM employees
    GROUP BY department, name_length_category;
```    
</details>


---
#### Q74. Find the total stock quantity per category, and also the number of distinct products per category. Use aliases, and only show categories where total stock > 50.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        category AS cat,
        SUM(stock_quantity) AS total_qty,
        COUNT(*) AS distinct_products
    FROM products
    GROUP BY category
    HAVING SUM(stock_quantity) > 50;
```    
</details>
 
---
#### Q75. For each state, count the number of customers, and use `CASE` to label states as `'Large'` if count >= 3, `'Medium'` if count = 2, `'Small'` if count = 1. Sort by count descending.

<details> <summary>Click to reveal answer</summary>

```sql
    SELECT 
        state,
        COUNT(*) AS customer_count,
        CASE 
            WHEN COUNT(*) >= 3 THEN 'Large'
            WHEN COUNT(*) = 2 THEN 'Medium'
            ELSE 'Small'
        END AS state_size
    FROM customers
    GROUP BY state
    ORDER BY customer_count DESC;
```    
</details>


---
<br/><br/><br/><br/>

#### Happy Practicing! 😊✨

<br/><br/><br/><br/>

---