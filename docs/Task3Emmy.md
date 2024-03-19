# Querying databases with SELECT statement
## Overview
[Relational Database Management System](https://www.techtarget.com/searchdatamanagement/definition/RDBMS-relational-database-management-system) is a program allow you to create [databases](https://en.wikipedia.org/wiki/Database), data tables, insert data into tables, edit, update, retrieve, delete data from tables, and manage user's permission. 

It includes [five(5) main sets of SQL commands](https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/) which are using frequently in MySQL:

* Data Definition Language(DDL)
    * CREATE
    * ALTER
    * DROP
    
* Data Query Language (DQL)
    * SELECT

* Data Manipulation Language (DML)
    * INSERT
    * UPDATE
    * DELETE

* Data Control Language (DCL)
    * CREATE USER
    * GRANT
    * REVOKE

* Transaction Control Language (TCL)
    * BEGIN
    * COMMIT
    * ROLLBACK

The goal of this section is walk you through a basic instruction of using SELECT command in Data Query Language of MySQL to retrieve data from databases. 

## Basic structure of SELECT statement

Basic SELECT statement in MySQL comes with five(5) clauses. To memorize the order of SQL queries, you can choose either this sentence _"Some French Waiters Grow Healthy Oranges"_ or _"Sweaty Feet Will Give Horrible Odours!"_, where the initial characters of this sentence align with those of SELECT statement :smile: :

!!! tips "Tip"
    <pre>
    **S**elect              **S**ome              **S**weaty
    **F**rom                **F**rench            **F**eet
    **W**here               **W**aiters           **W**ill
    **G**roup by            **G**row              **G**ive
    **H**aving              **H**ealthy           **H**orrible
    **O**rder by            **O**ranges           **O**dours
    </pre>

When writing a query, all clauses in the SELECT statement apart from SELECT itself are considered optional. Each of these optional clauses can either be included, combined, or omitted as needed.

## SQL Query order of execution
In SQL, the order you write the code isn't the same as how it executes. So, to understand how an SQL query works, it's important to know the right [SQL execution structure](https://matam-kirankumar.medium.com/sql-query-order-of-execution-37001da1462). Then, you can user certain keywords when writing the query. 



| What the query looks like |How it's executed            |    Why it works this way   |
|------------------------|---------------------------|-------------------------------|
| `SELECT` | :octicons-triangle-down-16: `FROM`    | SQL starts with which table your query is taking data from|
| `FROM`  | :octicons-triangle-down-16: `WHERE`   | This is how SQL filters on rows.|
| `WHERE`  | :octicons-triangle-down-16: `GROUP BY`| This is where your SQL query checks if you have an aggregation.|
| `GROUP BY`  | :octicons-triangle-down-16: `HAVING`  | `HAVING` requires a `GROUP BY` statement. |
| `HAVING`   | :octicons-triangle-down-16: `SELECT`  | Only after all these calculations have made will SQL `SELECT` which columns you want to see returned.|
| `ORDER BY`  | :octicons-triangle-down-16: `ORDER BY`| This sorts the data returned.|
| `LIMIT`    | :octicons-triangle-down-16: `LIMIT`   | Lastly, you can limit the number of rows returned.|
|||_source: [SQL Query Order of Execution](https://matam-kirankumar.medium.com/sql-query-order-of-execution-37001da1462), Kiran Kumar, Medium(2022)_|

## Examples of using SELECT statements

### Initial set up
Before exploring the simpliest SELECT statements, you need to initally set up

1. Open MySQL Workbench

2. Choose your MySQL database by **clicking** on the connection.

    In my example, I choose my localhost `Local instance 3306`

    ![Open MySQL](/assets/openMySQL.png){width="500"}

    !!! note
        The connection you choose is where you have the database

3. Fill in your username and password to login your connection

    ![Login MySQL Workbench](/assets/userPassword.png){width="500"}

4. Choose the schema you want to work on by **right clicking** on the schema's name, **click**  [Set as Default Schema].

    Another way to do that, **click** [File], **choose** [Open SQL Script], and type `USE` < schema's name > in query script.

Now, you are all set to dive in SELECT statements in the following sections:


### SELECT *

`SELECT` used with an asterisk `(*)` will return all rows and all columns from the table we're quering

1. Add the query below in SQL script:

    === "Query"

        ```sql linenums="1"
        SELECT * 
        FROM < table >
        ```

    === "Example"

        ``` sql linenums="1"
        SELECT * 
        FROM customer;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT ALL](/assets/selectAll.png){ width="500" }

!!! note
    * ![Lightning Bolt button](/assets/lightningBtn.png){width="20"}: Use this button when you want to run many queries at the same time.

    * ![Lightning Bolt button with cursor](/assets/lightningBtnWithCursor.png){width="20"}: Use this button when you want to run ONLY ONE specific query.


### FROM

Using `FROM` will show all rows and **some** columns from a single table

1. Add the query below in SQL script:

    === "Query"

        ```sql linenums="1"
        SELECT {colum1, column2} 
        FROM <table>
        ```

    === "Example"

        ``` sql linenums="1"
        SELECT v_name, v_areacode, v_phone, v_state 
        FROM vendor;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT FROM](/assets/selectFrom.png){ width="500" }


Show all rows and **combine** some columns from a single table. You can set a name for this combined column using `CONCAT` and `AS` followed by a name (a.k.a an `alias`) enclosed in double quote `" "`.

1. Add the query below in SQL script:

    === "Query"

        ```sql linenums="1" hl_lines="2"
        SELECT 
            CONCAT(colum1,' ', column2) AS "name"
        FROM <table>
        ```

    === "Example"

        ``` sql linenums="1" hl_lines="2 3"
        SELECT 
            CONCAT(CUS_LNAME, ' ', CUS_FNAME) AS "Name",
            CONCAT(CUS_AREACODE, ' ', CUS_PHONE) AS "Fullphone"
        FROM customer;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT CONCAT](/assets/selectConcat.png){ width="500" }

### ORDER BY

Display all rows from a single table in a specific sequence. You can indicate the sorting arrangement using the `ORDER BY` clause.

1. Add the query below in SQL script:

    === "Query"

        ``` sql linenums="1"
        SELECT { * | column1, column2 }
        FROM <table>
        ORDER BY <columnA>; -- (1)!
        ```

        1. :woman_raising_hand: columnA __does not need__ to match the { column1, column2,... } list in SELECT clause.

    === "Example"

        ``` sql linenums="1"
        SELECT P_CODE, P_DESCRIPT, P_PRICE
        FROM PRODUCT
        ORDER BY P_PRICE DESC; -- (1)!
        ```

        1. :woman_raising_hand: The default order in the `ORDER BY` clause is __ascending__. You can choose to include the keyword ASC after the column name, but it's optional. Additionally, using `DESC` specifies __descending__ order.

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT ORDER BY](/assets/selectOrderDesc.png){ width="500" }

In the `ORDER BY` clause, you can specify multiple columns for sorting, and the order will proceed sequentially from the first column onward.

1. Add the query below in SQL script:

    === "Query"

        ``` sql linenums="1" hl_lines="3"
        SELECT { * | column1, column2 }
        FROM <table>
        ORDER BY { columnA, columnB };
        ```

    === "Example"

        ``` sql linenums="1" hl_lines="3"
        SELECT CUS_LNAME, CUS_FNAME, CUS_INITIAL
        FROM CUSTOMER
        ORDER BY CUS_LNAME, CUS_FNAME;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT ORDER BY multiple columns](/assets/selectOrderMulti.png){ width="500" }

### WHERE

Using `WHERE` clause to filter the rows from a table based on specified condition.

1. Add the query below in SQL script:

    === "Query"

        ``` sql linenums="1" hl_lines="3"
        SELECT { * | column1, column2 }
        FROM <table>
        WHERE <condition>;
        ```

    === "Example"

        ``` sql linenums="1" hl_lines="3"
        SELECT CUS_CODE, CUS_LNAME, CUS_FNAME, CUS_AREACODE, CUS_PHONE
        FROM CUSTOMER
        WHERE CUS_FNAME = 'Anne' OR CUS_LNAME = 'Brown';
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT WHERE](/assets/selectWhere.png){ width="500" }


!!!note

    * [Conditions]((https://www.w3schools.com/mysql/mysql_operators.asp)) can be expressed in various forms:
        * Comparison operators
        * Logical operators
        * Ranges
        * Lists of values indicated by
        * Pattern matching

    * [NULL values](https://www.w3schools.com/mysql/mysql_null_values.asp)


### GROUP BY

Using `GROUP BY` clause to group rows with the same value. This clause is usually used with [aggregate functions](https://www.w3schools.com/sql/sql_aggregate_functions.asp#:~:text=An%20aggregate%20function%20is%20a,clause%20of%20the%20SELECT%20statement.).

1. Add the query below in SQL script:

    === "Query"

        ``` sql linenums="1" hl_lines="3"
        SELECT <AGGREGATE(column1)> { columnA, columnB...} -- (1)!
        FROM <table>
        GROUP BY { columnA, columnB };
        ```
        
        1. Replace __AGGREGATE__ with one of the five(5) aggregate functions.

    === "Example"

        ``` sql linenums="1" hl_lines="3"
        SELECT V_STATE, COUNT(*) AS 'Count by State'
        FROM VENDOR
        GROUP BY V_STATE;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT GROUP BY](/assets/selectGroupby.png){ width="500" }

