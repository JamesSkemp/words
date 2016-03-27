+++
title = "Log Parser queries to find 400 and 500 http status codes"
description = "Queries that can be used in Log Parser to find 400 and 500 status codes in IIS log files."
draft = false
comments = true
date = "2007-09-09T18:30:00-05:00"
modified = "2007-09-13T21:18:46-05:00"
slug = "Log-Parser-queries-to-find-400-and-500-http-status-codes"
blogengine = "141464e8-deea-4e42-bdff-580b03546814"
categories = ["software", "tutorials / guides"]
tags = ["log parser", "iis", "analytics"]
+++

<div class="note">
<p>
Note: This article was written using Log Parser 2.2. Therefore, while it may work for a different version, it may not.
</p>
</div>
<p>
In a previous article, I discussed <a href="/words/post/Find-404-errors-using-Log-Parser.aspx">how to use Log Parser to find 404 errors in IIS log files</a>. This time, I&#39;ve made it a little broader, by giving some queries to find all 400 codes, and all 500 codes, through log files.
</p>
<p>
<span style="text-decoration: line-through">There may be a better way to find these codes (instead of my IN statement), but a standard LIKE doesn&#39;t seem to work.</span>
</p>
<p>
Again, these assume that you&#39;ve currently got a command line open in the folder containing your IIS logs, and that you are logging the above information, as well as that logparser is setup in your PATH line.
</p>
<h4>400 Status Codes</h4>
<blockquote>
	<p>
	logparser -rtp:-1 &quot;SELECT cs-uri-stem, cs-uri-query, date, sc-status, cs(Referer) INTO 400sReport.txt FROM ex*.log WHERE (sc-status &gt;= 400 AND sc-status &lt; 500) ORDER BY sc-status, date, cs-uri-stem, cs-uri-query&quot;<br />
	</p>
</blockquote>
<h4>500 Status Codes</h4>
<blockquote>
	<p>
	logparser -rtp:-1 &quot;SELECT cs-uri-stem, cs-uri-query, date, sc-status, cs(Referer) INTO 500sReport.txt FROM ex*.log WHERE (sc-status &gt;= 500 AND sc-status &lt; 600) ORDER BY sc-status, date, cs-uri-stem, cs-uri-query&quot;<br />
	</p>
</blockquote>
<p>
A Google search for <strong>http status codes</strong> will give a number of resources regarding exactly what these codes mean.&nbsp;
</p>
<h4>Updated 2007.09.10</h4>
<p>
Added the correct parameter to display all date in one big &#39;table&#39;, so the column headings don&#39;t repeat every 10 lines.
</p>

