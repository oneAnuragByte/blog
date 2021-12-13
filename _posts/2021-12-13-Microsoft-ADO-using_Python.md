---
layout: post
title:  "Microsoft ADO with Python"
date:   2021-12-13 16:30:00 +0530
categories: jekyll update
---
***Note**: The details provided is as-is for informational purpose only.*

*Recently*, I came accross a cool Python package - [**adodbapi**](https://pypi.org/project/adodbapi/), which enables you to query a data source (like Microsoft SQL Server or anyother data source which has a OLE DB driver/provider available) using ADO syntax. Another good thing is.. that it works on top of already available OleDB Providers (and drivers). <br>
You may also use this package over an ODBC driver but that will require the ***Ole DB provider for ODBC driver*** bridge between your application and the ODBC driver (This is not recommended. If available, use the OleDB driver directly, removing the bridge/translator between the ODBC and OLE DB world).

Here are some links that you can go through, to understand these terminologies in detail:
1. [Microsoft OLE DB Driver for SQL Server](https://docs.microsoft.com/en-us/sql/connect/oledb/oledb-driver-for-sql-server?view=sql-server-ver15) <br>
*Quick gotcha: There had been multiple generation of this technology and previous drivers used to be called "Provider". The name has been changed to "Driver" to be consistent.*

2. [Ole DB Provider Overview](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/ms709836(v=vs.85)) <br>
*Quick gotcha: ADO makes it easy to use OLE DB interface for accessing Data*

3. [ADO Fundamentals](https://docs.microsoft.com/en-us/sql/ado/guide/data/ado-fundamentals?view=sql-server-ver15) <br>
*Quick gotcha: This can be used for relational database as well other data store which has ole db driver/provider available*

4. [Sample in .NET](https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/ado-net-code-examples#oledb)

***
<br>

**Here** is a sample Python script to help you understand - how can you use the [**adodbapi**](https://pypi.org/project/adodbapi/) to bring this functionality to Python. 

**Prerequisite**: 
1. Get a data source (for example Microsoft SQL Server instance accessible from the machine where the code has to run) 
2. Create a table called *Person*. You may have multiple columns for this table, but the example script below assumes that you have atleast 2 columns in the Person table.
3. Also the connection string below uses the NTLM authentication. If you would like to use SQL Auth, include the Username and Password in the connection string. [ConnectionStrings.com](https://www.connectionstrings.com/microsoft-ole-db-provider-for-sql-server-sqloledb/) has good amount of examples to help you build the required connection string.

``` python
    import adodbapi

    #Connection string to connect to Data source. 
    strConn = "Driver={ODBC Driver 17 for SQL Server};Server=<Server with instance name if available>;Database=<DatabaseName>;Trusted_Connection=Yes;"
    conn = adodbapi.connect(strConn)

    cursor = conn.cursor()
    cursor.execute('SELECT * FROM Person')

    #to get description of data set (column details of the table)
    cursor_description = cursor.get_description()

    print("*"*100)
    print('Connection String: ','"', strConn, '"', sep="")
    print('Cursor description as returned from DB using this connection string:\n', cursor_description)

    #retrieving data from Database: 
    print("\nData as returned from DB : \n")
    row = cursor.fetchone()
    while row:
        print(cursor_description[0][0], ":", row[0])
        print(cursor_description[1][0], ":", row[1])
        row = cursor.fetchone()
```

***cursor_description** would contain metadata of the data being returned, for example column name etc.*

Till we meet again...!