### HAVING

Using `HAVING` clause in SQL to filter the results of grouped data based on specified conditions. It's often used after the `GROUP BY` clause to apply conditions to the groups created by `GROUP BY`. Specifically, `HAVING` is used to filter groups based on aggregate values, such as `SUM`, `COUNT`, `AVG`, `MAX`, `MIN`, etc.

1. Add the query below in SQL script:

    === "Query"

        ``` sql linenums="1" hl_lines="4"
        SELECT <AGGREGATE(column1)> { columnA, columnB...} -- (1)!
        FROM <table>
        GROUP BY { columnA, columnB }
        HAVING <restriction>;
        ```
        
        1. Replace __AGGREGATE__ with one of the five(5) aggregate functions.

    === "Example"

        ``` sql linenums="1" hl_lines="4"
        SELECT EMP_LNAME, COUNT(*)
        FROM employee
        GROUP BY EMP_LNAME
        HAVING COUNT(*) >= 2;
        ```

2. **Click** ![Lightning Button](/assets/lightningBtn.png){width="20"} to run the query:

!!! success
    ![SELECT HAVING](/assets/selectHaving.png){ width="500" }

!!! success "Congratulation :clap:"
    Now that you're familiar with the simplest SELECT statements in MySQL, you can further practice and enhance your skills by exploring the following resources:

    * [SQL Bolt](https://sqlbolt.com/)
    * [SQL Zoo](https://sqlzoo.net/wiki/SQL_Tutorial)
    * [SQL Practice](https://www.sql-practice.com/)

    Happy practicing! :wink:

## Conclusion

By going through this section, you will achieve the following:

* Getting acknowledgement about 5 sets of SQL commands
* Understanding and proficiency in writing the simplest SELECT statements

Great work! :heart: If you encounter any issues while running MySQL queries, be sure to check out the next section for assistance:



