# Schemas and Tables
## Overview
In this section, you will learn how to create a schema, and add a table to a schema to...

!!! warning 
    Due to the limitations of our documentation, an understanding on configuring your MySQL server and how to configure a connection is not covered. However, it is a pre-requisite to creating a Schema or Table.

## Creating a Schema
1. Open MySQL Workbench.

2. Using your previously configured connection, connect to your MySQL database by **clicking** on the connection.

    ![Selecting a MySQL connection](/assets/selectConnection.png)

3. In the navigator panel (by default on the left side of the application window), **right click** in the whitespace. 
4. From the dropdown menu, **click** create schema. 
    
    ![Create Schema option in dropdown menu](/assets/rightClickSchema.png)
    !!! warning
        Ensure that you are in the Schemas tab and not the Administration tab (option at the bottom of the navigator section)

    A new panel should appear in the main area of the application.
    
5. In the newly opened panel, **specify** a name for your Schema. 
6. **Click** on the apply button at the bottom right of the panel. 
    
    ![Naming a schema](/assets/namingSchema.png)

    Upon clicking apply, you will be prompted to review the SQL query that will run to create your new schema.
    
    The prompt will look like this:

    ![Schema creation query prompt](/assets/schemaCreateQuery.png)


7.  **Verify** that the name of the schema is correct.
8. **Click** apply to create the schema or **click** cancel to make any changes.

    Once created our Schema should appear in the schema list automatically. 

    !!! success
        ![Schema list with newly created schema](/assets/newSchema.png)

    !!! tips
        We can close the Schema panel that was previously opened for us once our schema has been created. This helps to reduce cluttering our workspace with unnecessary tabs.

    !!! tips
        If the newly created schema is not visible in the schema list:

        1.  **Right click** the empty white space in the navigator section
        2. **Click** on refresh all from the dropdown menu.

## Creating a Table
1. Select the Schema that you want to add a table to by **double clicking** it. 

2. Expand the schema by **clicking** on the triangular icon on the left of the schema name. 

3. **Right click** on Tables

4. **Click** Create Table from the dropdown menu. 
    A new panel should appear in the main area of the application

## Populating a Table with Data