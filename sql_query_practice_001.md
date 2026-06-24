## Overview 

### 🛠️ PART 1: SETUP (Run this once in your SQL environment)
### 📝 PART 2: PRACTICE QUESTIONS + SOLUTIONS

* **SECTION A**: SELECT & WHERE (Basic Filtering)
* **SECTION B**: WHERE with AND / OR (Compound Conditions)
* **SECTION C**: ORDER BY (Sorting)
* **SECTION D**: LIMIT (Restricting Rows)
* **SECTION E**: DISTINCT (Removing Duplicates)
* **SECTION F**: SECTION F: Mixing Everything (SELECT, WHERE, ORDER BY, LIMIT, DISTINCT
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