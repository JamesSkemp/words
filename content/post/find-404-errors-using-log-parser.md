+++
title = "Find 404 errors using Log Parser"
summary = "Two quick SQL commands to run in Log Parser to get 404 errors from logs."
draft = false
comments = true
date = "2007-08-04T13:54:00-05:00"
modified = "2007-09-13T21:19:59-05:00"
slug = "Find-404-errors-using-Log-Parser"
blogengine = "843a9454-231f-41ad-a847-78c5012a1ae8"
categories = ["software", "tutorials / guides"]
tags = ["log parser", "iis", "analytics"]
+++

<div class="note">
<p>
Note: This article was written using Log Parser 2.2. Therefore, while it may work for a different version, it may not.
</p>
</div>
<p>
The following code will generate a listing of calls that generated a 404 error.
</p>
<blockquote>
	<p>
	logparser &quot;SELECT cs-uri-stem, cs-uri-query, date, sc-status, cs(Referer) INTO 404report.txt FROM ex*.log WHERE sc-status = 404 ORDER BY date, cs-uri-stem, cs-uri-query&quot;
	</p>
</blockquote>
<p>
This assumes that you&#39;ve currently got a command line open in the folder containing your IIS logs, and that you are logging the above information, as well as that logparser is setup in your PATH line.
</p>
<p>
A file called &#39;404report.txt&#39; will be generated in the folder containing your log files, which will list the above five fields. It&#39;s possible to generate a count instead, but I have no done so above.
</p>
<p>
Here&#39;s one that generates a count with pages and referers listed, of 404 pages.
</p>
<blockquote>
	<p>
	logparser &quot;SELECT cs-uri-stem AS page, cs(Referer) AS referer, count(*) AS hits INTO 404report.txt FROM ex*.log WHERE sc-status = 404 GROUP BY page, referer ORDER BY page&quot;
	</p>
</blockquote>
<p>
All-in-all, I&#39;m pretty impressed by this tool, once you have time to actually work with it.&nbsp;
</p>
<h4>Update, 2007.09.09</h4>
<p>
Updated both codes to export to <strong>404report.txt</strong>, instead of just <strong>report.txt</strong>.
</p>

