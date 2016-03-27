+++
title = ".NET DataSet dump (C#)"
description = "What I'm using to dump/output the contents of a DataSet in .NET (C#)."
draft = false
comments = true
date = "2008-10-18T16:36:00-05:00"
modified = "2009-06-01T23:09:24-05:00"
slug = "NET-DataSet-dump-C-Sharp"
blogengine = "d264d204-3506-4db7-99ab-d294e2e477d8"
categories = ["Internet", "tutorials / guides"]
tags = [".net", "c#"]
+++

<p>One thing that I really like about ColdFusion is the powerful cfdump.</p>
<blockquote>
<p>Use the cfdump tag to get the elements, variables, and values of most kinds of ColdFusion objects. Useful for debugging. You can display the contents of simple and complex variables, objects, components, user-defined functions, and other elements.&nbsp;</p>
</blockquote>
<p>Of all the tags in ColdFusion, cfoutput is probably the only tag that I use more.</p>
<p>Unfortunately, most other languages, JavaScript and&nbsp;.NET included, don't&nbsp;include this powerful, and versatile, functionality.</p>
<p>Here's what I've got if I want to dump the contents of a DataSet:</p>
<pre class="code"><code class="csharp">
StringBuilder dataString = new StringBuilder();

try {
	DataSet dataSet = new DataSet();
	dataSet.ReadXml(Server.MapPath(@"DataSetDump.xml"));
	foreach (DataTable table in dataSet.Tables) {
		dataString.Append("&lt;h2&gt;" + table.TableName.ToString() + "&lt;/h2&gt;");
		foreach (DataRow row in table.Rows) {
			foreach (DataColumn column in table.Columns) {
				dataString.Append("Column &lt;strong&gt;" + column.ToString() + "&lt;/strong&gt; = " + row[column].ToString() + "&lt;br /&gt;");
			}
		}
	}
} catch (Exception ex) {
	Response.Write(ex.Message);
}
</code></pre>
<p>Whether this is the best way to do it, that's what I guess I'll find out, but it's been working well enough for my purposes.</p>
<p>See an <a href="http://jamesrskemp.com/testing/asp.net/DataSetDump.aspx">example of this in use</a> (on a simple XML file).</p>
