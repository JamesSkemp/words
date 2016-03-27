+++
title = "A brief overview of IIS 6.0 and the W3C extended log format"
description = "An overview of Microsoft Internet Information Services (IIS) 6.0 and the World Wide Web Consortium (W3C) extended log file format, in relation to Log Parser. [slnet0514:92218721-d037-4d0e-854e-fad30f247873]"
draft = false
comments = true
date = "2007-11-03T21:00:00-05:00"
modified = "2007-11-11T10:21:05-06:00"
slug = "A-brief-overview-of-IIS-60-and-the-W3C-extended-log-format"
blogengine = "92218721-d037-4d0e-854e-fad30f247873"
categories = ["software", "tutorials / guides"]
tags = ["iis", "log parser"]
+++

<p>
In Microsoft Internet Information Services (IIS) 6.0, you can choose to use a number of different formats for your access logs. 
</p>
<p>
Access logs contain information about what files are requested, whether the request was successful or not. 
</p>
<p>
Of all the available formats, the World Wide Web Consortium (W3C) extended log file format is by far the most flexible format available, as you can select the information that you would like to log. Of course, with that added flexibility, you also have larger log files, with the more you decide to log. Since logging is handled by the server (specifically IIS), no matter what kind of files you serve, the hardest part is determining what you&#39;d like to log, and then doing something with that data. 
</p>
<h3>Overview of the fields</h3>
<p>
W3C extended log fields&nbsp;are server and/or client-related. For example, there is the IP address that I use, the IP address that the server uses, and the browser that I use to access the server/content. 
</p>
<p>
Working through the ordering in IIS, these fields are as follows: 
</p>
<ul>
	<li>
	<div>
	Date ( date ) 
	</div>
	</li>
	<li>
	<div>
	Time ( time ) 
	</div>
	</li>
	<li>
	<div>
	Client IP Address ( c-ip ) 
	</div>
	</li>
	<li>
	<div>
	User Name ( cs-username ) 
	</div>
	</li>
	<li>
	<div>
	Service Name ( s-sitename ) 
	</div>
	</li>
	<li>
	<div>
	Server Name ( s-computername ) 
	</div>
	</li>
	<li>
	<div>
	Server IP Address ( s-ip ) 
	</div>
	</li>
	<li>
	<div>
	Server Port ( s-port ) 
	</div>
	</li>
	<li>
	<div>
	Method ( cs-method ) 
	</div>
	</li>
	<li>
	<div>
	URI Stem ( cs-uri-stem ) 
	</div>
	</li>
	<li>
	<div>
	URI Query ( cs-uri-query ) 
	</div>
	</li>
	<li>
	<div>
	Protocol Status ( sc-status ) 
	</div>
	</li>
	<li>
	<div>
	Protocol Substatus ( sc-substatus ) 
	</div>
	</li>
	<li>
	<div>
	Win32 Status (&nbsp;sc-win32-status ) 
	</div>
	</li>
	<li>
	<div>
	Bytes Sent (&nbsp;sc-bytes ) 
	</div>
	</li>
	<li>
	<div>
	Bytes Received (&nbsp;cs-bytes ) 
	</div>
	</li>
	<li>
	<div>
	Time Taken (&nbsp;time-taken ) 
	</div>
	</li>
	<li>
	<div>
	Protocol Version (&nbsp;cs-version ) 
	</div>
	</li>
	<li>
	<div>
	Host (&nbsp;cs-host ) 
	</div>
	</li>
	<li>
	<div>
	User Agent (&nbsp;cs(User-Agent) ) 
	</div>
	</li>
	<li>
	<div>
	Cookie (&nbsp;cs(Cookie) ) 
	</div>
	</li>
	<li>
	<div>
	Referer ( cs(Referer) ) 
	</div>
	</li>
</ul>
<p>
As you&#39;ll notice, most fields begin with either c, cs, s, or sc. As you look at where they are used, you can see that: 
</p>
<ul>
	<li>
	<div>
	<strong>c</strong> is used for <strong>client</strong>-related&nbsp;fields 
	</div>
	</li>
	<li>
	<div>
	<strong>s</strong> is used for <strong>server</strong>-related fields 
	</div>
	</li>
	<li>
	<div>
	<strong>cs</strong> signifies information sent by the <strong>client to the server</strong> 
	</div>
	</li>
	<li>
	<div>
	<strong>sc</strong> signifies information sent by the <strong>server to the client</strong> 
	</div>
	</li>
</ul>
<h3>What the logs are named</h3>
<p>
When the log files are created in the extended format, they are given a specific filename, based upon what you&#39;ve configured for when they are created. 
</p>
<p>
By default, logs store daily information. So, each log will be given a filename based upon the current date, and will store 24 hours of data. However, logs can also be formatted to hold more or less data. Each, along with the format of the filename, is listed below. 
</p>
<ul>
	<li>
	<div>
	EXTEND<em>NN</em>.LOG 
	</div>
	<ul>
		<li>
		<div>
		Logs are unlimited in size, or created/closed after a particular size 
		</div>
		</li>
	</ul>
	</li>
	<li>
	<div>
	EX<em>YYMMDDHH</em>.LOG 
	</div>
	<ul>
		<li>
		<div>
		Hourly logs 
		</div>
		</li>
	</ul>
	</li>
	<li>
	<div>
	EX<em>YYMMDD</em>.LOG 
	</div>
	<ul>
		<li>
		<div>
		Daily logs 
		</div>
		</li>
	</ul>
	</li>
	<li>
	<div>
	EX<em>YYMMWW</em>.LOG 
	</div>
	<ul>
		<li>
		<div>
		Weekly logs 
		</div>
		</li>
	</ul>
	</li>
	<li>
	<div>
	EX<em>YYMM</em>.LOG 
	</div>
	<ul>
		<li>
		<div>
		Monthly logs 
		</div>
		</li>
	</ul>
	</li>
</ul>
<p>
For most sites, you can continue to use the default of daily logs. However, if you have a large amount of traffic, you may consider hourly logs, or even based upon a file size. 
</p>
<h3>Additional fields when using Log Parser</h3>
<p>
Briefly, there are two additional fields that are available, when using Log Parser (2.2). 
</p>
<p>
These additional fields are as follows. 
</p>
<ul>
	<li>
	<div>
	LogFilename 
	</div>
	</li>
	<li>
	<div>
	LogRow&nbsp; 
	</div>
	</li>
</ul>
<p>
<strong>LogFilename</strong> contains the full path to the log file, while <strong>LogRow</strong> contains the row in that log file, that the data came from. 
</p>
<h3>Next time ...&nbsp;</h3>
<p>
Next time, we&#39;ll cover which of these fields you may want to log, for what benefit. 
</p>

