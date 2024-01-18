---
title: "Mastering SQL: A Comprehensive Guide to SQL Queries || Lesson - 2"
datePublished: Thu Jan 18 2024 06:31:49 GMT+0000 (Coordinated Universal Time)
cuid: clriu3fwi000609l9h32v5ab0
slug: mastering-sql-a-comprehensive-guide-to-sql-queries-lesson-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705491445002/c7a7a070-c2bc-4023-ac30-37102050c8cb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1705491491837/e2dc06dc-bfdd-4461-89c3-323e41836a71.png
tags: sql, hashnode, wemakedevs, mayankaggarwal, mayank

---

In the ever-evolving landscape of data management, SQL stands as a formidable key to unlocking the secrets within databases. Whether you're a novice eager to grasp the fundamentals or a seasoned developer aiming to refine your skills, this blog series, "Mastering SQL: Unraveling the Power of Queries," is your compass in navigating the intricate world of structured query language.

# **Chapter 1: WHERE Clause**

In the SQL world, the "WHERE" clause serves as a powerful filter, allowing you to extract specific data from your database. This chapter will guide you through its usage, helping you understand how to retrieve exactly what you need.

### Understanding the WHERE Clause:

The basic syntax of a SELECT statement with a WHERE clause is as follows:

```sql
SELECT column1, column2, ...
FROM table
WHERE condition;
```

Here, "condition" is the criterion that determines which rows to retrieve. Let's dive into some practical examples to illustrate its usage.

#### Example 1.1: Basic Equality Check

Suppose we have a table named `employees` and want to retrieve information about employees with a specific job title, say 'Software Engineer'. The query would look like this:

```sql
SELECT *
FROM employees
WHERE job_title = 'Software Engineer';
```

This query will return all columns (`*`) from the `employees` table where the job title is 'Software Engineer'.

#### Example 1.2: Numeric Conditions

Consider a scenario where you want to find orders with a total amount greater than $1,000. The query would be:

```sql
SELECT *
FROM orders
WHERE total_amount > 1000;
```

This retrieves all columns from the `orders` table where the total amount exceeds $1,000.

#### Example 1.3: Textual Conditions with LIKE

Using the `LIKE` operator allows you to perform wildcard searches. Let's find all products whose name contains the word 'Laptop':

```sql
SELECT *
FROM products
WHERE product_name LIKE '%Laptop%';
```

The `%` symbols act as wildcards, allowing any characters before and after 'Laptop' in the product name.

### Practical Tips:

* **Be Mindful of Data Types:** Ensure that the data types match in your conditions. For instance, comparing strings with strings and numbers with numbers.
    
* **Use Logical Operators:** Combine multiple conditions using logical operators like AND, OR, and NOT to create complex criteria.
    

This marks the beginning of your SQL journey! Understanding the WHERE clause lays a foundation for crafting precise and targeted queries. In the next chapter, we'll explore the various operators you can use within the WHERE clause to refine your data retrieval even further. Stay tuned!

# **Chapter 2: Operators in WHERE**

Welcome back to our SQL mastery journey! In Chapter 1, we delved into the WHERE clause, laying the groundwork for precise data retrieval. Now, let's explore the diverse world of operators within the WHERE clause, empowering you to craft conditions that go beyond simple equality checks.

### Understanding Operators in WHERE:

Operators allow you to create more complex conditions in your queries. Here are some commonly used operators:

#### Equality Operators:

* `=`: Equal to
    
* `<>` or `!=`: Not equal to
    

#### Comparison Operators:

* `<`: Less than
    
* `>`: Greater than
    
* `<=`: Less than or equal to
    
* `>=`: Greater than or equal to
    

#### Logical Operators:

* `AND`: Both conditions must be true
    
* `OR`: At least one condition must be true
    
* `NOT`: Negates a condition
    

#### Membership Operators:

* `IN`: Checks if a value exists in a list
    
* `NOT IN`: Checks if a value does not exist in a list
    

#### BETWEEN Operator:

* `BETWEEN`: Checks if a value is within a range
    

#### LIKE Operator:

* `LIKE`: Matches patterns in text data using wildcards (% for any sequence of characters, \_ for a single character)
    

### Examples:

#### Example 2.1: Combining Conditions with AND

Let's find employees who are both 'Software Engineers' and have a salary greater than $70,000:

```sql
SELECT *
FROM employees
WHERE job_title = 'Software Engineer'
  AND salary > 70000;
```

#### Example 2.2: Using OR to Expand Options

Retrieve orders with a total amount either greater than $1,000 or placed by a specific customer:

