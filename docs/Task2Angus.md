# Creating a schema and Creating a table
## Overview
In this section, you will learn how to create a schema, and add a table to a schema to...

## Creating a Schema
1. Open MySQL Workbench

!!! warning 
    When opening MySQL Workbench, you will first see your connections page. Due to the limitations of our documentation, an understanding on configuring your MySQL server and how to configure a connection is not covered.

2. Using your previously configured connection, connect to your MySQL database.

3. In the navigator panel (by default on the left hand side of the window), right click within the space of the window and from the dropdown menu, select create schema. A new panel should appear in the main area of the application.
** ensure that you are in the Schemas tab and not the Administration tab (option at the bottom of the navigator section)

4. In the new panel, you can specify a name for your Schema. Once you've settled on a name, click on the apply button at the bottom right of the panel. 

5. Upon clicking apply, you will be prompted to review the SQL query/command that will be run to create your new schema.
The query should look like this:
CREATE SCHEMA `your_schema_name`;
Confirm that the name of the schema is correct and hit apply to create the schema or cancel to make any changes.
*We can close the Schema panel that was previously opened for us once our schema has been created

6. Once created our Schema should appear in the Navigator section in the schema tab automatically. 
** If the newly created schema is not present, right click the empty white space in the navigator section and click on refresh all from the dropdown menu.

## Creating a Table
7. Once the schema has been selected, expand the schema by clicking on the triangular icon on the left side of the schema name. Right click on Tables and select Create Table from the dropdown menu. A new panel should appear in the main area of the application

8. 
