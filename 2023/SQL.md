
# Basic SQL

## Basic SQL Lesson Overview

In this lesson, we will cover and you will be able to:

-   Describe why SQL is important
-   Explain how SQL data is stored and structured
-   Create SQL queries using proper syntax including
    -   SELECT & FROM
    -   LIMIT
    -   ORDER BY
    -   WHERE
    -   Basic arithmetic operations
    -   LIKE
    -   IN
    -   NOT
    -   AND & BETWEEN & OR

```
SELECT DISTINCT column, AGG_FUNC(_column_or_expression_), … 
FROM mytable 
	JOIN another_table 
	ON mytable.column = another_table.column 
	WHERE _constraint_expression_ 
	GROUP BY column 
	HAVING _constraint_expression_ 
	ORDER BY _column_ ASC/DESC 
	LIMIT _count_ OFFSET _COUNT_;
```


## 9. Types of Statements

The key to SQL is understanding **statements**. A few statements include:

1.  **CREATE TABLE** is a statement that creates a new table in a database.
2.  **DROP TABLE** is a statement that removes a table in a database.
3.  **SELECT** allows you to read data and display it. This is called a **query**.

## 11. SELECT & FROM

## 15. LIMIT

## 18. ORDER BY

The ORDER BY statement always comes in a query after the SELECT and FROM statements, but before the LIMIT statement. If you are using the LIMIT statement, it will always appear last.

Remember `DESC` can be added after the column in your **ORDER BY** statement to sort in descending order, as the default is to sort in ascending order.

## 21. ORDER BY Part II

When you provide a list of columns in an **ORDER BY** command, the sorting occurs using the leftmost column in your list first, then the next column from the left, and so on. We still have the ability to flip the way we order using **DESC**.

## 24. WHERE

Using the **WHERE** statement, we can display _subsets_ of tables based on conditions that must be met. You can also think of the **WHERE** command as _filtering_ the data.

Common symbols used in **WHERE** statements include:

1.  `>` (greater than)
2.  `<` (less than)
3.  `>=` (greater than or equal to)
4.  `<=` (less than or equal to)
5.  `=` (equal to)
6.  `!=` (not equal to)

The **WHERE** statement can also be used with non-numeric data. We can use the `=` and `!=` operators here. You need to be sure to use single quotes (just be careful if you have quotes in the original text) with the text data, not double quotes.

Commonly when we are using **WHERE** with non-numeric data fields, we use the **LIKE**, **NOT**, or **IN** operators. We will see those before the end of this lesson!

## 30. Arithmetic Operators

### Derived Columns

Creating a new column that is a combination of existing columns is known as a **derived** column (or "calculated" or "computed" column). Usually, you want to give a name, or "alias," to your new column using the **AS** keyword.

This derived column, and its alias, are generally only temporary, existing just for the duration of your query. The next time you run a query and access this table, the new column will not be there.

If you are deriving the new column from existing columns using a mathematical expression, then these familiar mathematical operators will be useful:

1.  `*` (Multiplication)
2.  `+` (Addition)
3.  `-` (Subtraction)
4.  `/` (Division)

## 33. Introduction to Logical Operators

In the next concepts, you will be learning about **Logical Operators**. **Logical Operators** include:

1.  **LIKE** This allows you to perform operations similar to using **WHERE** and `=`, but for cases when you might **not** know **exactly** what you are looking for.
2.  **IN** This allows you to perform operations similar to using **WHERE** and `=`, but for more than one condition.
3.  **NOT** This is used with **IN** and **LIKE** to select all of the rows **NOT LIKE** or **NOT IN** a certain condition.
4.  **AND & BETWEEN** These allow you to combine operations where all combined conditions must be true.
5.  **OR** This allows you to combine operations where at least one of the combined conditions must be true.

## 34. LIKE

The **LIKE** operator is extremely useful for working with text. You will use **LIKE** within a **WHERE** clause. The **LIKE** operator is frequently used with `%`. The `%` tells us that we might want any number of characters leading up to a particular set of characters or following a certain set of characters, as we saw with the **google** syntax above. Remember you will need to use single quotes for the text you pass to the **LIKE** operator because these lower and uppercase letters are not the same within the string. Searching for **'T'** is not the same as searching for **'t'**. In other SQL environments (outside the classroom), you can use either single or double-quotes.

