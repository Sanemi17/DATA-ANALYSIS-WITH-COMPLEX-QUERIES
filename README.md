# DATA-ANALYSIS-WITH-COMPLEX-QUERIES

COMPANY NAME: CODTECH IT SOLUTIONS

NAME: SANEMI VALECHA

INTERN ID:  CT04DZ135

DOMAIN NAME: SQL INTERNSHIP

DURATION: 4 WEEKS

MENTOR NAME: NEELA SANTOSH


In any data-driven application, extracting actionable insights from stored data is essential. Simple SELECT queries are useful for basic retrieval, but complex business requirements often need more advanced techniques. Task 2 of the SQL Internship was centered around learning and applying advanced SQL query structures, particularly window functions, subqueries, and common table expressions (CTEs). These tools enable more powerful and readable queries when working with large or relational datasets.

The focus of this task was to move beyond the basics and explore analytical querying, which is commonly used in real-world applications like financial reporting, employee performance tracking, e-commerce data analytics, and more. I worked with a sample table called Sales, which contained fields like SaleID, EmployeeID, Amount, and SaleDate. Using this table, I demonstrated each advanced concept by writing real queries and interpreting the results.

🔹 Window Functions
Window functions allow you to perform calculations across a set of rows related to the current row. Unlike aggregate functions (like SUM or AVG) that group rows together, window functions keep each row intact and simply add extra calculated columns.

I used a SUM window function with a PARTITION BY clause to calculate a running total of sales for each employee. This is extremely useful in performance tracking, leaderboard creation, and monthly revenue breakdowns.

Example used:

sql
Copy
Edit
SELECT 
  EmployeeID,
  SaleDate,
  Amount,
  SUM(Amount) OVER (PARTITION BY EmployeeID ORDER BY SaleDate) AS RunningTotal
FROM Sales;
This query returned a list of sales for each employee along with a cumulative total — a powerful feature that traditional GROUP BY queries can't achieve in one go.

🔹 Subqueries
Subqueries are queries nested inside another SQL query. They are used to break complex logic into simpler, nested parts, and are particularly helpful for filtering and comparisons.

In this task, I wrote a subquery to find the highest sale made by each employee. This helped reinforce the concept of correlated subqueries — those that reference a column from the outer query.

Example used:

sql
Copy
Edit
SELECT *
FROM Sales S
WHERE Amount = (
    SELECT MAX(Amount)
    FROM Sales
    WHERE EmployeeID = S.EmployeeID
);
This returned only those sales that were the maximum for each respective employee. Subqueries like these are commonly used in dashboards to show "top" performers or records.

🔹 Common Table Expressions (CTEs)
CTEs are temporary result sets defined within a query using the WITH keyword. They improve readability and allow recursive logic, simplifying complex nested queries. I used a CTE to calculate the average sale amount per employee and then selected only those sales that were above the average.

Example used:

sql
Copy
Edit
WITH AvgSales AS (
  SELECT EmployeeID, AVG(Amount) AS AvgAmount
  FROM Sales
  GROUP BY EmployeeID
)
SELECT S.EmployeeID, S.Amount, A.AvgAmount
FROM Sales S
JOIN AvgSales A ON S.EmployeeID = A.EmployeeID
WHERE S.Amount > A.AvgAmount;
This example shows how CTEs can be used to create intermediate results and write clearer, more modular queries. They’re heavily used in real-world enterprise reporting and ETL (Extract, Transform, Load) operations.

🧠 What I Learned
This task was extremely valuable in making me comfortable with advanced SQL concepts. I learned how:

Window functions give richer insights with just one query

Subqueries allow filtering based on grouped or calculated data

CTEs make multi-step queries easier to write and understand

I also learned about performance considerations, such as how using CTEs or subqueries can sometimes improve or reduce query efficiency depending on the situation.

🔍 Real-World Use Cases
These techniques are used daily in:

Financial systems (e.g., cumulative interest, balance tracking)

HR analytics (e.g., top-performing employees)

E-commerce platforms (e.g., customers who purchased above average)

BI dashboards (e.g., trend analysis and partitioned reports)

✅ Conclusion
Task 2 helped me understand the depth and power of SQL as a language for not just data retrieval, but true data analysis. It laid the foundation for writing cleaner, more effective SQL queries that mirror what is used in the industry for performance tracking, trend evaluation, and advanced filtering. Mastering these tools has given me confidence to handle larger, more complex datasets.


OUTPUTS

"https://github.com/user-attachments/assets/6027e19c-3b10-4ca5-85c3-b41c9237c438"


