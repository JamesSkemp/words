+++
title = "How to ensure that performance counters continue after a restart"
description = "A possible way to have performance counters restart automatically after your box restarts. Also, an example LogParser query to analyze those logs."
draft = false
comments = true
date = "2007-09-19T21:00:00-05:00"
modified = "2007-11-03T20:34:51-05:00"
slug = "How to ensure that performance counters continue after a restart"
blogengine = "7ce32188-b08f-435c-9374-30440f8238c8"
categories = ["software", "tutorials / guides"]
tags = ["windows", "iis", "analytics", "log parser"]
+++

<p>
A few days ago my server was restarted in the early morning hours. I had been logging network and processor usage using Windows built-in performance monitoring, but when the server restarted, the logs did not. 
</p>
<p>
A bit of research later, it appears that there is a way to have Windows restart the logging after a system restart. 
</p>
<p>
To enable this, it seems you just need to have the log stop after a certain amount of time (for example, after x hours, or x days). Then, check the box stating that &quot;When a log file closes,&quot; &quot;Start a new log file.&quot; 
</p>
<p>
This has the added benefit of keeping your log files manageable in size. 
</p>
<h3>Information to log</h3>
<p>
Unfortunately, I haven&#39;t found much in the way of information regarding what counters should be logged. I believe I read a Microsoft article that suggested Bytes Total/sec for the Network Interface, and Processor(_Total)\% Processor Time. 
</p>
<p>
I was doing this for a couple of weeks, but have decided to try out the following instead, for a couple of weeks. Once I&#39;ve got a baseline (looking at the old numbers and the new), I&#39;ll disable the logging for a bit, or decrease the polling time, and then start it back up to see if that baseline remains. 
</p>
<blockquote>
	<p>
	Memory\Available MBytes<br />
	Network Interface(x)\Bytes Received/Sec<br />
	Network Interface(x)\Bytes Sent/sec<br />
	Processor(_Total)\% Processor Time 
	</p>
</blockquote>
<p>
(Some information removed, to protect the innocent.) 
</p>
<p>
Once you have these logging, it&#39;s easy to use LogParser and avg(), min(), max() to generate some meaningful information. 
</p>
<h3>Example SQL query&nbsp;</h3>
<p>
See the below example (some data replaced with &#39;xxx&#39;). Modify to taste, and save as a sql file, running it through Log Parser with &#39;file&#39;. 
</p>
<blockquote>
	<p>
	/* 2007.09.19&nbsp;&nbsp;&nbsp; J.Skemp&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Created query. */<br />
	SELECT count(*) AS TotalCounters,<br />
	&nbsp;&nbsp;&nbsp; -- Get the initial and final datetime<br />
	&nbsp;&nbsp;&nbsp; min([(pdh-csv 4.0) (eastern daylight time)(240)]) as DateFirst,<br />
	&nbsp;&nbsp;&nbsp; max([(pdh-csv 4.0) (eastern daylight time)(240)]) as DateLast,<br />
	&nbsp;&nbsp;&nbsp; -- Processor information<br />
	&nbsp;&nbsp;&nbsp; avg(to_real([\\xxx\Processor(_Total)\% Processor Time])) as ProcAvg(%),<br />
	&nbsp;&nbsp;&nbsp; min(to_real([\\xxx\Processor(_Total)\% Processor Time])) as ProcMin(%),<br />
	&nbsp;&nbsp;&nbsp; max(to_real([\\xxx\Processor(_Total)\% Processor Time])) as ProcMax(%),<br />
	&nbsp;&nbsp;&nbsp; -- Memory information<br />
	&nbsp;&nbsp;&nbsp; avg(to_int([\\xxx\Memory\Available MBytes])) as MemAvailAvg(MB),<br />
	&nbsp;&nbsp;&nbsp; min(to_int([\\xxx\Memory\Available MBytes])) as MemAvailMin(MB),<br />
	&nbsp;&nbsp;&nbsp; max(to_int([\\xxx\Memory\Available MBytes])) as MemAvailMax(MB),<br />
	&nbsp;&nbsp;&nbsp; -- Network (in) information<br />
	&nbsp;&nbsp;&nbsp; avg(div(to_real([\\xxx\Network Interface(xxx)\Bytes Received/Sec]),1024)) as NetRecAvg(K),<br />
	&nbsp;&nbsp;&nbsp; min(div(to_real([\\xxx\Network Interface(xxx)\Bytes Received/Sec]),1024)) as NetRecMin(K),<br />
	&nbsp;&nbsp;&nbsp; max(div(to_real([\\xxx\Network Interface(xxx)\Bytes Received/Sec]),1024)) as NetRecMax(K),<br />
	&nbsp;&nbsp;&nbsp; -- Network (out) information<br />
	&nbsp;&nbsp;&nbsp; avg(div(to_real([\\xxx\Network Interface(xxx)\Bytes Sent/sec]),1024)) as NetSentAvg(K),<br />
	&nbsp;&nbsp;&nbsp; min(div(to_real([\\xxx\Network Interface(xxx)\Bytes Sent/sec]),1024)) as NetSentMin(K),<br />
	&nbsp;&nbsp;&nbsp; max(div(to_real([\\xxx\Network Interface(xxx)\Bytes Sent/sec]),1024)) as NetSentMax(K)<br />
	-- Change file names accordingly<br />
	INTO temp_report.txt<br />
	FROM ServerInfo_*.csv 
	</p>
</blockquote>
<p>
Add/remove as necessary, for your logs. 
</p>

