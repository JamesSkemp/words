+++
title = "Using Log Parser to find users accounts used to log into an FTP site"
description = "Query to find what user names were passed when logging into an IIS FTP site."
draft = false
comments = true
date = "2007-09-13T20:00:00-05:00"
modified = "2007-09-13T21:19:49-05:00"
slug = "Using-Log-Parser-to-find-users-accounts-used-to-log-into-an-FTP-site"
blogengine = "9ec06000-b479-4519-808e-34a17e31e2c0"
categories = ["software", "tutorials / guides"]
tags = ["iis", "log parser", "analytics"]
+++

<p>
The following Log Parser query can be used on FTP log files in order to determine what user names were used to login, or attempt to login, to an FTP site.
</p>
<blockquote>
	<p>
	logparser &quot;select cs-uri-stem, count(cs-method) from ex*.log where cs-method like &#39;%USER&#39; group by cs-uri-stem order by count(cs-method),cs-uri-stem&quot;&nbsp;
	</p>
</blockquote>
<p>
This assumes that you&#39;ve added Log Parser to your path, and that you&#39;re running this from your log file directory.
</p>
<p>
This query will tell you what ip addresses successfully logged into your FTP site.
</p>
<blockquote>
	<p>
	logparser &quot;select c-ip, count(sc-status) from ex*.log where sc-status = &#39;230&#39; group by c-ip order by count(sc-status),c-ip&quot;&nbsp;
	</p>
</blockquote>
<p>
Finally, this query will show you what ip addresses attempted to log into your FTP site, and will give a count of how many times.
</p>
<blockquote>
	<p>
	logparser &quot;select c-ip, count(*) from ex*.log group by c-ip order by count(*),c-ip&quot;&nbsp;
	</p>
</blockquote>
<p>
You can find other Log Parser articles on my site by viewing other items tagged with <strong>log parser</strong> (link below). 
</p>

