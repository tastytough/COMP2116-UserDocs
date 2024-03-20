# Introduction

Welcome! :wave: This guide aims to familiaze you with the essential concept of working with databases, including understanding data types, creating schemas and tables, setting up MySQL Workbench, and executing simple SELECT statements. This documentation will provide you with the basic knowledge to get started with MySQL in general and MySQL WorkBench in details.

> ![MySQL logo](/assets/mysql-logo-2.png){ width="50" } [**MySQL Workbench**](https://www.mysql.com/products/workbench/) is a visual database design tool that integrates SQL development, administration, database design, creation and maintenance into a single integrated development environment for the [MySQL](https://www.mysql.com/) database system.

## Intended Users

This documentation is intended for:

- New users to MySQL to learn about databases

- Second-term Full-stack Web Development student of BCIT.

## Prerequisite Knowledge

- Having a basic knowledge of Microsoft Excel
  - know how to create a simple table with data in rows and columns.
  - how to format a table, and what data type should be in a specific cell.
- Set up a connection from MySQL Workbench to MySQL server.

## Software Requirements

- [MySQL Server 8.0](https://dev.mysql.com/downloads/installer/)

- [MySQL Workbench 8.0](https://dev.mysql.com/downloads/installer/)

!!! info
MySQL Workbench and Server can be found in the same installation wizard

## Procedures Overview

Here's a summary of the main sections covered in the documentation:

- ABC
- BCD
- XYZ

## Typographical Conventions

1.  When you see **bold text**, it’s a mouse action:

    E.g **Click** [File, New Query Tab] to create a new query tab to type commands for your table.

2.  When you see [square brackets], it’s action on MySQL Workbench:

    E.g **Right click** on [Table], **click** [Create Table] to create a new table in `test-constrainst-e-nguyen schema`.

3.  Some queries have a clickable `+` button to show more explanation for these queries:

    ```sql linenums="1"
    SELECT P_CODE, P_DESCRIPT, P_PRICE
    FROM PRODUCT
    ORDER BY P_PRICE DESC; -- (1)!
    ```

    1. :woman_raising_hand: The default order in the `ORDER BY` clause is **ascending**. You can choose to include the keyword ASC after the column name, but it's optional. Additionally, using `DESC` specifies **descending** order.

4.  Some queries have a highlight line to show a modified code compared with the previous one to let you know the changes:

    ```sql linenums="1" hl_lines="3"
    SELECT V_STATE, COUNT(*) AS 'Count by State'
    FROM VENDOR
    GROUP BY V_STATE;
    ```

5.  Each example will include a content tab with the query structure and a real-life example:
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

6. File names, schemas, tables are shown as a same format: `test-constrainst-e-nguyen`

## Notes and Warning Messages

!!! note
Indicates important information.

!!! info
Indicates additional information.

!!! tips
Some helpful tips to enhance your understanding.

!!! warning
Some content need to read carefully before proceeding.

!!! success
Indicates successful results.

## Objective of Documentation

- Understand Entity-Relationship Diagrams (ERD) and create them.
- Familiarize yourself with data types commonly used in databases.
- Comprehend the concepts of primary keys and foreign keys in database design.
- Explore the relationships between different tables within a database.
- Learn the process of normalizing database tables.
- Recognize the characteristics of both poor and effective data structures.
- Master the techniques for storing data in databases efficiently.
- Gain proficiency in retrieving data from databases.
- Practice querying using the SELECT statement with single tables.