```sql
SELECT *
FROM orders
WHERE total_amount > 1000
   OR customer_id = 123;
```

#### Example 2.3: Employing the IN Operator

Find products with specific product IDs:

```sql
SELECT *
FROM products
WHERE product_id IN (101, 102, 103);
```

#### Example 2.4: Unleashing the Power of LIKE

Search for customers whose names start with 'J':

```sql
SELECT *
FROM customers
WHERE customer_name LIKE 'J%';
```

### Practical Tips:

* **Parentheses for Clarity:** When combining multiple conditions, use parentheses to ensure the correct order of evaluation.
    
* **Use NOT for Exclusions:** The NOT operator can be handy for excluding specific values or conditions.
    

Mastering these operators expands your query toolkit, enabling you to express intricate conditions and retrieve precisely the data you need. Stay tuned for Chapter 3, where we'll delve into frequently used operators that will further enhance your SQL expertise!

# **Chapter 3: Frequently Used Operators - Navigating SQL with Precision**

Welcome back to our SQL mastery journey! In the previous chapters, we explored the WHERE clause and various operators, setting the stage for more nuanced queries. In Chapter 3, we'll delve into frequently used operators that add finesse to your SQL statements, making your data retrieval more dynamic and powerful.

### Exploring Frequently Used Operators:

#### 1\. **IN Operator:**

The `IN` operator is a powerful tool to filter results based on a list of values. Suppose you want to find all employees in specific departments:

```sql
SELECT *
FROM employees
WHERE department_id IN (101, 102, 103);
```

This query retrieves employees from departments 101, 102, and 103.

#### 2\. **NOT Operator:**

The `NOT` operator negates a condition. Let's find all employees who are not 'Managers':

```sql
SELECT *
FROM employees
WHERE job_title != 'Manager';
```

This query returns all employees who don't hold the title 'Manager'.

#### 3\. **BETWEEN Operator:**

The `BETWEEN` operator checks if a value is within a specified range. For instance, finding orders placed between two dates:

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';
```

This query retrieves orders placed within the specified date range.

#### 4\. **LIKE Operator with Wildcards:**

Expanding on the `LIKE` operator, you can use wildcards to match patterns in text data. Find customers whose names contain 'John':

```sql
SELECT *
FROM customers
WHERE customer_name LIKE '%John%';
```

This query returns customers with names like 'John Doe' or 'Johnny Smith'.

### Practical Tips:

* **Case Sensitivity:** Be aware that some databases are case-sensitive, so 'Manager' and 'manager' may be treated differently.
    
* **Optimize with Indexing:** Frequent use of the `LIKE` operator can impact performance. Consider indexing columns used in such operations for efficiency.
    

#### Putting it into Practice:

Combine these frequently used operators to craft intricate conditions. For example, finding orders placed by specific customers within a certain date range:

```sql
SELECT *
FROM orders
WHERE customer_id IN (101, 102, 103)
  AND order_date BETWEEN '2023-01-01' AND '2023-12-31';
```

This query pulls orders placed by customers 101, 102, or 103 within the specified date range.

As you master these operators, your SQL prowess will reach new heights. Stay tuned for Chapter 4, where we'll explore the "LIMIT" clause, allowing you to control the number of rows returned by your queries. Happy querying!

# **Chapter 4: LIMIT Clause - Harnessing Precision in Result Sets**

Welcome back to our SQL mastery journey! In the previous chapters, we navigated through the WHERE clause and various operators, refining our ability to retrieve specific data. In Chapter 4, we'll explore the LIMIT clause—a powerful tool for controlling the size of result sets, optimizing performance, and making your queries more manageable.

### Understanding the LIMIT Clause:

The LIMIT clause is used to restrict the number of rows returned by a query. It's particularly useful when dealing with large datasets or when you're only interested in a specific subset of results.

#### Basic Syntax:

```sql
SELECT column1, column2, ...
FROM table
WHERE condition
LIMIT number_of_rows;
```

### Examples:

#### Example 4.1: Retrieve a Specific Number of Rows

Suppose you want to retrieve the first 10 employees from the 'employees' table:

```sql
SELECT *
FROM employees
LIMIT 10;
```

This query returns only the first 10 rows from the 'employees' table.

#### Example 4.2: Combining with ORDER BY

When used with ORDER BY, LIMIT becomes a potent combination. Let's find the top 5 highest-paid employees:

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 5;
```

This query first orders the employees by salary in descending order and then retrieves only the top 5.

#### Example 4.3: Paginating Results

For scenarios where you want to implement pagination, you can use LIMIT along with OFFSET. Suppose you want to display 10 records per page, and you're on page 3:

```sql
SELECT *
FROM products
LIMIT 10 OFFSET 20;
```

This query skips the first 20 rows and then retrieves the next 10, effectively showing results for page 3.

### Practical Tips:

* **Understand Your Needs:** Use LIMIT judiciously based on your application's requirements. Fetching only the necessary data can significantly improve query performance.
    
* **Combine with ORDER BY:** When using LIMIT, consider incorporating ORDER BY to ensure the desired subset of data is retrieved.
    

### Putting it into Practice:

Imagine you want to retrieve the top 3 highest-priced products from a 'products' table:

```sql
SELECT *
FROM products
ORDER BY price DESC
LIMIT 3;
```

This query orders products by price in descending order and returns only the top 3.

As you incorporate the LIMIT clause into your SQL toolkit, you gain more control over the volume of data retrieved, optimizing your queries for efficiency. Stay tuned for Chapter 5, where we'll explore the ORDER BY clause, unraveling the art of sorting your query results. Happy querying!

# **Chapter 5: ORDER BY Clause - Crafting Structured Results**

Welcome back to our SQL mastery journey! In the preceding chapters, we've covered the WHERE clause, various operators, and the LIMIT clause. Now, in Chapter 5, we'll delve into the ORDER BY clause—an essential tool for organizing query results with precision.

### Understanding the ORDER BY Clause:

The ORDER BY clause enables you to sort the result set based on one or more columns. Sorting can be done in ascending (ASC) or descending (DESC) order.

#### Basic Syntax:

```sql
SELECT column1, column2, ...
FROM table
WHERE condition
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;
```

### Examples:

#### Example 5.1: Sorting in Ascending Order

Consider a scenario where you want to retrieve a list of employees ordered by their hire date in ascending order:

```sql
SELECT *
FROM employees
ORDER BY hire_date ASC;
```

This query returns all employees, sorted by their hire date from the earliest to the most recent.

#### Example 5.2: Sorting in Descending Order

Now, let's find the newest products in a 'products' table by sorting them based on their creation date in descending order:

```sql
SELECT *
FROM products
ORDER BY creation_date DESC;
```

This query returns all products, sorted by their creation date from the most recent to the earliest.

#### Example 5.3: Sorting by Multiple Columns

You can also sort results by multiple columns. For instance, sorting employees by department ID in ascending order and then by salary in descending order:

```sql
SELECT *
FROM employees
ORDER BY department_id ASC, salary DESC;
```

This query first sorts employees by department ID in ascending order. Within each department, it further sorts them by salary in descending order.

### Practical Tips:

* **Understand Data Types:** Keep in mind that sorting can behave differently based on data types. Be cautious when sorting text and numeric columns.
    
* **Use with LIMIT:** Combining ORDER BY with the LIMIT clause can help you retrieve a specific subset of ordered results.
    

### Putting it into Practice:

Imagine you want to retrieve the top 5 highest-priced products from a 'products' table, but this time, you want them ordered alphabetically by product name:

```sql
SELECT *
FROM products
ORDER BY product_name ASC
LIMIT 5;
```

This query orders products by name in ascending order and then returns only the top 5.

By mastering the ORDER BY clause, you gain control over how your query results are presented, enhancing the clarity and utility of your SQL statements. Stay tuned for Chapter 6, where we'll dive into aggregate functions, unlocking the power to perform calculations on your data. Happy querying!

# **Chapter 6: Aggregate Functions - Unleashing the Power of Data Calculations**

Welcome back to our SQL mastery journey! In the previous chapters, we've explored the WHERE clause, operators, the LIMIT clause, and the ORDER BY clause. Now, in Chapter 6, we'll venture into the realm of aggregate functions—a crucial set of tools that allow you to perform calculations on your data, extracting meaningful insights and statistics.

### Understanding Aggregate Functions:

Aggregate functions operate on sets of rows to compute a single result, summarizing or transforming data within a column.

#### Common Aggregate Functions:

1. **COUNT():** Returns the number of rows in a set.
    
2. **SUM():** Calculates the sum of values in a numeric column.
    
3. **AVG():** Computes the average of values in a numeric column.
    
4. **MIN():** Finds the minimum value in a column.
    
5. **MAX():** Retrieves the maximum value in a column.
    

#### Basic Syntax:

```sql
SELECT AGGREGATE_FUNCTION(column) AS result_alias
FROM table
WHERE condition;
```

### Examples:

#### Example 6.1: Counting Records

Find the total number of orders in an 'orders' table:

```sql
SELECT COUNT(*) AS total_orders
FROM orders;
```

This query returns a single value, the count of all rows in the 'orders' table.

#### Example 6.2: Calculating Average Salary

Determine the average salary of employees in a 'employees' table:

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```

This query computes and returns the average salary from the 'employees' table.

#### Example 6.3: Finding Maximum and Minimum Values

Identify the highest and lowest prices among products:

```sql
SELECT MAX(price) AS max_price, MIN(price) AS min_price
FROM products;
```

This query retrieves the maximum and minimum prices from the 'products' table.

### Practical Tips:

* **Use with GROUP BY:** Aggregate functions are often used in conjunction with the GROUP BY clause to perform calculations on subsets of data.
    
* **Handle NULL Values:** Aggregate functions might behave unexpectedly with NULL values. Use functions like COALESCE() to handle such cases.
    

### Putting it into Practice:

Imagine you want to find the total revenue generated from all orders in the 'orders' table. Assuming each order has a 'quantity' and 'unit\_price' column:

```sql
SELECT SUM(quantity * unit_price) AS total_revenue
FROM orders;
```

This query calculates the total revenue by multiplying the quantity and unit price for each order and then summing up the results.

As you harness the power of aggregate functions, you gain the ability to perform insightful calculations on your data, uncovering patterns and trends. Stay tuned for Chapter 7, where we'll explore the GROUP BY clause, paving the way for more advanced data analysis. Happy querying!

# **Chapter 7: GROUP BY Clause - Unraveling Data Patterns and Trends**

Welcome back to our SQL mastery journey! In the previous chapters, we've navigated through the WHERE clause, operators, the LIMIT clause, the ORDER BY clause, and aggregate functions. Now, in Chapter 7, we'll explore the GROUP BY clause—an instrumental tool that enables you to group your data based on specific columns, paving the way for more advanced data analysis.

### Understanding the GROUP BY Clause:

The GROUP BY clause is used to arrange identical data into summary rows, based on the values of one or more columns.

#### Basic Syntax:

```sql
SELECT column1, column2, AGGREGATE_FUNCTION(column3) AS result_alias
FROM table
WHERE condition
GROUP BY column1, column2;
```

### Examples:

#### Example 7.1: Grouping by Category

Suppose you want to find the total quantity of products sold for each category from an 'order\_details' table:

```sql
SELECT category, SUM(quantity) AS total_quantity
FROM order_details
GROUP BY category;
```

This query groups the data by category, calculating the total quantity sold for each category.

#### Example 7.2: Grouping by Multiple Columns

Extend the previous example to group by both category and supplier, finding the total quantity sold for each combination:

```sql
SELECT category, supplier, SUM(quantity) AS total_quantity
FROM order_details
GROUP BY category, supplier;
```

This query provides a more detailed breakdown, grouping data by both category and supplier.

#### Example 7.3: Using HAVING Clause

Imagine you want to find categories with total quantities sold greater than 100 units. The HAVING clause helps filter grouped results:

```sql
SELECT category, SUM(quantity) AS total_quantity
FROM order_details
GROUP BY category
HAVING SUM(quantity) > 100;
```

This query filters the results to include only those categories with a total quantity sold exceeding 100 units.

### Practical Tips:

* **Understand Aggregate Functions:** When using GROUP BY, columns in the SELECT clause must either be part of the GROUP BY clause or be used with an aggregate function.
    
* **Mind the Order:** The order of columns in the GROUP BY clause matters. Results are grouped first by the first column, then by the second, and so on.
    

### Putting it into Practice:

Suppose you want to analyze the total revenue generated by each product category from an 'orders' table. Assuming you have an 'order\_details' table with columns 'product\_id', 'quantity', and 'unit\_price':

```sql
SELECT p.product_id, p.product_name, c.category_name, SUM(od.quantity * od.unit_price) AS total_revenue
FROM products p
JOIN order_details od ON p.product_id = od.product_id
JOIN categories c ON p.category_id = c.category_id
GROUP BY p.product_id, p.product_name, c.category_name;
```

This query joins the 'products', 'order\_details', and 'categories' tables, grouping the data by product ID, product name, and category name while calculating the total revenue for each combination.

As you embrace the GROUP BY clause, you gain the ability to unravel complex data patterns and trends, opening new avenues for advanced data analysis. Stay tuned for Chapter 8, where we'll explore the HAVING clause, refining our ability to filter grouped results with precision. Happy querying!

# **Chapter 8: HAVING Clause - Fine-Tuning Grouped Results**

Welcome back to our SQL mastery journey! In the preceding chapters, we've covered the WHERE clause, operators, the LIMIT clause, the ORDER BY clause, aggregate functions, and the GROUP BY clause. Now, in Chapter 8, we'll explore the HAVING clause—a powerful tool that allows you to filter grouped results based on specified conditions, providing a way to fine-tune your data analysis.

### Understanding the HAVING Clause:

The HAVING clause works in conjunction with the GROUP BY clause, enabling you to filter grouped results based on aggregate function results.

#### Basic Syntax:

```sql
SELECT column1, column2, AGGREGATE_FUNCTION(column3) AS result_alias
FROM table
WHERE condition
GROUP BY column1, column2
HAVING condition_on_aggregate_function;
```

### Examples:

#### Example 8.1: Filtering Groups by Total Quantity Sold

Extend the previous example of grouping products by category and supplier. Now, filter out categories and suppliers with a total quantity sold less than 50 units:

```sql
SELECT category, supplier, SUM(quantity) AS total_quantity
FROM order_details
GROUP BY category, supplier
HAVING SUM(quantity) > 50;
```

This query uses the HAVING clause to include only groups with a total quantity sold greater than 50 units.

#### Example 8.2: Finding Categories with High Average Price

Suppose you want to find categories with an average unit price greater than $50:

```sql
SELECT category, AVG(unit_price) AS average_price
FROM products
GROUP BY category
HAVING AVG(unit_price) > 50;
```

This query filters out categories with an average unit price less than or equal to $50.

#### Example 8.3: Using HAVING with COUNT

Imagine you want to find employees who have placed at least five orders. The HAVING clause helps filter groups based on the count of orders:

```sql
SELECT employee_id, COUNT(order_id) AS total_orders
FROM orders
GROUP BY employee_id
HAVING COUNT(order_id) >= 5;
```

This query includes only employees who have placed at least five orders.

### Practical Tips:

* **Understand Aggregate Functions:** The conditions in the HAVING clause typically involve aggregate functions. Ensure you grasp the nature of these functions and how they interact with grouped data.
    
* **Apply Logical Operators:** Combine multiple conditions in the HAVING clause using logical operators (AND, OR) for more complex filtering.
    

### Putting it into Practice:

Suppose you want to find product categories with both high average unit prices (greater than $100) and high total quantities sold (greater than 200 units). Assuming you have an 'order\_details' table and a 'products' table:

```sql
SELECT p.category, AVG(p.unit_price) AS avg_price, SUM(od.quantity) AS total_quantity
FROM products p
JOIN order_details od ON p.product_id = od.product_id
GROUP BY p.category
HAVING AVG(p.unit_price) > 100 AND SUM(od.quantity) > 200;
```

This query calculates the average unit price and total quantity sold for each product category and includes only categories that meet both conditions.

By mastering the HAVING clause, you gain precision in filtering grouped results, enabling you to extract insights that match specific criteria. Stay tuned for Chapter 9, where we'll explore the "General Order," bringing together the concepts covered in previous chapters to create well-structured and powerful SQL queries. Happy querying!

# **Chapter 9: General Order - Crafting Structured and Powerful SQL Queries**

Welcome back to our SQL mastery journey! In the preceding chapters, we've explored various SQL clauses and concepts, including the WHERE clause, operators, the LIMIT clause, the ORDER BY clause, aggregate functions, the GROUP BY clause, and the HAVING clause. In Chapter 9, we'll bring together these concepts to create well-structured and powerful SQL queries, following a general order for crafting effective statements.

### The General Order of SQL Statements:

Creating a SQL query involves combining different clauses in a logical sequence. The general order is as follows:

```sql
SELECT columns
FROM table
JOIN other_table ON condition
WHERE condition
GROUP BY columns
HAVING condition
ORDER BY columns;
```

### Examples:

#### Example 9.1: Retrieve Employee Information with Total Orders

Suppose you want to retrieve information about employees along with the total number of orders they have placed. You can follow the general order like this:

```sql
SELECT employees.employee_id, employees.employee_name, COUNT(orders.order_id) AS total_orders
FROM employees
LEFT JOIN orders ON employees.employee_id = orders.employee_id
GROUP BY employees.employee_id, employees.employee_name
ORDER BY total_orders DESC;
```

This query retrieves employee information, counts the total number of orders placed by each employee using the LEFT JOIN and GROUP BY clauses, and then orders the results by the total number of orders in descending order.

#### Example 9.2: Find High-Value Customers by Country

Suppose you want to find high-value customers by country, considering customers who have made purchases totaling more than $10,000. The general order can be applied as follows:

```sql
SELECT customers.country, customers.customer_name, SUM(orders.total_amount) AS total_purchases
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id
GROUP BY customers.country, customers.customer_name
HAVING SUM(orders.total_amount) > 10000
ORDER BY total_purchases DESC;
```

This query retrieves customer information, sums the total amount of purchases using the LEFT JOIN and GROUP BY clauses, filters out customers with total purchases less than $10,000 using the HAVING clause, and finally orders the results by total purchases in descending order.

### Practical Tips:

* **Understand Joins:** When using JOIN clauses, ensure you understand the relationships between tables and use the appropriate join type (INNER JOIN, LEFT JOIN, etc.).
    
* **Test Incrementally:** Build your query step by step, testing each part incrementally to ensure it produces the expected results.
    

### Putting it into Practice:

Now, imagine you want to find the top 3 product categories with the highest average unit prices, but only for categories with a total quantity sold exceeding 50 units. Assuming you have an 'order\_details' table and a 'products' table:

```sql
SELECT p.category, AVG(p.unit_price) AS avg_price, SUM(od.quantity) AS total_quantity
FROM products p
JOIN order_details od ON p.product_id = od.product_id
GROUP BY p.category
HAVING SUM(od.quantity) > 50
ORDER BY avg_price DESC
LIMIT 3;
```

This query follows the general order, combining JOIN, GROUP BY, HAVING, ORDER BY, and LIMIT clauses to find the top 3 product categories meeting specific criteria.

By adhering to the general order of SQL statements, you can construct queries that are not only powerful but also structured and easy to understand. Stay tuned for Chapter 10, where we'll explore data modification operations such as updating, deleting, and altering tables. Happy querying!

# **Chapter 10: Data Modification Operations - Transforming and Evolving Your Database**

Welcome back to our SQL mastery journey! In the preceding chapters, we've explored various SQL clauses and concepts, including the WHERE clause, operators, the LIMIT clause, the ORDER BY clause, aggregate functions, the GROUP BY clause, the HAVING clause, and the General Order of SQL statements. In Chapter 10, we'll dive into data modification operations—essential techniques for updating, deleting, and altering tables in your database.

### 10.1 UPDATE Statement:

The UPDATE statement is used to modify existing records in a table.

#### Basic Syntax:

```sql
UPDATE table
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

#### Example 10.1.1: Update Employee Salary

Suppose you want to give all employees in the 'sales' department a salary raise of 10%. You can use the UPDATE statement like this:

```sql
UPDATE employees
SET salary = salary * 1.1
WHERE department = 'sales';
```

This query updates the 'salary' column for all employees in the 'sales' department, increasing it by 10%.

### 10.2 DELETE Statement:

The DELETE statement is used to remove records from a table.

#### Basic Syntax:

```sql
DELETE FROM table
WHERE condition;
```

#### Example 10.2.1: Delete Inactive Customers

Suppose you want to delete customers who haven't made any purchases. You can use the DELETE statement like this:

```sql
DELETE FROM customers
WHERE customer_id NOT IN (SELECT DISTINCT customer_id FROM orders);
```

This query deletes customers from the 'customers' table who do not have corresponding entries in the 'orders' table.

### 10.3 ALTER TABLE Statement:

The ALTER TABLE statement is used to modify the structure of an existing table.

#### Basic Syntax:

```sql
ALTER TABLE table
ADD COLUMN new_column data_type;
```

#### Example 10.3.1: Add a Birthday Column to Employees

Suppose you want to add a 'birthday' column to the 'employees' table. You can use the ALTER TABLE statement like this:

```sql
ALTER TABLE employees
ADD COLUMN birthday DATE;
```

