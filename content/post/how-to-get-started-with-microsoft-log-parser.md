+++
title = "How to get started with Microsoft Log Parser"
description = "The following guide will get you started with Log Parser."
draft = false
comments = true
date = "2008-11-07T14:50:00-06:00"
modified = "2008-11-07T14:49:55-06:00"
slug = "How-to-get-started-with-Microsoft-Log-Parser"
blogengine = "820d8569-38ec-4417-ae7b-15569678e73a"
categories = ["software", "tutorials / guides"]
tags = ["log parser"]
aliases = ["/post/How-to-get-started-with-Microsoft-Log-Parser/"]
+++

<p>
I&#39;ve <a href="/words/?tag=/log+parser">written about Microsoft Log Parser</a> before, and even started <a href="http://logparserplus.com/">a site around it</a>. But, I noticed the other day that I hadn&#39;t written on how to get started with this powerful tool. 
</p>
<h3>Getting Log Parser</h3>
<p>
The current version of Log Parser is version 2.2, which you can <a href="http://www.microsoft.com/technet/scriptcenter/tools/logparser/default.mspx" target="_blank">download from Microsoft</a>. 
</p>
<h3>Installing Log Parser</h3>
<p>
While it says&nbsp;supported operating systems are&nbsp;&quot;Windows 2000; Windows Server 2003; Windows XP Professional Edition,&quot; it appears to run fine on Windows XP Home Edition and Windows Vista (at least Ultimate has been personally confirmed). 
</p>
<p>
While it will install to C:\Program Files\Log Parser 2.2\ by default, you can grab the core executable&nbsp;and move&nbsp;it anywhere you&#39;d like, including to a USB flash drive, for parsing on other systems. 
</p>
<h3>Running Log Parser (easily)</h3>
<p>
Log Parser is run from the command line. By making one addition to your system(s), you can easily run Log Parser from any directory. 
</p>
<p>
To allow the Log Parser executable to be run from any directory, through the command line, right-click on My Computer and select Properties. On the Advanced tab is an Environment Variables button. 
</p>
<p>
Under System variables you&#39;ll find a Path variable, with an existing value. If you add the full path to logparser.exe, you can simply type <strong>logparser</strong> from the command line to&nbsp;run the executable. 
</p>
<p>
For example: 
</p>
<blockquote>
	<p>
	;C:\Program Files\Log Parser 2.2\&nbsp; 
	</p>
</blockquote>
<div class="note">
<p>
Each path must be separated by a semi-colon (;). 
</p>
</div>
<h3>Starting Log Parser</h3>
<p>
With this done, you can now&nbsp;go to Start &gt; Run ...&nbsp;- or press&nbsp;the Windows key and&nbsp;R&nbsp;- and Open <strong>cmd</strong>. 
</p>
<p>
To verify that Log Parser is available, type <strong>logparser -h</strong>, which should show a listing of available commands.
</p>
<h3>Next steps</h3>
<p>
Visit <a href="http://logparserplus.com/">Log Parser Plus</a> to see a listing of available functions and a list of examples and tutorials, and to share your queries.
</p>

