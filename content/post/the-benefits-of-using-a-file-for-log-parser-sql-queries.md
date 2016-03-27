+++
title = "The benefits of using a file for Log Parser SQL queries"
description = "With Log Parser, you can define your SQL query in a file, instead of on the command line."
draft = false
comments = true
date = "2010-09-26T09:41:00-05:00"
modified = "2010-09-26T09:55:43-05:00"
slug = "The-benefits-of-using-a-file-for-Log-Parser-SQL-queries"
blogengine = "4432e29f-bd9b-4af0-830d-fc398637bcaf"
categories = ["tutorials / guides"]
tags = ["log parser", "xml"]
+++

<p>One of the things I always forget about when I'm using Microsoft Log Parser is that you can define your SQL query in a file and run it, instead of putting it in the command line.</p>
<p>For example, the following will run whatever SQL is defined in strivinglife.robots.sql.</p>
<pre class="code"><code class="logparser">logparser -i:w3c -o:xml file:strivinglife.robots.sql</code></pre>
<p>Where this comes in handy is for something like the <a rel="external" href="http://logparserplus.com/Examples">Log Parser query</a> I defined today, that parses IIS logs for requests to the robots.txt file and outputs the ip address and user-agent of the request, with a total count from that combination.</p>
<pre class="code"><code class="sql">SELECT c-ip AS [ClientIp], cs(user-agent) AS [ClientUserAgent], COUNT(*) AS [Requests]
--USING
INTO strivinglife.robots.xml
FROM \\server1\projects\logs\server2008\w3svc5\u_ex1009*.log
WHERE cs-uri-stem = '/robots.txt'
GROUP BY ClientIp, ClientUserAgent
--HAVING
ORDER BY Requests DESC</code></pre>
<p>Because&nbsp;my output is XML, and I don't want the parens to turn into underscores (as well as&nbsp;so that I know what my element names are) I alias the columns to particular names.&nbsp;(The commented lines are from my template file.)</p>
<p>This then gives me an output that I can parse and display, for example, on a Web page.</p>