This query adds a new column named 'birthday' with the data type DATE to the 'employees' table.

### Practical Tips:

* **Use WHERE Clause Carefully:** When using UPDATE or DELETE statements, always include a WHERE clause to ensure you're modifying or deleting the intended records.
    
* **Back Up Data:** Before performing significant data modifications, it's good practice to back up your data or test the operations in a safe environment.
    

### Putting it into Practice:

Imagine you want to update the 'unit\_price' of products in the 'electronics' category to increase them by 5%. You can use the UPDATE statement like this:

```sql
UPDATE products
SET unit_price = unit_price * 1.05
WHERE category = 'electronics';
```

This query increases the 'unit\_price' for all products in the 'electronics' category by 5%.

By mastering data modification operations, you gain the ability to keep your database up-to-date and adapt its structure to evolving needs. Stay tuned for Chapter 11, where we'll explore the TRUNCATE TABLE statement—a powerful tool for quickly and efficiently removing all records from a table. Happy querying!

# **Chapter 11: TRUNCATE TABLE - Efficiently Clearing Table Data**

Welcome back to our SQL mastery journey! In the preceding chapters, we've covered various SQL concepts, including the WHERE clause, operators, the LIMIT clause, the ORDER BY clause, aggregate functions, the GROUP BY clause, the HAVING clause, the General Order of SQL statements, and data modification operations. In Chapter 11, we'll explore the TRUNCATE TABLE statement—a powerful and efficient tool for quickly removing all records from a table.

