+++
title = "W3C extended log format fields and IIS 6.0"
summary = "In this article, I'll be covering IIS 6.0 and what benefit you gain from tracking various W3C extended log format fields, for statistical and debugging purposes. [slnet0514:5263c19c-37d9-4f5e-adb8-29c85e3aee36]"
draft = false
comments = true
date = "2007-11-06T21:30:00-06:00"
modified = "2007-11-11T10:21:24-06:00"
slug = "W3C-extended-log-format-fields-and-IIS-60"
blogengine = "5263c19c-37d9-4f5e-adb8-29c85e3aee36"
categories = ["article", "tutorials / guides"]
tags = ["iis"]
+++

<p>
In a previous article, I gave <a href="/words/post/A-brief-overview-of-IIS-60-and-the-W3C-extended-log-format.aspx">an overview of the World Wide Web Consortium (W3C) extended log format, in relation to Internet Information Services (IIS) 6.0</a>. 
</p>
<p>
This time, I&#39;d like to cover what each field provides, again in relation to IIS and a Web site, for statistical and debugging purposes. 
</p>
<h3>What fields are available</h3>
<p>
Again, we&#39;ve covered what fields are available in the W3C extended log format in a previous article. 
</p>
<p>
Read&nbsp;<em><a href="/words/post/A-brief-overview-of-IIS-60-and-the-W3C-extended-log-format.aspx">A brief overview of IIS 6.0 and the W3C extended log format</a></em> for more information about these fields. 
</p>
<h3>Essential fields</h3>
<p>
In the W3C extended log format, there are a number of essential fields, which are listed below. 
</p>
<ul>
	<li>Date ( date ) </li>
	<li>Time ( time ) </li>
	<li>URI Stem ( cs-uri-stem ) </li>
</ul>
<p>
At the very least, there are these&nbsp;three fields which&nbsp;should be tracked. 
</p>
<p>
<strong>Date</strong> and <strong>Time</strong> should be tracked in order to determine the time at which a request took place. Even though you may be using daily logs, keeping Date in means you can do daily analysis over multiple logs. 
</p>
<p>
At the very least, <strong>URI Stem</strong> is also essential, in order to determine which files are being called, and how often. 
</p>
<h3>Essential fields 2</h3>
<p>
Of course, the first list isn&#39;t quite enough, which is why most of the time you&#39;ll want to have the following as well. 
</p>
<ul>
	<li>URI Query ( cs-uri-query ) </li>
	<li>Protocol Status ( sc-status ) </li>
	<li>Referer ( cs(Referer) ) </li>
</ul>
<p>
While <strong>URI Stem</strong> works for older, static sites, <strong>URI Query</strong> is equally essential for today&#39;s dynamic sites, which rely on parameters being passed and accepted. 
</p>
<p>
<strong>Protocol Status</strong> gives us an idea of whether the request was successful or not, which enables us to determine which requests were invalid, or may be causing other errors. 
</p>
<p>
Depending upon your views on things<strong>, Referer</strong> is essential, or not. I&#39;ve decided to include it, since it helps determine where invalid requests are coming from, as well as where valid requests are coming from. This can also help determine the path individuals are taking through your own site. 
</p>
<h3>Slightly less essential fields</h3>
<p>
Now that we&#39;ve gone through the essential fields, in two parts, we can take a look at what fields are <em>slightly</em> less essential. Not everyone may find a need for these fields, but most of the time I think you&#39;ll want to include them. 
</p>
<ul>
	<li>Client IP Address ( c-ip ) </li>
	<li>User Agent ( cs(User-Agent) ) </li>
</ul>
<p>
One could argue that <strong>Client IP Address</strong> and <strong>User Agent</strong> are very essential indeed. However, depending upon the purpose of the site, they may not be. 
</p>
<p>
For example, for an Intranet, or personal site, there may be no reason to track either of these fields, since the client used to view the site, as well as the IP addresses, could be a controlled listing. 
</p>
<p>
However, for sites that are available for a larger, external, audience, these two fields are indeed quite essential. For the first reason, however, I include these both here. 
</p>
<p>
<strong>Client IP Address</strong> can be used to determine which IPs, if any, are resulting in traffic, either good or bad. <strong>User Agent</strong> can be used to determine what software is being used to view the site, and thereby allow for proper testing. 
</p>
<h3>Semi-essential fields</h3>
<p>
Semi-essential fields are fields that I believe are essential, for more in-depth analysis of traffic and server status. These fields are listed below. 
</p>
<ul>
	<li>Bytes Sent ( sc-bytes ) </li>
	<li>Bytes Received ( cs-bytes ) </li>
	<li>Time Taken ( time-taken ) </li>
</ul>
<p>
As we discussed in the previous article, sc is server to client, and cs is client to server. While <strong>Bytes Received</strong> isn&#39;t as essential as <strong>Bytes Sent</strong>, since the majority of traffic will be the latter, I&#39;ve grouped them here. Both are semi-essential, since they both help determine not only how much is being transmitted, but also who is pulling down a lot of traffic (combined with <strong>Client IP Address</strong>). 
</p>
<p>
<strong>Time Taken</strong> ties in directly with these, as well, since typically the more Bytes going around, the longer it&#39;s going to take. So, most of the time, files with a larger <strong>Bytes Sent</strong> value will also have a large <strong>Time Taken</strong> value. However, <strong>Time Taken</strong> may also mean that a file is performing poorly, for more dynamic files. 
</p>
<h3>Even more semi-essential</h3>
<p>
We&#39;ve got a few more fields to cover that are semi-essential, before we list &#39;the rest.&#39; 
</p>
<ul>
	<li>Server Port ( s-port ) </li>
	<li>Method ( cs-method ) </li>
	<li>Protocol Substatus ( sc-substatus ) </li>
	<li>Protocol Version ( cs-version ) </li>
</ul>
<p>
<strong>Method</strong> is a nice enough field, since it helps determine how the content is being requested. Is someone GETting the file? Is information being POSTed back? Is something just requesting the HEAD? 
</p>
<p>
<strong>Server Port</strong> is semi-essential, or not, depending what ports are being used. For most sites, it&#39;ll just be port 80, but you may have other posts used as well. 
</p>
<p>
<strong>Protocol Version</strong> can be used to give some insight into what software is being used to view files, which may help with determing what technologies, such as compression, can be used. 
</p>
<p>
Finally, <strong>Protocol Substatus</strong> may provide additional information, depending upon the <strong>Protocol Status</strong> that was returned. <strong>Win32 Status</strong>, which we haven&#39;t mentioned yet, is similar, but I wouldn&#39;t consider it as essential, which is why I&#39;m not including it here. 
</p>
<h3>The rest</h3>
<p>
Finally, we&#39;ve got the rest. Of course, these are how I&#39;m rating these, so if someone can convince me otherwise, please do. Otherwise, these are the fields, in order solely of how they are listed in IIS, that are less essential than all the rest. 
</p>
<ul>
	<li>User Name ( cs-username ) </li>
	<li>Service Name ( s-sitename ) </li>
	<li>Server Name ( s-computername ) </li>
	<li>Server IP Address ( s-ip ) </li>
	<li>Win32 Status ( sc-win32-status ) </li>
	<li>Host ( cs-host ) </li>
	<li>Cookie ( cs(Cookie) ) </li>
</ul>
<p>
<strong>User Name</strong> is a good field, if you&#39;re using technology that stores this. For example, many Intranet sites, or the like. In these cases, this can help you determine who&#39;s doing what. However, for the average external site, this field won&#39;t provide any helpful information. 
</p>
<p>
<strong>Service Name</strong> is the site name used in IIS, which is typically something in the format of W3SVC#. This can be helpful when going over multiple log files, but otherwise may not provide helpful information. Likewise, <strong>Server Name</strong> provides the name of the computer. This may be helpful after moving from one computer to another, if you&#39;ve changed the name, in order to determine performance changes, but&nbsp;otherwise ... most sites won&#39;t have a need for this. 
</p>
<p>
Ditto for <strong>Server IP Address</strong>, which, for most sites, will be pretty consistent. Again, this may provide some help in determining performance, or otherwise comparing one server to another (such as over multiple logs, from the same day). 
</p>
<p>
<strong>Win32 Status</strong> may provide additional information about a status code, but <strong>Protocol Status</strong> may be enough. 
</p>
<p>
<strong>Host</strong> can help rebuild a URI, if you have multiple domains pointing to a single site, or otherwise see which is performing better. 
</p>
<p>
Finally, you&#39;ve got <strong>Cookie</strong>. Depending upon your site, this may be very essential indeed, but I&#39;m not that big of a fan. However, if you&#39;re site is relying upon cookies, this will obviously be worth that much more. 
</p>
<h3>Final thoughts</h3>
<p>
Hopefully, this gives an idea of the benefit of various W3C extended log format fields. Of course, this doesn&#39;t cover actual analysis of these fields, which we&#39;ll cover in another article. 
</p>

