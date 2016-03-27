+++
title = "Parse FileZilla Server logs with Log Parser"
description = "SQL to run through Log Parser to parse and transform FileZilla Server logs into W3C Extended format."
draft = false
comments = true
date = "2008-11-23T22:15:00-06:00"
modified = "2008-11-23T22:20:04-06:00"
slug = "Parse-FileZilla-Server-logs-with-Log-Parser"
blogengine = "4cf7475e-baae-437a-adf1-7dfe7f5213cb"
categories = ["article", "software"]
tags = ["log parser"]
+++

<p>
While FileZilla Server is one of the best FTP servers available, it&#39;s logging leaves much to be desired.
</p>
<p>
However, after a couple of hours, I&#39;ve created a script for Log Parser that will generate a W3C log from FileZilla Server&#39;s logs.
</p>
<p>
Save the following to a file, for example, FileZillaServer.sql:
</p>
<blockquote>
	<p>
	SELECT<br />
	&nbsp;SUBSTR(Text, 1, SUB(INDEX_OF(Text, &#39;)&#39;), 1)) AS RequestNumber<br />
	&nbsp;, TO_TIMESTAMP(<br />
	&nbsp;&nbsp;TRIM(<br />
	&nbsp;&nbsp;&nbsp;SUBSTR(<br />
	&nbsp;&nbsp;&nbsp;&nbsp;Text<br />
	&nbsp;&nbsp;&nbsp;&nbsp;, ADD(INDEX_OF(Text, &#39;)&#39;), 1)<br />
	&nbsp;&nbsp;&nbsp;&nbsp;, SUB(INDEX_OF(Text, &#39;-&#39;), ADD(INDEX_OF(Text, &#39;)&#39;), 4))<br />
	&nbsp;&nbsp;&nbsp;)<br />
	&nbsp;&nbsp;)<br />
	&nbsp;&nbsp;, &#39;M/d/yyyy?H:mm:ss&#39;<br />
	&nbsp;) AS DateTime<br />
	&nbsp;--, TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;, TRIM(SUBSTR(<br />
	&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;, 0<br />
	&nbsp;&nbsp;, LAST_INDEX_OF(<br />
	&nbsp;&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;&nbsp;, &#39;(&#39;<br />
	&nbsp;&nbsp;)<br />
	&nbsp;)) AS User<br />
	&nbsp;, SUBSTR(<br />
	&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;, ADD(LAST_INDEX_OF(<br />
	&nbsp;&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;&nbsp;, &#39;(&#39;<br />
	&nbsp;&nbsp;), 1)<br />
	&nbsp;&nbsp;, SUB(LAST_INDEX_OF(<br />
	&nbsp;&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;&nbsp;, &#39;)&#39;<br />
	&nbsp;&nbsp;), ADD(LAST_INDEX_OF(<br />
	&nbsp;&nbsp;&nbsp;TRIM(SUBSTR(Text, ADD(INDEX_OF(Text, &#39;-&#39;), 1), SUB(INDEX_OF(Text, &#39;&gt;&#39;), ADD(INDEX_OF(Text, &#39;-&#39;), 1))))<br />
	&nbsp;&nbsp;&nbsp;, &#39;(&#39;<br />
	&nbsp;&nbsp;), 1))<br />
	&nbsp;) AS IpAddress<br />
	&nbsp;, SUBSTR(Text, ADD(INDEX_OF(Text, &#39;&gt;&#39;), 2), SUB(STRLEN(Text), INDEX_OF(Text, &#39;&gt;&#39;))) AS Request<br />
	<strong>INTO FileZilla.log</strong><br />
	<strong>FROM fzs-*.log</strong><br />
	WHERE Text LIKE &#39;(%&#39;<br />
	&nbsp;AND Request NOT LIKE &#39;Connected,%&#39;<br />
	&nbsp;AND Request NOT LIKE &#39;221 %&#39;<br />
	&nbsp;AND Request NOT LIKE &#39;disconnected%&#39;<br />
	&nbsp;AND Request NOT LIKE &#39;QUIT%&#39;
	</p>
</blockquote>
<p>
Items in <strong>bold</strong> can be easily changed.
</p>
<p>
Then call the SQL with:
</p>
<blockquote>
	<p>
	logparser -rtp:-1 -i:TEXTLINE -o:W3C file:FileZillaServer.sql
	</p>
</blockquote>
<p>
This returns the following fields:
</p>
<ul>
	<li>
	<div>
	RequestNumber (string)
	</div>
	</li>
	<li>
	<div>
	DateTime (timestamp)
	</div>
	</li>
	<li>
	<div>
	User (string)
	</div>
	</li>
	<li>
	<div>
	IpAddress (string)
	</div>
	</li>
	<li>
	<div>
	Request (string)
	</div>
	</li>
</ul>
<h3>Notes</h3>
<p>
In my attempt to parse the files, I ran into an issue with generating the timestamp. While AM/PM is added to the time,&nbsp;the time is actually&nbsp;output in 24-hour time.
</p>
<p>
Ignoring the fact that it therefore seems unnecessary to include AM/PM as well, Log Parser seems to run into issues if you try to TO_TIMESTAMP with the AM/PM included, and 24-hour time. In particular, it chokes on hour 0 and 13-23, if there&#39;s also AM or PM.
</p>
<p>
Changing the code to pull AM/PM resolved the issue with NULLs (-) being returned.
</p>