## 37. IN

The **IN** operator is useful for working with both numeric and text columns. This operator allows you to use an `=`, but for more than one item of that particular column. We can check one, two, or many column values for which we want to pull data, but all within the same query. In the upcoming concepts, you will see the **OR** operator that would also allow us to perform these tasks, but the **IN** operator is a cleaner way to write these queries.

## 40. NOT

The **NOT** operator is an extremely useful operator for working with the previous two operators we introduced: **IN** and **LIKE**. By specifying **NOT LIKE** or **NOT IN**, we can grab all of the rows that do not meet particular criteria.


## 43. AND and BETWEEN

The **AND** operator is used within a **WHERE** statement to consider more than one logical clause at a time. Each time you link a new statement with an **AND**, you will need to specify the column you are interested in looking at. You may link as many statements as you would like to consider at the same time. This operator works with all of the operations we have seen so far including arithmetic operators (`+`, `*`, `-`, `/`). **LIKE**, **IN**, and **NOT** logic can also be linked together using the **AND** operator.

### BETWEEN Operator

Sometimes we can make a cleaner statement using **BETWEEN** than we can use **AND**. Particularly this is true when we are using the same column for different parts of our **AND** statement. In the previous video, we probably should have used **BETWEEN**.

Instead of writing :

```
WHERE column >= 6 AND column <= 10
```

we can instead write, equivalently:

```
WHERE column BETWEEN 6 AND 10
```

You will notice that using **BETWEEN** is tricky for dates! While **BETWEEN** is generally inclusive of endpoints, it assumes the time is at 00:00:00 (i.e. midnight) for dates. This is the reason why we set the right-side endpoint of the period at '2017-01-01'.

## 46. OR

Similar to the **AND** operator, the **OR** operator can combine multiple statements. Each time you link a new statement with an **OR**, you will need to specify the column you are interested in looking at. You may link as many statements as you would like to consider at the same time. This operator works with all of the operations we have seen so far including arithmetic operators (`+`, `*`, `-`, `/`), **LIKE**, **IN**, **NOT**, **AND**, and **BETWEEN** logic can all be linked together using the **OR** operator.

When combining multiple of these operations, we frequently might need to use parentheses to assure that logic we want to perform is being executed correctly. The video below shows an example of one of these situations.

# SQL Joins

## Lesson Overview

In this lesson you will be:

-   Creating Joins
-   Using Primary - Foreign Keys
-   Integrating Aliases
-   Evaluating Various Join Types
-   Integrating Filters with Joins

### Database Normalization

When creating a database, it is really important to think about how data will be stored. This is known as **normalization**, and it is a huge part of most SQL classes. If you are in charge of setting up a new database, it is important to have a thorough understanding of database **normalization**.

There are essentially three ideas that are aimed at database normalization:

1.  Are the tables storing logical groupings of the data?
2.  Can I make changes in a single location, rather than in many tables for the same information?
3.  Can I access and manipulate data quickly and efficiently?

