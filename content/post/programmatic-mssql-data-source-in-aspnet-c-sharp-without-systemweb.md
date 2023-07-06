+++
title = "Programmatic MSSQL data source in ASP.NET (C#) without System.Web"
description = "Another way to programmatically make a database call, but this time without extra System.Web includes."
draft = false
comments = true
date = "2009-06-06T14:08:00-05:00"
modified = "2009-06-06T14:24:22-05:00"
slug = "Programmatic-MSSQL-data-source-in-ASPNET-C-Sharp-without-SystemWeb"
blogengine = "cb23a73b-23c6-453a-b21d-37caba98a77f"
categories = ["article", "technology"]
tags = ["c#", "mssql", ".net"]
+++

In [a similar article](/post/programmatic-mssql-data-source-in-aspnet-c-sharp) I detailed how I was doing programmatic access of Microsoft SQL Server. However, on another project I was creating a class in App_Code. Using my method required the use of a couple additional namespaces from System.Web. That seemed a bit excessive.

So I did some digging around and came up with what I believe is a better solution, for use in classes/non-Web code.

First, the following must be included in.

```csharp
// For DataTable
using System.Data;
// For SqlConnection, SqlCommand, SqlParameter, SqlDataAdapter
using System.Data.SqlClient;
// For ConfigurationManager
using System.Configuration;
```

Next we have the code, with some dummy data.

```csharp
public DataTable returnDataTable(int Id) {
	DataTable returnValue = new DataTable();

	SqlConnection connection = new SqlConnection();
	connection.ConnectionString = ConfigurationManager.ConnectionStrings["connectionString"].ConnectionString;
	SqlCommand command = new SqlCommand();
	command.Connection = connection;
	command.CommandType = CommandType.StoredProcedure;
	command.CommandText = "stored_proc";
	command.Parameters.Add(new SqlParameter("@id", Id));
	SqlDataAdapter adapter = new SqlDataAdapter(command);
	adapter.Fill(returnValue);

	adapter = null;
	command = null;
	connection.Close();
	connection = null;

	return returnValue;
}
```

This seems to be a bit better than what I had.

Or not? Let me know.
