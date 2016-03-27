+++
title = "Log Parser script: Percent of status codes across all hits/requests"
description = "Log Parser SQL script to determine what percent status codes are across all requests."
draft = false
comments = true
date = "2007-10-01T23:00:00-05:00"
modified = "2007-10-02T08:33:52-05:00"
slug = "Log-Parser-script-Percent-of-status-codes-across-all-hitsrequests"
blogengine = "75e37670-17c8-4355-8d4d-86d62bf50ca5"
categories = ["software", "tutorials / guides"]
tags = ["iis", "log parser", "analytics"]
+++

<div class="note">
<p>
Note: This article was written using Log Parser 2.2. Therefore, while it may work for a different version, it may not.
</p>
</div>
<p>
The following SQL can be used by Log Parser to generate a chart with the total requests (for a day, month, or year) and what percent each status code is of those requests. An example chart can be found at the end of this article.
</p>
<p>
First, I assume that the below is put in the same directory as the logs you would like to parse.&nbsp;
</p>
<blockquote>
	<p>
	SELECT sc-status AS [HTTP Status Code], count(*) AS Requests<br />
	INTO http_status_percent_graph-%date%.png<br />
	FROM ex%date%*.log<br />
	GROUP BY [HTTP Status Code]<br />
	ORDER BY Requests DESC<br />
	</p>
</blockquote>
<p>
Once you&#39;ve saved this, you can call the script like such, so long as you&#39;re already in the directory you saved the SQL file.
</p>
<blockquote>
	<p>
	logparser file:http_status_percent_graph.sql?date=0710 -o:chart -chartType:Pie -chartTitle:&quot;Status as Percent of Requests&quot;
	</p>
</blockquote>
<p>
If you just want the numbers, you can use the following SQL.
</p>
<blockquote>
	<p>
	SELECT sc-status, count(*)<br />
	INTO http_status_codes-%date%.txt<br />
	FROM ex%date%*.log<br />
	GROUP BY sc-status<br />
	ORDER BY sc-status 
	</p>
</blockquote>
<p>
It too can be called via the command line (again, assuming you save the SQL file and run the following in the same directory as your log files). 
</p>
<blockquote>
	<p>
	logparser -rtp:-1 file:http_status_codes.sql?date=0710&nbsp;
	</p>
</blockquote>
<p>
Feel free to modify the scripts to your own need.
</p>
<h3>Example chart</h3>
<p style="text-align: center">
<img style="width: 640px; height: 480px" src="/files/2007/10/http_status_percent_graph-example.gif" alt="Example of the status code chart" title="Example of the status code chart" /><br />
Example of the status code chart
</p>