### 11.1 TRUNCATE TABLE Statement:

The TRUNCATE TABLE statement is used to delete all records from a table, providing a faster and more efficient alternative to the DELETE statement.

#### Basic Syntax:

```sql
TRUNCATE TABLE table;
```

### Example:

#### Example 11.1.1: Clearing Order Details Table

Suppose you want to clear all records from the 'order\_details' table. You can use the TRUNCATE TABLE statement like this:

```sql
TRUNCATE TABLE order_details;
```

This query removes all records from the 'order\_details' table, leaving the table structure intact.

### Benefits of TRUNCATE TABLE:

1. **Efficiency:** TRUNCATE TABLE is often faster than DELETE, especially for large tables, as it doesn't generate individual row delete statements.
    
2. **Resetting Auto-Increment Columns:** If a table has an auto-increment column, TRUNCATE TABLE resets the auto-increment value back to its seed.
    
3. **Minimal Logging:** TRUNCATE TABLE generates less transaction log than DELETE, making it more resource-efficient.
    

### Considerations:

* **No WHERE Clause:** Unlike DELETE, TRUNCATE TABLE does not allow a WHERE clause. It removes all records from the table.
    
* **Table Lock:** TRUNCATE TABLE acquires a table-level lock, which may impact concurrent operations on the same table.
    

### Practical Tips:

* **Understand Use Cases:** Use TRUNCATE TABLE when you need to quickly remove all records from a table without affecting its structure.
    
* **Backup Data:** As with any operation that involves data deletion, ensure you have a backup in case you need to recover the data.
    

### Putting it into Practice:

Imagine you want to clear all records from the 'log\_entries' table, which logs various system events. You can use the TRUNCATE TABLE statement like this:

```sql
TRUNCATE TABLE log_entries;
```

This query efficiently removes all log entries, providing a clean slate for new system events.

By mastering the TRUNCATE TABLE statement, you gain a quick and efficient tool for clearing table data, particularly useful in scenarios where you need to reset or refresh data regularly. Stay tuned for Chapter 12, where we'll explore more advanced topics, including subqueries and joins, taking your SQL skills to the next level. Happy querying!

# **Chapter 12: Advanced SQL Concepts - Subqueries and Joins**

Welcome back to our SQL mastery journey! In the preceding chapters, we've covered a wide array of SQL concepts, including the WHERE clause, operators, LIMIT clause, ORDER BY clause, aggregate functions, GROUP BY clause, HAVING clause, the General Order of SQL statements, data modification operations, and the TRUNCATE TABLE statement. In Chapter 12, we'll delve into more advanced topics—subqueries and joins—unlocking the full potential of your SQL skills.

### 12.1 Subqueries:

A subquery is a query nested within another query, providing a way to perform complex operations and calculations.

#### Basic Syntax:

```sql
SELECT column1, column2, ...
FROM table
WHERE column1 OPERATOR (SELECT column1 FROM another_table WHERE condition);
```

### Examples:

#### Example 12.1.1: Find Employees in Sales Department with High Salaries

Suppose you want to find employees in the 'sales' department with salaries greater than the average salary of all employees. You can use a subquery like this:

```sql
SELECT employee_id, employee_name, salary
FROM employees
WHERE department = 'sales'
  AND salary > (SELECT AVG(salary) FROM employees);
```

This query uses a subquery to calculate the average salary from the 'employees' table and then selects employees in the 'sales' department with salaries greater than that average.

### 12.2 Joins:

Joins combine rows from two or more tables based on a related column between them.

#### Basic Syntax:

```sql
SELECT column1, column2, ...
FROM table1
JOIN table2 ON table1.column = table2.column;
```

### Examples:

#### Example 12.2.1: Retrieve Customer Orders with Product Details

Suppose you want to retrieve information about customer orders, including details about the products ordered. You can use a JOIN like this:

```sql
SELECT customers.customer_id, customers.customer_name, orders.order_id, orders.order_date, products.product_name, order_details.quantity
FROM customers
JOIN orders ON customers.customer_id = orders.customer_id
JOIN order_details ON orders.order_id = order_details.order_id
JOIN products ON order_details.product_id = products.product_id;
```

