+++
title = "Programmatic SQL command timeout using a SqlDataSource (C#)"
description = "How to programmatically set a timeout on a Sql command, using a SqlDataSource, in C#."
draft = false
comments = true
date = "2009-06-24T08:20:00-05:00"
modified = "2009-06-24T08:34:53-05:00"
slug = "Programmatic-SQL-command-timeout-using-a-SqlDataSource-C-Sharp"
blogengine = "d69dd5f6-6c55-4f39-a740-aa55422aacc4"
categories = ["article"]
tags = ["c#", "mssql", ".net"]
+++

<p>Granted, in the case where this came up, I should have moved away from a SqlDataSource, but I wrote it using one, and a re-write isn't possible at the moment.</p>
<p>So, I had to find a way yesterday to programmatically set the command timeout of a select, using a SqlDataSource (that was programmatically written).</p>
<p>After much research, I found that you have to set the timeout on selecting. After opening a dummy document to see if I could determine how it was normally done, I came up with something like the following:</p>
<pre class="code"><code class="csharp">SqlDataSource dataSource = new SqlDataSource();
// code removed
dataSource.Selecting += GenericSelecting;
// code removed</code></pre>
<p>The GenericSelecting is as follows:</p>
<pre class="code"><code class="csharp">protected void GenericSelecting(object sender, SqlDataSourceSelectingEventArgs e) {
	e.Command.CommandTimeout = 6000;
}</code></pre>
<p>Excessive timeout, yes, but it works.</p>
<p>Why does this need to be done? Well, even if you set a timeout on the connection string that only determines how long the initial connection to Sql will go before it times out. The commands against that data source, however, are outside of that timeout. Which means that if your Sql takes more than 30 seconds (IIRC), you get a nice timeout error.</p>
<p>In this case the stored procedure was pretty massive (granted, it wasn't taking 6000 seconds), so a timeout had to be used.</p>
