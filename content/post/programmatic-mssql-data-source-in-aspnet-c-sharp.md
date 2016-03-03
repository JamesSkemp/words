+++
title = "Programmatic MSSQL data source in ASP.NET (C#)"
summary = "The code I've been using to open a connection, programmatically, to Microsoft SQL Server."
draft = false
comments = true
date = "2009-06-01T21:03:00-05:00"
modified = "2009-06-06T14:24:59-05:00"
slug = "Programmatic-MSSQL-data-source-in-ASPNET-C-Sharp"
blogengine = "6e75e124-2b85-40f1-ba2b-c57c8c4a64c3"
categories = ["article", "technology"]
tags = ["c#", "mssql", ".net"]
+++

<p>I keep having to search through code to find it, so, since writing about it makes it easier for me to find ... here's how I've been programmatically making calls to Microsoft SQL Server.</p>
<p>If I'm doing something wrong, please comment below or send me an email. Some times have been changed to dummy values.</p>
<pre class="code"><code class="csharp">
SqlDataSource dataSource = new SqlDataSource();
dataSource.ConnectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ConnectionString;
dataSource.SelectCommand = "stored_proc";
dataSource.SelectCommandType = SqlDataSourceCommandType.StoredProcedure;
dataSource.SelectParameters.Add("id", value);
dataSource.CacheDuration = 3600;

DataView viewData = (DataView)dataSource.Select(DataSourceSelectArguments.Empty);
DataTable tableData = viewData.ToTable();

//Stuff

tableData = null;
viewData = null;
dataSource = null;
</code></pre>
<p>From what I can tell, there's no close by doing a select this way; the connection must close after it's performed?</p>
<h3>Update June 6 2009:</h3>
<p>To use this code you would also need to include the following, if they were not already included.</p>
<pre class="code"><code class="csharp">// Need to add for SqlDataSource
using System.Web.UI.WebControls;
// Need for ConfigurationManager
using System.Configuration;
// Need for DataView
using System.Data;
// For DataSourceSelectArguments
using System.Web.UI;</code></pre>
<p>Because of this, there may be another way to do this, that doesn't require these additions.</p>