This query uses multiple JOIN clauses to combine information from the 'customers', 'orders', 'order\_details', and 'products' tables.

### Practical Tips:

* **Understand Types of Joins:** Different types of joins (INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN) cater to different scenarios. Choose the one that fits your requirements.
    
* **Use Subqueries Wisely:** Subqueries can be resource-intensive. Ensure they are necessary and well-optimized, especially when dealing with large datasets.
    

### Putting it into Practice:

Imagine you want to find employees who have placed orders, along with the total number of orders each employee has placed. You can use a subquery and a JOIN like this:

```sql
SELECT employees.employee_id, employees.employee_name, COUNT(orders.order_id) AS total_orders
FROM employees
JOIN orders ON employees.employee_id = orders.employee_id
GROUP BY employees.employee_id, employees.employee_name;
```

This query utilizes a JOIN to combine information from the 'employees' and 'orders' tables and a subquery to calculate the total number of orders placed by each employee.

By incorporating subqueries and joins into your SQL toolkit, you elevate your ability to tackle more complex data scenarios and extract valuable insights from your database. Stay tuned for more advanced topics in Chapter 13, where we'll explore common table expressions (CTEs) and window functions. Happy querying!

**Chapter 13: Common Table Expressions (CTEs) and Window Functions - Mastering Advanced SQL Techniques**

Welcome back to our SQL mastery journey! In the preceding chapters, we've covered a range of SQL concepts, from basic queries to advanced topics like subqueries and joins. In Chapter 13, we'll explore even more powerful and flexible tools—Common Table Expressions (CTEs) and Window Functions.

### 13.1 Common Table Expressions (CTEs):

A Common Table Expression (CTE) is a named temporary result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement.

#### Basic Syntax:

```sql
WITH cte_name (column1, column2, ...) AS (
    -- CTE query
    SELECT column1, column2, ...
    FROM table
    WHERE condition
)
-- Main query using CTE
SELECT *
FROM cte_name;
```

### Examples:

#### Example 13.1.1: Calculate Employee Salaries with a Bonus

Suppose you want to calculate employee salaries with an additional bonus. You can use a CTE like this:

```sql
WITH BonusCTE AS (
    SELECT employee_id, salary * 1.1 AS total_salary
    FROM employees
)
SELECT employees.employee_id, employees.employee_name, BonusCTE.total_salary
FROM employees
JOIN BonusCTE ON employees.employee_id = BonusCTE.employee_id;
```

This query uses a CTE to calculate the total salary with a 10% bonus and then joins the result with the 'employees' table.

### 13.2 Window Functions:

Window functions perform calculations across a set of table rows related to the current row, known as the "window."

#### Basic Syntax:

```sql
SELECT column1, column2, ..., 
       WINDOW_FUNCTION(column3) OVER (PARTITION BY column4 ORDER BY column5)
FROM table;
```

### Examples:

#### Example 13.2.1: Rank Employees by Salary within Each Department

Suppose you want to rank employees by salary within each department. You can use a window function like this:

```sql
SELECT employee_id, employee_name, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS salary_rank
FROM employees;
```

This query uses the RANK window function to assign a rank to employees based on their salary within each department.

### Practical Tips:

* **Optimize CTE Usage:** Use CTEs for better code readability and maintainability, especially when dealing with complex queries.
    
* **Explore Window Function Varieties:** Window functions include various types such as RANK, DENSE\_RANK, ROW\_NUMBER, and aggregate functions with the OVER clause. Familiarize yourself with their use cases.
    

### Putting it into Practice:

Imagine you want to find the average salary of employees in each department along with their individual salaries. You can use a CTE and a window function like this:

```sql
WITH DepartmentAverage AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT employees.employee_id, employees.employee_name, employees.salary,
       DepartmentAverage.avg_salary
FROM employees
JOIN DepartmentAverage ON employees.department_id = DepartmentAverage.department_id;
```

This query calculates the average salary in each department using a CTE and then joins the result with individual employee data.

By incorporating CTEs and window functions into your SQL repertoire, you gain advanced tools for handling complex scenarios and deriving deeper insights from your data. Stay tuned for Chapter 14, where we'll explore more advanced SQL techniques, including pivoting and unpivoting data. Happy querying!

Embark on this journey through the chapters, and you'll emerge with a comprehensive understanding of SQL, equipped to wield its power in your database endeavors. Happy querying!

> ***Next Part will be uploaded soon. So make sure to follow me.***