This is discussed in detail [here](https://www.itprotoday.com/sql-server/sql-design-why-you-need-database-normalization).

However, most analysts are working with a database that was already set up with the necessary properties in place. As analysts of data, you don't really need to think too much about data **normalization**. You just need to be able to pull the data from the database, so you can start making insights. This will be our focus in this lesson.

## 3. Introduction to JOINs

```sql
SELECT orders.*,
       accounts.*
FROM orders 
JOIN accounts
ON orders.account_id = accounts.id;

```

The way we join any two tables is in this way: linking the **PK** and **FK** (generally in an **ON** statement).

### JOIN More than Two Tables

```sql
SELECT *
FROM web_events
JOIN accounts
ON web_events.account_id = accounts.id
JOIN orders
ON accounts.id = orders.account_id
```


## 10. Alias

Example:

```sql
FROM tablename AS t1
JOIN tablename2 AS t2
```

Before, you saw something like:

```sql
SELECT col1 + col2 AS total, col3
```

## 14. LEFT and RIGHT JOINs

Notice each of these new **JOIN** statements pulls all the same rows as an **INNER JOIN**, which you saw by just using **JOIN**, but they also potentially pull some additional rows.

If there is not matching information in the **JOIN**ed table, then you will have columns with empty cells. These empty cells introduce a new data type called **NULL**. You will learn about **NULL**s in detail in the next lesson, but for now you have a quick introduction as you can consider any cell without data as **NULL**.

**Query1**

```sql
SELECT a.id, a.name, o.total
FROM orders o
LEFT JOIN accounts a
ON o.account_id = a.id
```

**Query2**

```sql
SELECT a.id, a.name, o.total
FROM orders o
RIGHT JOIN accounts a
ON o.account_id = a.id
```

You might see the SQL syntax of

```
LEFT OUTER JOIN
```

OR

```
RIGHT OUTER JOIN
```

### OUTER JOINS

The last type of join is a full outer join. This will return the inner join result set, as well as any unmatched rows from either of the two tables being joined.

Again this returns rows that **do not match** one another from the two tables. The use cases for a full outer join are **very rare**.

You can see examples of outer joins at the link [here](http://www.w3resource.com/sql/joins/perform-a-full-outer-join.php) and a description of the rare use cases [here](https://stackoverflow.com/questions/2094793/when-is-a-good-situation-to-use-a-full-outer-join). We will not spend time on these given the few instances you might need to use them.

Similar to the above, you might see the language **FULL OUTER JOIN**, which is the same as **OUTER JOIN**.

## 18. JOINs and Filtering

A simple rule to remember is that, when the database executes this query, it executes the join and everything in the **ON** clause first. Think of this as building the new result set. That result set is then filtered using the **WHERE** clause.

**Query1**

```sql
SELECT orders.*, accounts.*
FROM orders
LEFT JOIN accounts
ON orders.account_id = accounts.id 
WHERE accounts.sales_rep_id = 321500
```

**Query2**

```sql
SELECT orders.*, accounts.*
FROM orders
LEFT JOIN accounts
ON orders.account_id = accounts.id 
AND accounts.sales_rep_id = 321500
```

## Recap

You learned a key element for **JOIN**ing tables in a database has to do with primary and foreign keys. Choosing the set up of data in our database is very important, but not usually the job of a data analyst. This process is known as **Database Normalization**.

You learned how to combine data from multiple tables using **JOIN**s. The three **JOIN** statements you are most likely to use are: JOIN, LEFT JOIN, RIGHT JOIN.

There are a few more advanced **JOIN**s that we did not cover here, and they are used in very specific use cases. [UNION and UNION ALL](https://www.w3schools.com/sql/sql_union.asp), [CROSS JOIN](http://www.w3resource.com/sql/joins/cross-join.php), and the tricky [SELF JOIN](https://www.w3schools.com/sql/sql_join_self.asp). These are more advanced than this course will cover, but it is useful to be aware that they exist, as they are useful in special cases.

You also learned that you can alias tables and columns using **AS** or not using it. This allows you to be more efficient in the number of characters you need to write, while at the same time you can assure that your column headings are informative of the data in your table.


# SQL Aggregations

In this lesson, we will cover and you will be able to:

-   Deal with NULL values
-   Create aggregations in your SQL Queries including
    -   COUNT
    -   SUM
    -   MIN & MAX
    -   AVG
    -   GROUP BY
    -   DISTINCT
    -   HAVING
-   Create DATE functions
-   Implement CASE statements

## 1. Nulls

**NULLs** are a datatype that specifies where no data exists in SQL. They are often ignored in our aggregation functions, which you will get a first look at in the next concept using **COUNT**.

Notice that **NULL**s are different than a zero - they are cells where data does not exist.

When identifying **NULL**s in a **WHERE** clause, we write **IS NULL** or **IS NOT NULL**. We don't use `=`, because **NULL** isn't considered a value in SQL. Rather, it is a property of the data.

## 5. COUNT & NULLs
Notice that **COUNT** does not consider rows that have **NULL** values. Therefore, this can be useful for quickly identifying which rows have missing data.

## 6. SUM

Unlike **COUNT**, you can only use **SUM** on numeric columns. However, **SUM** will ignore **NULL** values, as do the other aggregation functions you will see in the upcoming lessons.

## 9. MIN & MAX

```sql
SELECT MIN(standard_qty) AS standard_min,
       MIN(gloss_qty) AS gloss_min,
       MIN(poster_qty) AS poster_min,
       MAX(standard_qty) AS standard_max,
       MAX(gloss_qty) AS gloss_max,
       MAX(poster_qty) AS poster_max
FROM   orders
```

Notice that **MIN** and **MAX** are aggregators that again ignore **NULL** values. Check the expert tip below for a cool trick with **MAX** & **MIN**.

### Expert Tip

Functionally, **MIN** and **MAX** are similar to **COUNT** in that they can be used on non-numerical columns. Depending on the column type, **MIN** will return the lowest number, earliest date, or non-numerical value as early in the alphabet as possible. As you might suspect, **MAX** does the opposite—it returns the highest number, the latest date, or the non-numerical value closest alphabetically to “Z.”

## 10. AVG


```sql
SELECT AVG(standard_qty) AS standard_avg,
       AVG(gloss_qty) AS gloss_avg,
       AVG(poster_qty) AS poster_avg
FROM orders
```

Similar to other software **AVG** returns the mean of the data - that is the sum of all of the values in the column divided by the number of values in a column. This aggregate function again ignores the **NULL** values in both the numerator and the denominator.

If you want to count **NULL**s as zero, you will need to use **SUM** and **COUNT**. However, this is probably not a good idea if the **NULL** values truly just represent unknown values for a cell.

### MEDIAN - Expert Tip

One quick note that a median might be a more appropriate measure of center for this data, but finding the median happens to be a pretty difficult thing to get using SQL alone — so difficult that finding a median is occasionally asked as an interview question.

## 13. GROUP BY

```sql
SELECT account_id,
       SUM(standard_qty) AS standard,
       SUM(gloss_qty) AS gloss,
       SUM(poster_qty) AS poster
FROM orders
GROUP BY account_id
ORDER BY account_id
```

The key takeaways here:

-   **GROUP BY** can be used to aggregate data within subsets of the data. For example, grouping for different accounts, different regions, or different sales representatives.

-   Any column in the **SELECT** statement that is not within an aggregator must be in the **GROUP BY** clause.

-   The **GROUP BY** always goes between **WHERE** and **ORDER BY**.

-   **ORDER BY** works like **SORT** in spreadsheet software.

### GROUP BY - Expert Tip

Before we dive deeper into aggregations using **GROUP BY** statements, it is worth noting that SQL evaluates the aggregations before the **LIMIT** clause. If you don’t group by any columns, you’ll get a 1-row result—no problem there. If you group by a column with enough unique values that it exceeds the **LIMIT** number, the aggregates will be calculated, and then some rows will simply be omitted from the results.

Key takeaways:

-   You can **GROUP BY** multiple columns at once, as we showed here. This is often useful to aggregate across a number of different segments.

-   The order of columns listed in the **ORDER BY** clause does make a difference. You are ordering the columns from left to right.

### GROUP BY - Expert Tips

-   The order of column names in your **GROUP BY** clause doesn’t matter—the results will be the same regardless. If we run the same query and reverse the order in the **GROUP BY** clause, you can see we get the same results.

-   As with **ORDER BY**, you can substitute numbers for column names in the **GROUP BY** clause. It’s generally recommended to do this only when you’re grouping many columns, or if something else is causing the text in the GROUP BY clause to be excessively long.

-   A reminder here that any column that is not within an aggregation must show up in your GROUP BY statement. If you forget, you will likely get an error. However, in the off chance that your query does work, you might not like the results!

## 19. DISTINCT

**DISTINCT** is always used in **SELECT** statements, and it provides the unique rows for all columns written in the **SELECT** statement. Therefore, you only use **DISTINCT** once in any particular **SELECT** statement.

You could write:

```sql
SELECT DISTINCT column1, column2, column3
FROM table1;
```

which would return the unique (or **DISTINCT**) rows across all three columns.

### DISTINCT - Expert Tip

It’s worth noting that using **DISTINCT**, particularly in aggregations, can slow your queries down quite a bit.

## 22. HAVING

### HAVING - Expert Tip

**HAVING** is the “clean” way to filter a query that has been aggregated, but this is also commonly done using a [subquery](https://mode.com/sql-tutorial/sql-sub-queries/). Essentially, any time you want to perform a **WHERE** on an element of your query that was created by an aggregate, you need to use **HAVING** instead.

```sql
SELECT account_id,
       SUM(total_amt_usd) AS sum_total_amt_usd
FROM orders
GROUP BY 1
HAVING SUM(total_amt_usd) >= 250000
```

## 25. DATE Functions

**DATE_TRUNC** allows you to truncate your date to a particular part of your date-time column. Common truncations are `day`, `month`, and `year`. [Here](https://blog.modeanalytics.com/date-trunc-sql-timestamp-function-count-on/) is a great blog post by Mode Analytics on the power of this function.

**DATE_PART** can be useful for pulling a specific portion of a date, but notice pulling `month` or day of the week (`dow`) means that you are no longer keeping the years in order. Rather you are grouping for certain components regardless of which year they belonged in.

For additional functions you can use with dates, check out the documentation [here](https://www.postgresql.org/docs/9.1/static/functions-datetime.html), but the **DATE_TRUNC** and **DATE_PART** functions definitely give you a great start!

## 29. CASE Statements

```sql
SELECT id,
       account_id,
       occurred_at,
       channel,
       CASE WHEN channel = 'facebook' THEN 'yes' ELSE 'no' END AS is_facebook
FROM web_events
ORDER BY occurred_at
```

```sql
SELECT account_id,
       occurred_at,
       total,
       CASE WHEN total > 500 THEN 'Over 500'
            WHEN total > 300 AND total <= 500 THEN '301 - 500'
            WHEN total > 100 AND total <=300 THEN '101 - 300'
            ELSE '100 or under' END AS total_group
FROM orders
```

### CASE - Expert Tip

-   The CASE statement always goes in the SELECT clause.

-   CASE must include the following components: WHEN, THEN, and END. ELSE is an optional component to catch cases that didn’t meet any of the other previous CASE conditions.

-   You can make any conditional statement using any conditional operator (like [WHERE](https://mode.com/resources/sql-tutorial/sql-where)) between WHEN and THEN. This includes stringing together multiple conditional statements using AND and OR.

-   You can include multiple WHEN statements, as well as an ELSE statement again, to deal with any unaddressed conditions.

## 30. CASE & Aggregations

```sql
SELECT CASE WHEN total > 500 THEN 'OVer 500'
            ELSE '500 or under' END AS total_group,
            COUNT(*) AS order_count
FROM orders
GROUP BY 1
```


# SQL Subqueries & Temporary Tables

This lesson will focus on the following components of subqueries, and you will be able to:

-   Create subqueries to solve real-world problems
-   Differentiate between Subqueries and Joins
-   Implement the best type of Subqueries
-   Consider the tradeoffs to using subqueries
-   Implement the best subquery strategy

#### What exactly is a subquery?

A subquery is a query _within_ a query.

-   As a reminder, a query has both **SELECT** and **FROM** clauses to signify what you want to extract from a table and what table you’d like to pull data from. A query that includes subquery, as a result, has multiple **SELECT** and **FROM** clauses.
-   The subquery that sits nested inside a larger query is called an **INNER QUERY**. This inner query can be fully executed on its own and often is run independently before when trying to troubleshoot bugs in your cod

```sql
SELECT product_id,
       name,
       price
FROM db.product
Where price > (SELECT AVG(price)
              FROM db.product)
```

#### **When do you need to use a subquery?**

You need to use a subquery when you have the need to manipulate an existing table to “pseudo-create” a table that is then used as a part of a larger query. In the examples below, existing tables cannot be joined together to solve the problem at hand. Instead, an existing table needs to be manipulated, massaged, or aggregated in some way to then join to another table in the dataset to answer the posed question.

### Differences between Subqueries and Joins

#### Use Cases:

_Subquery:_ When an existing table needs to be manipulated or aggregated to then be joined to a larger table.

_Joins:_ A fully flexible and discretionary use case where a user wants to bring two or more tables together and select and filter as needed.

#### Syntax:

_Subquery:_ A subquery is a query within a query. The syntax, as a result, has multiple **SELECT** and **FROM** clauses.

_Joins:_ A join is simple stitching together multiple tables with a common key or column. A join clause cannot stand and be run independently.

#### Dependencies:

_Subquery:_ A subquery clause can be run completely independently. When trying to debug code, subqueries are often run independently to pressure test results before running the larger query.

_Joins:_ A join clause cannot stand and be run independently.

### Similarities between Subqueries and Joins

#### Output:

Both subqueries and joins are essentially bringing multiple tables together (whether an existing table is first manipulated or not) to generate a single output.

## 4. Subqueries and Joins Deep-dives

https://youtu.be/4N84LWhuQEg

The following comparison will help iterate again the differences between subqueries and joins.

#### Subqueries:

**Output:** Either a scalar (a single value) or rows that have met a condition. **Use Case:** Calculate a scalar value to use in a later part of the query (e.g., average price as a filter). **Dependencies:** Stand independently and be run as complete queries themselves.

#### Joins:

**Output:** A joint view of multiple tables stitched together using a common “key”. **Use Case:** Fully stitch tables together and have full flexibility on what to “select” and “filter from”. **Dependencies:** Cannot stand independently.

## 5. Subquery Basics

https://youtu.be/K2UdKf3_izA

### Fundamentals to Know about Subqueries:

-   Subqueries must be fully placed inside parentheses.
-   Subqueries must be fully independent and can be executed on their own
-   Subqueries have two components to consider:
    -   Where it’s placed
    -   Dependencies with the outer/larger query

**A caveat with subqueries being independent:**

In almost all cases, subqueries are fully independent. They are "interim”/temp tables that can be fully executed on their own. **However, there is an exception.** When a subquery, _typically in the form of a nested or inline subquery_, is correlated to its outer query, it cannot run independently. This is most certainly an edge case since correlated subqueries are rarely implemented compared to standalone, simple subqueries.

### Placement:

There are four places where subqueries can be inserted within a larger query:

-   With
-   Nested
-   Inline
-   Scalar

### Dependencies:

A subquery can be **dependent** on the outer query or **independent** of the outer query.

## 6. Subqueries: Placement

https://youtu.be/v3QFqBqI5lE

The key concept of placement is where exactly the subquery is placed within the context of the larger query. There are four different places where a subquery can be inserted. From my experience, the decision of which placement to leverage stems from (1) the problem at hand and (2) the readability of the query.

### Subquery Placement:

**With:** This subquery is used when you’d like to “pseudo-create” a table from an existing table and **visually scope** the temporary table at the top of the larger query.

**Nested:** This subquery is used when you’d like the temporary table to act as a filter within the larger query, which implies that it often sits within the **where clause.**

**Inline:** This subquery is used in the same fashion as the **WITH** use case above. However, instead of the temporary table sitting on top of the larger query, it’s embedded within the **from clause.**

**Scalar:** This subquery is used when you’d like to generate a scalar value to be used as a benchmark of some sort.

For example, when you’d like to calculate the average salary across an entire organization to compare to individual employee salaries. Because it’s often a single value that is generated and used as a benchmark, the scalar subquery often sits within the **select clause.**

### Advantages:

**Readability:** `With` and `Nested` subqueries are most advantageous for readability.

**Performance:** `Scalar` subqueries are advantageous for performance and are often used on smaller datasets.

## 7. Your First Subquery

https://youtu.be/cTM1jPYXLoQ

```sql
SELECT channel,
       AVG(event_count) AS avg_event_count
FROM
(SELECT DATE_TRUNC('day',occurred_at) AS day,
        channel,
        count(*) as event_count
   FROM web_events
   GROUP BY 1,2
   ) sub
   GROUP BY 1
   ORDER BY 2 DESC
```

In the video above, we review what it’s really like to build and execute a subquery. You’ll notice the following order of operations.

1.  **Build the Subquery:** The aggregation of an existing table that you’d like to leverage as a part of the larger query.
2.  **Run the Subquery:** Because a subquery can stand independently, it’s important to run its content first to get a sense of whether this aggregation is the interim output you are expecting.
3.  **Encapsulate and Name:** Close this subquery off with parentheses and call it something. In this case, we called the subquery table ‘sub.’
4.  **Test Again:** Run a `SELECT *` within the larger query to determine if all syntax of the subquery is good to go.
5.  **Build Outer Query:** Develop the `SELECT *` clause as you see fit to solve the problem at hand, leveraging the subquery appropriately.

